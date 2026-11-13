# Clinic Bot — Arquitectura para Producción

**Estado:** Planeación cerrada, lista para iniciar Fase 1
**Alcance:** Un solo doctor, con panel de administración web
**Prioridad:** Base lista para escalar a futuro (multi-doctor / multi-clínica)
**Desarrollo dividido en 2 fases:** (1) Chatbot en producción, (2) Panel de administración

**Decisiones confirmadas:**
- Lenguaje: **TypeScript**
- Panel: uso mixto celular + computadora → **diseño responsive obligatorio**, no solo desktop
- Número de WhatsApp Business de producción: **en trámite** (no bloquea el inicio del desarrollo, sí bloquea el deploy final — ver sección 8)
- Panel permite **cancelar y reagendar citas** (no solo verlas)
- Notificación de handoff en Fase 1 (sin panel): **mensaje de WhatsApp normal al número del doctor**

---

## 1. Objetivo de esta versión

El demo demostró la viabilidad técnica del flujo completo (WhatsApp → bot → BD → notificación). Esta versión busca convertirlo en un sistema real:

- Que el doctor pueda **administrar sus horarios y ver sus citas desde un panel web**, sin tocar la base de datos directamente.
- Que el bot **no se caiga silenciosamente** (logging, manejo de errores, reintentos).
- Que un paciente pueda **pedir hablar directamente con el doctor/staff** desde el mismo chat, sin salir del flujo del bot.
- Que el código esté organizado de forma que agregar un segundo doctor o una segunda clínica en el futuro sea una extensión, no una reescritura.

El desarrollo se dividirá en dos fases (ver sección 12): primero el chatbot funcionando sólido en producción, después el panel de administración.

---

## 2. Componentes del sistema

```
                    ┌─────────────────────┐
                    │   Meta WhatsApp      │
                    │   Business API       │
                    └──────────┬───────────┘
                               │ webhook
                               ▼
                    ┌─────────────────────┐
                    │   API (Express)      │
                    │   - Bot engine       │
                    │   - Modo human/bot   │
                    │   - REST API admin   │◄──────┐
                    │   - Auth (JWT)       │       │
                    │   - Cron jobs        │       │ HTTPS
                    └──────────┬───────────┘       │
                               │                    │
                               ▼                    │
                    ┌─────────────────────┐  ┌──────┴──────┐
                    │   PostgreSQL         │  │  Panel Admin │
                    │   (Supabase)         │  │  (React)     │
                    └─────────────────────┘  └─────────────┘
```

**Decisión clave:** el bot de WhatsApp y el panel de administración comparten el mismo backend (misma API Express), solo que exponen rutas distintas (`/webhook` para Meta, `/api/*` para el panel). Esto evita duplicar lógica de negocio (citas, slots, notificaciones) en dos lugares.

---

## 3. Stack tecnológico

| Capa | Tecnología | Nota |
|---|---|---|
| Backend / Bot | Node.js 22 + Express | Se mantiene del demo |
| Lenguaje | **TypeScript** (confirmado) | Ver sección 3.1 |
| Base de datos | PostgreSQL vía Supabase (pooler) | Se mantiene |
| Frontend admin | React + Vite + TailwindCSS | Panel para el doctor (fase 2) |
| Autenticación admin | JWT + bcrypt | Login simple email/contraseña |
| Mensajería | Meta WhatsApp Business API | Requiere pasar a producción (sección 8) |
| Hosting backend | Railway | Se mantiene |
| Hosting frontend | Railway (mismo servicio, build estático) o Vercel | Ver 3.2 |
| Cron / recordatorios | `node-cron` dentro del mismo servicio | Sin necesidad de infra extra |
| Logs | `pino` | Formato estructurado, barato |
| Monitoreo de errores | Sentry (free tier) | Opcional pero recomendado |
| Testing | Vitest + Supertest | Backend |
| CI | GitHub Actions | Lint + test en cada push |
| Validación de datos | `zod` | Env vars y payloads de la API |

### 3.1 ¿Por qué TypeScript?

