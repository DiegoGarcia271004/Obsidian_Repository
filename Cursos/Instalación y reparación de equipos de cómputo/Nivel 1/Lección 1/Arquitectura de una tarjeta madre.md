---
tags:
  - IREC
---
En general todas las tarjetas madres poseen la siguiente arquitectura de comunicación, en esta ocasión se observará la arquitectura de un procesador con 16 núcleos a 32 hilos.

**Microprocesador:** Contiene 16 núcleos físicos.
**Memoria RAM:** Cada núcleo físico tiene acceso hasta 16Gb.
**Puertos PCIe:** La mayoría están en comunicación directa con el microprocesador.
- **PCIe 10GBe:** Aplicable a tarjetas de red, Ethernet.
- **PCIe GPU:** Aplicable a tarjetas de video.
- **PCIe SSD:** Aplicable a discos de estado sólido con conector PCI.
**Chipset:** Circuito que funciona como un puente entre los puertos USB, SATA, eSATA, audio, wifi y BIOS.
**USB:** Puertos para conectar dispositivos como teclados, mouse, discos duros externos, etc.
**SATA:** Conexiones para conectar unidades ópticas, discos duros magnéticos, etc.
**eSATA:** Para conectar discos duros magnéticos y de estado sólido de más reciente tecnología.
**WAN:** Comunicación con conexión inalámbrica.
**SP7.1:** Canal de audio.
**BIOS:** Comunicación para el arranque de la computadora.
**SM-BUS:** Comunicación para cargar programas como el sistema operativo a la memoria RAM del sistema para ser ejecutado.
**PCIe SSD(OS):** Es el único puerto PCIe conectado al chipset, generalmente se utiliza para almacenar el sistema operativo y éste inicie de manera más rápida.