# Introducción a Rasperry Pi

## ¿Que es el Raspberry-Pi?

El Raspberry Pi es un ordenador pequeño de bajo costo que puede hacer muchas cosas. Lo conectas a un monitor, un teclado y un ratón.

A este tipo de computadoras se les llama: Single Board Computer (SBC).

![https://projects-static.raspberrypi.org/projects/raspberry-pi-setting-up/edbc847fb73193738573d2c16bc039602b0b3657/en/images/pi-plug-in.gif](https://projects-static.raspberrypi.org/projects/raspberry-pi-setting-up/edbc847fb73193738573d2c16bc039602b0b3657/en/images/pi-plug-in.gif)

## Conociendo la Raspberry Pi

![conoce la raspberry pi](https://projects-static.raspberrypi.org/projects/raspberry-pi-getting-started/265d1b0102bf58bc4b05b87ad3cb7793f5bf9ed7/es-ES/images/pi-labelled-names.png)

* **Puertos USB:** se usan para conectar un ratón y un teclado. También puede conectar otros componentes, como una pincho USB.

* **Ranura para tarjeta SD** - aquí puedes colocar la tarjeta SD. Aquí es donde se almacenan el software del sistema operativo y tus archivos.

* **Puerto Ethernet** - esto se usa para conectar la Raspberry Pi a una red con un cable. La Raspberry Pi también se puede conectar a una red a través de una LAN inalámbrica.

* **Conector de audio** - aquí puedes conectar auriculares o altavoces.

* **Puerto HDMI**: aquí se conecta el monitor (o proyector) que estás utilizando para mostrar la salida de la Raspberry Pi. Si tu monitor tiene altavoces, también puedes usarlos para escuchar el sonido.

* **Conector de alimentación micro USB**: aquí se conecta una fuente de alimentación. Siempre debe hacer esto lo último, después de haber conectado todos tus otros componentes.

* **Puertos GPIO**: con ellos puedes conectar componentes electrónicos como LEDs y botones a la Raspberry Pi.

## Especificaciones Técnicas

El modelo Raspberry Pi 3B+ tiene las siguientes especificaciones:

* SoC: Broadcom BCM2837B0 quad-core A53 (ARMv8) 64-bit @ 1.4GHz
* GPU: Broadcom Videocore-IV
* RAM: 1GB LPDDR2 SDRAM
* Networking: Gigabit Ethernet (via USB channel), 2.4GHz and 5GHz 802.11b/g/n/ac Wi-Fi
* Bluetooth: Bluetooth 4.2, Bluetooth Low Energy (BLE)
* Storage: Micro-SD
* GPIO: 40-pin GPIO header, populated
* Ports: HDMI, 3.5mm analogue audio-video jack, 4x USB 2.0, Ethernet, Camera Serial Interface (CSI), Display Serial Interface (DSI)
* Dimensions: 82mm x 56mm x 19.5mm, 50g

El modelo mas nuevo es el Raspberry Pi 4, cuyas especificaciónes pueden se encontradas en este [enlace.](https://www.raspberrypi.org/products/raspberry-pi-4-model-b/specifications/)


## Comenzando con la Raspberry Pi

### Lo Que Necesitas

#### Hardware

* Una Raspberry Pi con una tarjeta SD, de al menos **8 GB**.	
* Un monitor con un cable (y, si es necesario, un adaptador HDMI)
* Un teclado y ratón USB
* Una fuente de alimentación con capacidad minima de **2.5 Amp para el Raspberry Pi 3, y 3.0 Amp para el Raspberry Pi 4**.
* Un lector de tarjetas SD
* Auriculares o altavoces (opcional)
* Un cable de ethernet (opcional)

#### Software

Debes descargar los siguientes programas los cuales vamos a utilizar:

* [SD Card Formatter](https://www.sdcard.org/downloads/formatter/index.html)
* [Balena Etcher](https://www.balena.io/etcher/)
* [Rasbian OS](https://www.raspberrypi.org/downloads/raspbian/): Se recomienda la versión "with desktop".

### Preparación de la Tarjeta micro SD

##### Paso No. 1 - Formatear la SD Card

Este paso borrará todo el contenido de la SD Card.

* Instalar el software SD Card Formatter.
* Insertar a SD Card e la computadora o por medio de un adaptador.
* En SD Formatter, selecciónar la tarjeta apropiada y formatearla ![](https://projects-static.raspberrypi.org/projects/raspberry-pi-setting-up/edbc847fb73193738573d2c16bc039602b0b3657/en/images/sd_formatter_win_annotated.png)

##### Paso No. 2 - Grabar la imagen del SO e la SD Card

* Bajar e instalar Balena Etcher.
* Conectar el lector SD on la memoria instalada
* Abrir Balena Etcher y selecciónar el archivo `.img` o `.zip` que se quiere grabar en la tarjeta SD
* Selecciónar la SD en la que se quiere grabar la imagen.
* Revisar la selección y presionar 'Flash!.

##### Paso No. 3 - Iniciar la Raspberry Po
* Conectar la Raspberry Pi a un monitor, teclado y mouse
* Insertar la memoria SD en el Raspberry Pi
* Encenderlo y esperar que arranque el Sistema Operativo.

![](https://projects-static.raspberrypi.org/projects/raspberry-pi-setting-up/edbc847fb73193738573d2c16bc039602b0b3657/en/images/pi-desktop.png)

### Paso No. 4 - Finalizando la preparación

* Cuando se inicia por primera vez el SO del Raspberry Pi, aparece una ventana con la aplicación **Welcome to Raspberry Pi**

![](https://projects-static.raspberrypi.org/projects/raspberry-pi-setting-up/edbc847fb73193738573d2c16bc039602b0b3657/en/images/piwiz.gif)

* Hacer click en Siguiente para iniciar la configuración
* Seguir los pasos para configurar el **Pais**, **Lenguaje** y **Zona Horaria**
* Establecer un password para el Raspberry Pi   
* Conectarse a una red Wifi y cambiar la IP según se indique.
* Finalizar y reiniciar el Raspberry Pi.


---
# Computación Física con Python

Una de las funciones mas poderosas del Raspberry Pi es la fila de pines del GPIO que se encuentra en orilla superior  de la tarjeta. GPIO significa General-Purpose Input/Output,o Entradas/Salidas de Propósito General. Estos pines son interface físicas entre la Raspberry Pi y el mundo exterior. De una manera simple, puede imagina que son switches que pueden encenderse o apagarse (entradas) o que el Pi puede encender o apagar (salidas).

Los pines del GPIO permiten al Raspberry Pi controlar y monitorear el mundo exterior al ser conectados a circuitos electrónicos. ElPi es 

The GPIO pins allow the Raspberry Pi to control and monitor the outside world by being connected to electronic circuits. The Pi is able to control LEDs, turning them on or off, run motors, and many other things. It’s also able to detect whether a switch has been pressed, the temperature, and light. We refer to this as physical computing.

There are 40 pins on the Raspberry Pi (26 pins on early models), and they provide various different functions.

If you have a RasPiO pin label, it can help to identify what each pin is used for. Make sure your pin label is placed with the keyring hole facing the USB ports, pointed outward


---


Contenido derivado de la publicación de Raspberry Pi Foundation bajo esta licencia: Creative Commons license. Material original en este [enlace](https://projects.raspberrypi.org/en/projects/raspberry-pi-setting-up)

https://projects.raspberrypi.org/en/projects?hardware[]=electronic-components