Confirmado: el proyecto se construirá en TypeScript, tanto en `apps/api` como en `apps/admin`. Como el panel admin consume la misma API que el bot, los contratos de datos (forma de una cita, un slot, un usuario, un mensaje) se comparten entre dos consumidores. TypeScript evita bugs de "el frontend espera `starts_at` pero el backend manda `startsAt`", y el paquete `packages/shared` (sección 4) es donde viven esos tipos compartidos.

### 3.2 Panel admin: ¿mismo servicio o separado?

- **Mismo servicio (recomendado para empezar):** Express sirve el build de React como archivos estáticos. Un solo despliegue en Railway, un solo dominio, $0 extra.
- **Separado (Vercel/Netlify para el frontend):** mejor DX (deploys de frontend más rápidos, preview URLs), pero implica configurar CORS y manejar dos despliegues.

Para un solo doctor, empezaría con la opción de mismo servicio y separaría más adelante si el panel crece mucho.

**Responsive obligatorio:** el doctor usará el panel tanto desde celular como desde computadora, así que TailwindCSS se debe usar con un enfoque *mobile-first* desde la primera pantalla (Login), no como ajuste posterior. Esto afecta especialmente la pantalla de Conversaciones (sección 7) y la de horarios, que son las que más se van a usar en el día a día.

---

## 4. Estructura de carpetas (monorepo)

```
clinic-bot/
├── apps/
│   ├── api/                        # Backend: bot + API REST del panel
│   │   ├── src/
│   │   │   ├── bot/
│   │   │   │   ├── flow.ts             # Motor de estados de la conversación
│   │   │   │   └── messages.ts         # Parser/formateo de mensajes WhatsApp
│   │   │   ├── routes/
│   │   │   │   ├── webhook.routes.ts   # Recibe mensajes de Meta (distingue paciente vs. doctor)
│   │   │   │   ├── cubo-webhook.routes.ts  # Recibe confirmaciones de pago de Cubo
│   │   │   │   ├── auth.routes.ts      # Login del panel
│   │   │   │   ├── appointments.routes.ts
│   │   │   │   ├── slots.routes.ts
│   │   │   │   ├── conversations.routes.ts  # Handoff a humano (fase 1.5 / 2)
│   │   │   │   └── doctors.routes.ts   # Preparado para multi-doctor futuro
│   │   │   ├── controllers/            # Lógica HTTP (parsea request, llama servicio, responde)
│   │   │   ├── services/
│   │   │   │   ├── whatsapp.service.ts     # incluye envío/recepción de imágenes
│   │   │   │   ├── appointments.service.ts
│   │   │   │   ├── slots.service.ts
│   │   │   │   ├── services.service.ts     # Catálogo de servicios con precio
│   │   │   │   ├── payments.service.ts     # Pagos: Cubo y transferencia
│   │   │   │   ├── auth.service.ts
│   │   │   │   ├── conversations.service.ts  # Cambia modo bot/human, guarda mensajes
│   │   │   │   └── notifications.service.ts
│   │   │   ├── middleware/
│   │   │   │   ├── auth.middleware.ts  # Verifica JWT en rutas del panel
│   │   │   │   ├── errorHandler.ts
│   │   │   │   └── requestLogger.ts
│   │   │   ├── jobs/
│   │   │   │   └── reminders.job.ts    # Cron: recordatorio 24h antes
│   │   │   ├── db/
│   │   │   │   ├── index.ts            # Pool de conexión
│   │   │   │   └── migrations/         # SQL versionado (ver sección 5)
│   │   │   ├── config/
│   │   │   │   └── env.ts              # Validación de variables de entorno (zod)
│   │   │   ├── utils/
│   │   │   └── index.ts                # Entry point
│   │   ├── tests/
│   │   │   ├── appointments.test.ts
│   │   │   └── slots.test.ts
│   │   ├── package.json
│   │   └── tsconfig.json
│   │
│   └── admin/                      # Panel web del doctor (fase 2)
│       ├── src/
│       │   ├── pages/
│       │   │   ├── Login.tsx
│       │   │   ├── Appointments.tsx    # Ver citas
│       │   │   ├── Schedule.tsx        # Administrar horarios/slots
│       │   │   └── Conversations.tsx   # Chats en modo "human" + input para responder
│       │   ├── components/
│       │   ├── api/
│       │   │   └── client.ts           # Wrapper de fetch hacia /api/*
│       │   ├── context/
│       │   │   └── AuthContext.tsx
│       │   └── main.tsx
│       ├── package.json
│       └── vite.config.ts
│
├── packages/
│   └── shared/                     # Tipos compartidos entre api y admin (opcional)
│       └── types.ts                # Appointment, Slot, Doctor, User, Message
│
├── docs/
│   ├── architecture.md             # Este documento
│   └── db-schema.md
│
├── .github/
│   └── workflows/
│       └── ci.yml
│
├── package.json                    # npm workspaces
└── README.md
```

