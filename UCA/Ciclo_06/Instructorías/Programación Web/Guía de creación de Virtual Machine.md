A continuación se presentará una guía para poder realizar la creación y configuración de una Virtual Machine con VMware workstation.

## Creación de Virtual Machine en VMware
---

Primeramente, se debe de tener ya instalado tanto la distribución de Linux como VMware.
A continuación procederemos a ejecutar VMware:

![[Pasted image 20251012201937.png|center]]

A continuación procederemos a darle a **Create New Virtual Machine** y en la ventana emergente daremos Next:

![[Pasted image 20251012202051.png|center]]

Ya procediendo a la selección de la distribución, dejamos seleccionado `Installer disc image file (iso)` y seleccionamos en donde hemos descargado nuestra distribución, luego le damos a siguiente.

![[Pasted image 20251012202428.png|center]]

Luego podemos ponerle el nombre a nuestra máquina virtual, en este caso le pondremos `Servidor laboratorio 6`.

![[Pasted image 20251012203034.png|center]]

Dejamos la configuración por defecto y seleccionamos Next.

![[Pasted image 20251012203306.png|center]]

En esta parte necesitamos cambiar la configuración del adaptador de red, seleccionamos la opción de **Customize Hardware…**

![[Pasted image 20251012203419.png|center]]

Se nos aparecerá una ventana emergente y seleccionáremos la opción **Network Adapter** del menú izquierdo y cambiaremos la opción por defecto de **NAT** a **Bridged** y por último seleccionaremos **Close**.

![[Pasted image 20251012203505.png|center]]

Por último, revisamos que se haya aplicado el cambio del **Network Adapter** y seleccionamos finalmente **Finish**

![[Pasted image 20251012203617.png|center]]

La máquina virtual se iniciará desde la imagen ISO que seleccionó y podrá comenzar la instalación del sistema operativo.

## Configuración de la máquina virtual
---

Seleccionaremos la opción de **Try or Install Ubuntu Server**, para ello deberemos de dar clic dentro de la máquina virtual para poder navegar y seleccionar opciones.

![[Pasted image 20251012203910.png|center]]

Seleccionaremos el idioma **English**

![[Pasted image 20251012203956.png|center]]

Nos informa de una nueva versión, pero para esta práctica seleccionaremos \[Continue Without Updating\]

![[Pasted image 20251012204136.png|center]]


Seleccionar \[Done\] (No realizaremos cambios en este apartado)

![[Pasted image 20251012204227.png|center]]

Asegurarse de tener la siguiente configuración, y seleccionar **Done**

![[Pasted image 20251012204335.png|center]]

Anotamos la dirección IP que aparece en nuestra máquina virtual

![[Pasted image 20251012204434.png]]

Dejaremos en blanco el **Proxy Address**

![[Pasted image 20251012204535.png]]

Dejaremos la configuración por defecto del **Mirror address**

![[Pasted image 20251012204612.png]]

En toda la configuración del espacio en disco, se usará la configuración por defecto, nos aseguramos de que estén marcadas estas opciones

![[Pasted image 20251012204658.png]]

Seleccionar \[Done\] 

![[Pasted image 20251012204741.png]]

Seleccionar \[Continue\]

![[Pasted image 20251012204817.png|center]]

Para fines prácticos del laboratorio, completamos el formulario con los siguientes datos, tener mucho cuidado ya que se usarán las credenciales más adelante.

```bash
Your Name: [Nombre del estudiante]

Your Server Name: [Carnet del estudiante]

Pick a username: uca

Password: 1234
```

![[Pasted image 20251012205009.png]]

Seleccionar \[Done\] y dejar seleccionada **Skip for now**, luego seleccionar \[Continue\]

![[Pasted image 20251012205129.png]]

Importante seleccionar OpenSSH con la barra espaciadora

![[Pasted image 20251012205214.png]]

En esta parte usaremos la configuración por defecto sin seleccionar nada

![[Pasted image 20251012205245.png]]

En esta parte necesitaremos esperar unos minutos a que se apliquen todas las configuraciones y actualizaciones de paquetes de la máquina virtual, al terminar seleccionaremos la opción de \[Reboot now\]

![[Pasted image 20251012205631.png]]

Si al iniciar la máquina virtual muestra este error, solo debemos de dar Enter y accedemos con nuestras credenciales

![[Pasted image 20251012205656.png|center]]
Finalmente acceden con sus credenciales a la máquina virtual y les aparecerá en consola algo similar a la imagen de abajo

![[Pasted image 20251012205804.png|center]]

En caso de no haber anotado la IP de la máquina virtual podemos efectuar el comando ip a en la consola de la máquina virtual, en la primera opción esta la IP local, la tercera es la de Docker y la segunda es la que nos interesa la cual sería la dirección IP que utilizaremos para conectarnos mediante SSH a la máquina virtual

![[Pasted image 20251012205942.png|center]]

Ya con todo preparado, podemos realizar la guía de laboratorio.