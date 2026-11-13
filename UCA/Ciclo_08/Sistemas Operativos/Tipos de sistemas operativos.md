Un sistema operativo está diseñado alrededor de las características y necesidades del sistema donde se ejecuta.

| Sistema               | Necesidad principal                              |
| --------------------- | ------------------------------------------------ |
| Servidor web          | Atender muchos usuarios simultaneamente          |
| Smartphone            | Ahorrar batería y administrar recursos limitados |
| Sistemas industriales | Responder dentro de tiempos deteminados.         |
| Sensor IoT            | Consumir muy poca energia                        |
| Mainframe             | Procesar enormes cantidades de transacciones     |
| PC                    |  Interactividad y facilidad de uso               |

## Sistemas operativos de mainframe

Diseñadas para poder procesar enromes cantidades de datos y transacciones
- Bancos
- Compañías de seguros
- Gobiernos
- Grandes empresas
- Sistemas de procesamiento masivo

**¿Qué problemas intenta resolver?**
Supongamos que un banco posee
- 10M de clientes
- Millones de transacciones diarias
- Consultas simultaneas
- Operaciones que no pueden perderse

Los SO de mainframe están orientados a tener
- confiabilidad
- disponibilidad
- procesamiento masivo
- seguridad 

## Sistemas operativos de servidores

Un servidor normalmente proporciona servicios a otros equipos.
- Múltiples usuarios
- Múltiples procesos
- Redes 
- Almacenamiento
- Seguridad
- Alta disponibilidad

## Sistemas operativos de multiprocesadores

Actualmente prácticamente todos nuestros dispositivos tienen múltiples núcleos. El SO puede permitir que diferentes procesos se ejecuten simultáneamente
- Concurrencia
- Paralelismo

## Sistemas operativos de computadoras de bolsillo

Estos sistemas tienen restricciones que un PC normalmente no tiene
Por eso el SO debe administrar cuidadosamente
- CPU
- pantalla
- red
- GPS
- sensores
- aplicaciones en segundo plano

## Sistemas operativos integrados

Un sistema operativo embebido está diseñado para formar parte de un dispositivo específico
*Ejemplos:*
- Televisores
- routers
- impresoras
- automóviles
- cámaras
- electrodomésticos
- sistemas industriales

---

# Ejemplos de administración de recursos

**Obtener una página:**
Page Size = 4096 bytes
Virtual Address = 13500

$$
\text{Page}=\left\lfloor  \frac{\text{Virtual Address}}{\text{Page Size}}  \right\rfloor 
$$
$$
 = \left\lfloor  \frac{13500}{4096}  \right\rfloor =3
$$
**Obtener el offset:**
$$
\text{Offset} = \text{Virtual Address} - (\text{Page} \times \text{Page Size})
$$
$$
\text{Offset} = 13500-(3\times 4096) =1212
$$
**Bloques con almacenamiento**
SSD = 512GB
Block Size = 4KB

$$
\text{Blocks } = \frac{\text{Almacenamiento}}{\text{Block Size}}
$$
$$
\text{Blocks} = \frac{512\times 1024^{3}}{4\times 1024}= 134,217,728\text{ bytes}
$$

Un archivo tiene 10500 bytes
El sistema usa bloques de 4096 bytes
¿Cuántos bytes necesita?
$$
\text{Blocks}=\left\lceil  \frac{10500}{4096}  \right\rceil =3
$$
> Internal fragmentation