**Por qué monorepo con workspaces:** un solo `git clone`, un solo `npm install`, y el paquete `shared` evita duplicar definiciones de tipos entre bot/API y panel. Railway puede desplegar solo `apps/api` (que a su vez sirve el build de `apps/admin`).

---

## 5. Base de datos — esquema ampliado

Cambios respecto al demo, pensando en administración real y escalabilidad futura:

```sql
-- Doctores (hoy habrá 1 solo registro, pero la tabla ya existe)
CREATE TABLE doctors (
  id         SERIAL PRIMARY KEY,
  name       VARCHAR(100) NOT NULL,
  phone      VARCHAR(20),
  created_at TIMESTAMPTZ DEFAULT NOW()
);

-- Usuarios del panel de administración (login del doctor / staff)
CREATE TABLE admin_users (
  id            SERIAL PRIMARY KEY,
  doctor_id     INT REFERENCES doctors(id),
  email         VARCHAR(150) UNIQUE NOT NULL,
  password_hash VARCHAR(255) NOT NULL,
  role          VARCHAR(20) DEFAULT 'doctor',  -- 'doctor' | 'staff' a futuro
  created_at    TIMESTAMPTZ DEFAULT NOW()
);

CREATE TABLE patients (
  id         SERIAL PRIMARY KEY,
  phone      VARCHAR(20) UNIQUE NOT NULL,
  name       VARCHAR(100),
  created_at TIMESTAMPTZ DEFAULT NOW()
);

CREATE TABLE slots (
  id          SERIAL PRIMARY KEY,
  doctor_id   INT REFERENCES doctors(id) DEFAULT 1,
  starts_at   TIMESTAMPTZ NOT NULL,
  duration_min INT DEFAULT 30,
  available   BOOLEAN DEFAULT TRUE,
  created_at  TIMESTAMPTZ DEFAULT NOW()
);

CREATE TABLE appointments (
  id             SERIAL PRIMARY KEY,
  patient_id     INT REFERENCES patients(id),
  slot_id        INT REFERENCES slots(id),
  reason         VARCHAR(255),
  status         VARCHAR(20) DEFAULT 'confirmed',  -- confirmed | cancelled | completed
  reminder_sent  BOOLEAN DEFAULT FALSE,
  cancelled_at   TIMESTAMPTZ,
  created_at     TIMESTAMPTZ DEFAULT NOW()
);

-- Conversación por paciente: controla si responde el bot o un humano
CREATE TABLE conversations (
  id            SERIAL PRIMARY KEY,
  patient_id    INT REFERENCES patients(id) UNIQUE,
  mode          VARCHAR(10) DEFAULT 'bot',   -- 'bot' | 'human'
  last_message_at TIMESTAMPTZ DEFAULT NOW(), -- para saber si sigue abierta la ventana de 24h
  updated_at    TIMESTAMPTZ DEFAULT NOW()
);

-- Historial de mensajes de una conversación (para mostrarlo como hilo en el panel)
CREATE TABLE messages (
  id              SERIAL PRIMARY KEY,
  conversation_id INT REFERENCES conversations(id),
  direction       VARCHAR(10) NOT NULL,  -- 'inbound' | 'outbound'
  sender          VARCHAR(10) NOT NULL,  -- 'patient' | 'bot' | 'staff'
  body            TEXT NOT NULL,
  created_at      TIMESTAMPTZ DEFAULT NOW()
);

-- Catálogo de servicios con precio (consultas, ultrasonidos, consulta remota).
-- Un servicio con variaciones de precio (ej. ultrasonido de embarazo en 2D vs
-- 3D/4D) es más de una fila, mismo `name`, distinto `variant`.
CREATE TABLE services (
  id         SERIAL PRIMARY KEY,
  name       VARCHAR(100) NOT NULL,
  variant    VARCHAR(50),               -- NULL si el servicio no tiene variantes
  price      NUMERIC(10,2) NOT NULL,
  active     BOOLEAN DEFAULT TRUE,      -- permite ocultar un servicio sin borrarlo
  created_at TIMESTAMPTZ DEFAULT NOW()
);

-- Pagos de servicios que lo requieren (hoy: solo "Consulta en línea").
-- No se usa para citas presenciales/ultrasonidos, esas se pagan en clínica.
CREATE TABLE payments (
  id             UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  patient_id     UUID REFERENCES patients(id),
  service_id     INT REFERENCES services(id),
  method         VARCHAR(20) NOT NULL
                   CHECK (method IN ('cubo', 'transfer')),
  status         VARCHAR(20) DEFAULT 'pending'
                   CHECK (status IN ('pending', 'confirmed', 'rejected', 'escalated')),
  attempts       INT DEFAULT 0,         -- reintentos de confirmación (máx. 3, ver sección 7.1)
  cubo_reference VARCHAR(100),          -- id que manda el webhook de Cubo, para cruzar el pago
  created_at     TIMESTAMPTZ DEFAULT NOW(),
  confirmed_at   TIMESTAMPTZ
);
```

**Notas:**
- `doctor_id` con `DEFAULT 1` en `slots` significa que hoy no cambias nada en el flujo del bot, pero el día que agregues un segundo doctor, solo agregas una fila en `doctors` y filtras por `doctor_id` — no rediseñas tablas.
- `conversations.mode` es el interruptor central del handoff (ver sección 7): mientras es `'bot'`, `flow.ts` procesa los mensajes normalmente; en `'human'`, el webhook solo guarda el mensaje y notifica al panel.
- Las migraciones deben ir versionadas en `apps/api/src/db/migrations/` (archivos `001_init.sql`, `002_add_admin_users.sql`, `003_add_conversations.sql`, etc.) en vez de correr SQL suelto a mano — así el esquema queda documentado y reproducible.
- **Pregunta abierta, no resuelta todavía:** con `services` ya existiendo, ¿`appointments.reason` (texto libre limitado a un par de opciones) debería reemplazarse por un `appointments.service_id` que apunte al catálogo — así "Ultrasonido de embarazo (3D/4D)" queda registrado como una relación real, no como texto? Es una migración más invasiva porque toca una tabla que ya está en uso; se define como parte del paso 1.8 del roadmap (sección 12), no antes.

---

## 6. Panel de administración — funcionalidad mínima (MVP)

| Pantalla | Función |
|---|---|
| Login | Email + contraseña, JWT guardado en memoria (no localStorage, por seguridad XSS) |
| Ver citas | Lista de citas próximas, filtro por fecha, estado (confirmada/cancelada) |
| Administrar horarios | Agregar slots nuevos, marcar como no disponible, eliminar slots sin citas |
| Conversaciones | Lista de chats en modo `human`, hilo de mensajes, input para responder (ver sección 7) |
| Cancelar / reagendar cita | El doctor puede cancelar una cita o moverla a otro slot disponible, con notificación automática al paciente por WhatsApp |

Endpoints necesarios en la API (`/api/*`, protegidos por JWT):

```
POST   /api/auth/login
GET    /api/appointments
PATCH  /api/appointments/:id       # cambiar status (cancelar) o reasignar slot_id (reagendar)
GET    /api/slots
POST   /api/slots
DELETE /api/slots/:id
GET    /api/conversations                    # lista de chats en modo human
GET    /api/conversations/:id/messages        # hilo de una conversación
POST   /api/conversations/:id/messages        # el doctor/staff responde
PATCH  /api/conversations/:id                 # cambiar mode ('human' → 'bot')
```

---

## 7. Handoff a humano — comunicación directa con el doctor

Cuando el paciente elige, dentro del flujo del bot, la opción de "hablar directamente" con el doctor/staff, la conversación **no cambia de número ni de chat** — sigue siendo el mismo número de WhatsApp Business, pero las respuestas dejan de generarlas `flow.ts` y pasan a escribirlas el doctor/staff desde el panel.

### Cómo funciona

1. El paciente selecciona la opción "Hablar con el doctor" en el flujo (botón interactivo).
2. `flow.ts` llama a `conversations.service.ts` y cambia `conversations.mode` a `'human'` para ese paciente, y le responde confirmando que un miembro del staff lo va a contactar.
3. Cada mensaje entrante siguiente pasa por `webhook.routes.ts`, que revisa el `mode`:
   - Si es `'bot'` → sigue el flujo normal (`flow.ts`).
   - Si es `'human'` → **no** se procesa como flujo; solo se guarda en `messages` y se notifica al panel (nueva entrada en la lista de "Conversaciones").
4. El doctor/staff ve el hilo en el panel y responde ahí; `conversations.service.ts` envía el mensaje vía `whatsapp.service.ts` y lo guarda como `outbound`/`sender: 'staff'`.
5. El doctor puede "cerrar" la conversación desde el panel, lo que regresa `mode` a `'bot'`.

### Notificación al doctor durante la Fase 1 (mientras no existe el panel)

Como el panel (con su pantalla de Conversaciones) es parte de la Fase 2, en la Fase 1 la notificación de "un paciente quiere hablar directamente" se resuelve así:

- Al momento del paso 2 (cambio de `mode` a `'human'`), `notifications.service.ts` reutiliza el mismo mecanismo que ya notifica citas nuevas (`notifyDoctor`) para enviarle al **número personal del doctor**, vía WhatsApp, un mensaje con el nombre/teléfono del paciente y el motivo si está disponible.
- El doctor responde manualmente **desde su propio WhatsApp**, escribiéndole al paciente directamente (no hay wrapper de panel todavía).
- Esto significa que en Fase 1 el doctor sí necesita tener guardado el número del paciente y escribirle por su cuenta; `messages` igual queda guardando el mensaje entrante del paciente (por webhook) aunque la respuesta del doctor —al no pasar por la API— no quede registrada en esa tabla hasta la Fase 2.
- Es importante que el doctor, una vez atendida la solicitud, le avise al desarrollador o (más adelante) use el panel para regresar `mode` a `'bot'` — mientras tanto, el bot no volverá a responder automáticamente a ese paciente.

### Restricción importante de Meta a tener en cuenta

Mientras estén dentro de la **ventana de 24 horas** desde el último mensaje del paciente (campo `last_message_at`), el doctor puede responder con texto libre sin restricciones. Si pasan más de 24 horas sin que el paciente escriba, cualquier mensaje nuevo del staff necesitará una plantilla aprobada por Meta — igual que cualquier otro mensaje iniciado por el negocio. Vale la pena mostrar en el panel un aviso si la ventana está por cerrarse.

### Por qué no usar un link directo tipo `wa.me/`

Se consideró la alternativa de simplemente mandar un enlace `wa.me/numero-del-doctor` que abra un chat aparte. Se descartó porque abriría una conversación totalmente separada del bot (se pierde el contexto/historial) y expondría un número distinto al número de negocio. El enfoque de arriba mantiene todo en el mismo hilo y reutiliza la infraestructura que de todas formas se va a construir para el panel.

---

## 7.1 Servicios con precio y consulta remota de pago

Esta sección amplía el menú principal del bot: ya no es solo "agendar cita", sino tres caminos distintos desde el mensaje inicial, y dentro de "agendar cita" un catálogo de servicios con precio (no solo motivo de consulta).

### El menú completo

**Rama 1 — Agendar cita (automático, sin intervención humana).** El paciente elige un servicio del catálogo (`services`): `Consulta presencial`, `Ultrasonidos` (con submenú de tipos, algunos con variantes de precio como 2D/3D-4D), o `Consulta y ultrasonido`. Si el servicio elegido tiene más de una variante, el bot muestra un segundo `sendList` con las variantes y su precio antes de continuar al flujo de horarios que ya existe. El precio se **muestra** al paciente, pero no se cobra por el bot — se paga en la clínica.

**Rama 2 — Seguimiento de paciente (gratis, sin handoff).** Distinto del handoff: el bot solo notifica al doctor con el número del paciente (mismo mecanismo que `notifyHandoffRequest`, sección 7), pero **`conversations.mode` no cambia** — el bot sigue respondiendo normal en el chat. El doctor contacta al paciente por su cuenta, fuera del hilo del bot.

**Rama 3 — Comunicación con staff/doctor (gratis, es el handoff).** Esta es literalmente la función que ya está descrita en la sección 7 completa — `triggerHandoff`, cambio de `mode` a `'human'`, sin ningún cambio adicional.

**Rama 4 — Consulta en línea (de pago).** Mismo patrón que la Rama 2 (notificar + compartir número, sin tocar `mode`), pero **solo después de que un `payments` se marque `confirmed`**. Es la única rama nueva que necesita lógica de verdad.

> Nota técnica: con 4+ opciones de nivel superior, ya no caben en `sendButtons` (máximo 3) — este menú se arma con `sendList`.

### El flujo de pago (Rama 4)

1. Paciente elige "Consulta en línea" → bot le informa el precio (leído de `services`) y ofrece método de pago: `sendButtons` con dos opciones, `Cubo` / `Transferencia` (caben bien en el límite de 3).
2. Se crea una fila en `payments` con `status = 'pending'`, `method` según lo elegido, `service_id` apuntando a "Consulta en línea".

**Camino Cubo:**
3. El bot genera/envía el link de cobro de Cubo (falta documentación de su API para el detalle exacto de esta llamada).
4. Cubo le pega un webhook a un endpoint nuevo (`/webhooks/cubo`, separado del de Meta) cuando el paciente paga.
5. Ese webhook busca el `payments` por `cubo_reference`, lo marca `confirmed`, y dispara la notificación al doctor (mismo mensaje que la Rama 2: número del paciente + contexto).
6. Si no se confirma tras 3 intentos (el criterio exacto de "intento" queda por definir cuando llegue la documentación de Cubo — ¿reintentos de generar link, o reintentos de verificar estado?), se marca `escalated` y se notifica al doctor para que lo resuelva directamente con el paciente — misma resolución que el camino de transferencia.

**Camino transferencia:**
3. El bot manda los datos bancarios y pide una captura de pantalla como comprobante.
4. Cuando llega la imagen (requiere el soporte de imágenes en `whatsapp.service.ts` que todavía no existe — ver folder structure actualizada abajo), el bot la reenvía al **doctor** con dos botones: `Confirmar` / `Rechazar`.
5. La respuesta del doctor a esos botones llega al mismo webhook de Meta — pero **desde el número del doctor, no de un paciente**. Esto exige un cambio en `webhook.routes.ts`: comparar `incoming.from` contra `env.DOCTOR_PHONE` **antes** de tratarlo como mensaje de un paciente, y procesarlo por una rama separada, sin sesión de flujo (el id del pago va embebido en el id del botón, ej. `pay_confirm_<paymentId>`).
6. Si confirma → `payments.status = 'confirmed'`, se notifica al doctor con el número del paciente (aunque ya lo tiene, por consistencia con el otro camino).
7. Si rechaza → se incrementa `payments.attempts`; si `< 3`, se le pide al paciente que verifique la transacción o reenvíe una captura correcta, y se vuelve al paso 4. Si `= 3`, `status = 'escalated'` y se notifica al doctor para resolverlo manualmente.

### Piezas nuevas que este flujo exige (no existían hasta el paso 1.4)

- **Manejo de imágenes en `whatsapp.service.ts`** — recibir un `media_id` del webhook de Meta y reenviarlo al doctor sin necesariamente descargar/resubir el archivo.
- **Distinción doctor vs. paciente en `webhook.routes.ts`** — comparación contra `env.DOCTOR_PHONE` antes de la lógica normal de paciente.
- **`services.service.ts`** — CRUD de lectura del catálogo (crear/editar servicios queda para el panel, Fase 2).
- **`payments.service.ts`** — creación de pagos, actualización de estado, conteo de intentos.
- **Endpoint nuevo `/webhooks/cubo`** — pendiente de la documentación real de Cubo para diseñar su payload.
- **Nuevos pasos en `BotFlowStep`** (`packages/shared`) — algo como `select_service`, `select_service_variant`, `payment_method`, `awaiting_transfer_proof`.

---

## 8. Producción real de WhatsApp — el paso que el demo no cubrió

Esto es lo más crítico para que el bot "se use de verdad" y suele subestimarse:

1. **Verificación de negocio en Meta Business Manager** (documentos legales de la clínica).
2. **Número de teléfono de producción** (no el número de prueba del sandbox) — se compra o se porta un número dedicado.
3. **Plantillas de mensaje aprobadas por Meta** — cualquier mensaje que el bot inicie fuera de la ventana de 24h (ej. recordatorio de cita, o respuesta tardía del staff) debe ser una plantilla pre-aprobada, no texto libre.
4. **Política de privacidad pública** — Meta la exige como requisito de la app.
5. **Nombre de perfil de negocio verificado** (el "nombre para mostrar" en WhatsApp pasa por revisión).

Recomiendo tratar esto como una tarea en paralelo desde ya, porque la revisión de Meta puede tardar días y es la dependencia externa más lenta de todo el proyecto.

**Estado actual: en trámite.** Esto no bloquea el inicio del desarrollo (se puede seguir trabajando con el número de prueba/sandbox mientras tanto), pero sí es la dependencia crítica para el paso 1.6 del roadmap (deploy a producción). Vale la pena que confirmes el avance del trámite periódicamente para que no se convierta en el cuello de botella justo cuando el código ya esté listo.

---

## 9. Seguridad y buenas prácticas

- **Contraseñas del panel:** hash con `bcrypt`, nunca texto plano.
- **JWT:** expiración corta (ej. 2h) + refresh token, o simplemente re-login si el volumen de uso es bajo.
- **Datos de pacientes:** aunque El Salvador no tiene una ley equivalente a HIPAA, es buena práctica limitar quién accede a la BD (solo el backend, nunca exponer `DATABASE_URL` al frontend), y no loguear números de teléfono completos en logs de producción. Esto aplica también al contenido de `messages`, que puede incluir información sensible del paciente.
- **Rate limiting** en el webhook (`express-rate-limit`) para evitar abuso.
- **Variables de entorno:** validadas al arrancar con `zod`, para fallar rápido si falta una en vez de fallar silenciosamente en producción.

---

## 10. Herramientas de desarrollo

| Herramienta | Uso |
|---|---|
| Git + GitHub | Control de versiones (ya lo usas) |
| GitHub Actions | Lint + tests automáticos en cada push/PR |
| ESLint + Prettier | Consistencia de código |
| Vitest | Testing unitario/integración del backend |
| Postman / Thunder Client | Probar endpoints del panel manualmente |
| ngrok | Túnel local para webhook de Meta (ya lo usas) |
| Railway CLI | Logs y variables desde terminal |

---

## 11. Presupuesto mensual estimado

| Componente | Costo |
|---|---|
| Railway (Hobby plan, backend + panel) | $5 |
| Supabase (free tier, suficiente para 1 doctor) | $0 |
| Meta WhatsApp API (bajo volumen, <1000 conversaciones/mes) | $0 |
| Dominio propio (opcional, ej. `.com`) | ~$1/mes (~$12/año) |
| Sentry (free tier, hasta 5k eventos/mes) | $0 |
| **Total** | **$5 – $6/mes** (hasta $12–15 si quieres dominio propio) |

Si el volumen de conversaciones de WhatsApp crece más allá de la capa gratuita de Meta (conversaciones iniciadas por el negocio, no por el usuario), ahí empieza a haber costo variable por conversación — pero para un solo doctor es poco probable que lo alcances pronto.

---

## 12. Roadmap propuesto — dividido en 2 fases

### Fase 1 — Chatbot en producción

| Paso | Contenido |
|---|---|
| 1.1 | Reestructurar repo a monorepo, migrar backend del demo a la nueva estructura (+ TypeScript si se decide) |
| 1.2 | Migraciones de BD base (doctors, ajustes a slots/appointments, conversations, messages) |
| 1.3 | Endurecer el bot: logging, manejo de errores, rate limiting, tests |
| 1.4 | Implementar handoff a humano a nivel de bot: opción en el flujo, cambio de `mode`, guardado de mensajes en `messages`, y notificación por WhatsApp al número personal del doctor (ver sección 7) |
| 1.5 | **En paralelo desde el inicio de la fase 1:** dar seguimiento al trámite de verificación de negocio en Meta + plantillas aprobadas |
| 1.6 | Deploy a producción con número real (bloqueado por 1.5 hasta que el trámite se resuelva) |
| 1.7 | Recordatorios automáticos (cron) |
| 1.8 | Catálogo de `services` + menú de 4 ramas + "Seguimiento de paciente" (gratis, sin handoff) — ver sección 7.1. Incluye decidir si `appointments.reason` migra a `service_id` |
| 1.9 | Consulta en línea de pago: tabla `payments`, manejo de imágenes en `whatsapp.service.ts`, distinción doctor/paciente en el webhook, camino de transferencia con reintentos (ver sección 7.1) |
| 1.10 | Integración con Cubo: webhook `/webhooks/cubo`, generación de link de cobro — bloqueado hasta conseguir la documentación de su API |

### Fase 2 — Panel de administración

| Paso | Contenido |
|---|---|
| 2.1 | Migración de BD para `admin_users` + auth (login, JWT, middleware) |
| 2.2 | Panel admin MVP (responsive): ver citas, administrar horarios, cancelar/reagendar citas |
| 2.3 | Panel admin: pantalla de Conversaciones (responder handoff desde la web en vez de que el doctor escriba desde su WhatsApp personal) |
| 2.4 | Pulido: aviso de ventana de 24h por vencer en Conversaciones |

**Nota sobre el handoff en Fase 1:** el bot dispara el cambio de modo, guarda todo en `messages` y le avisa al doctor por WhatsApp — pero el doctor responde desde su WhatsApp personal, no desde un panel (ese no existe aún). Es un punto de fricción manual aceptado temporalmente a cambio de no bloquear el lanzamiento del chatbot esperando el panel completo. La pantalla de Conversaciones (Fase 2) es lo que cierra ese ciclo completamente dentro del sistema.

---

## 13. Resumen de decisiones confirmadas

| Tema | Decisión |
|---|---|
| Lenguaje | TypeScript |
| Uso del panel | Responsive, celular + computadora por igual |
| Número de WhatsApp de producción | En trámite — no bloquea desarrollo, sí bloquea deploy final (paso 1.6) |
| Cancelar/reagendar citas | Sí, desde el panel (Fase 2) |
| Notificación de handoff en Fase 1 | WhatsApp normal al número del doctor; responde manualmente hasta que exista el panel |
| Precio de servicios | Catálogo en tabla `services` (no variables de entorno) — incluye consulta presencial, ultrasonidos con variantes, y consulta en línea |
| "Seguimiento de paciente" vs. "Comunicación con staff/doctor" | El primero es solo notificación (sin handoff, gratis); el segundo **es** el handoff ya definido en la sección 7 |
| Reintentos de pago (Cubo y transferencia) | Máximo 3, luego se escala al doctor para resolución manual en ambos casos |
