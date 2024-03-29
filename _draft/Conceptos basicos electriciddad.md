
## ¿Qué es Arduino?

* Plataforma open-source (codigo abierto) para la creación de proyectos electrónicos mediante hardware y software.
* Tarjeta de Desarrollo basada en Microcontrolador.
* Se utiliza un Software de Desarrollo (Arduino IDE).
* Fácil de programar (C++ simplificado)
* Entradas/Salidas (sensores y actuadores)
* Gran cantidad de librerias disponibles
* En varias presentaciones: Arduino UNO el más popular.

![](https://a.pololu-files.com/picture/0j7808.1200.jpg?810c5e85aeb9493d9ec9fed8abe68464)

## Placa de Arduino Uno

La arduino Uno es una placa de desarrollo basada en un microcontrolador Atmega328. Tiene 14 pines de entrada/salida digital (de los cuales 4 pueden ser utilizados para salidas PWM), 6 entradas análogas, un resonador cerámico de 16 MHz, un conector para USB tipo hembra, un Jack para fuente de Poder, un conector ICSP y un botón reset.

**Características técnicas:**

|Placa de desarrollo|ARDUINO UNO|
|------------------|------------------|
| Microcontrolador | ATmega328P       |
| Tensión de funcionamiento | 5V               |
| Voltaje de entrada (recomendado) | 7-12V            |
| Voltaje de entrada (límite) | 6-20V            |
| Digital pines I/O | 14 (de los cuales 6 proporcionan una salida PWM) |
| PWM digital pines I/O | 6                |
| Pines de entrada analógica | 6                |
| Corriente DC por Pin I/O | 20mA             |
| Corriente DC para Pin 3.3V | 60mA             |
| Memoria flash    | 32KB ATmega328P de los que 0,5 KB son utilizados por el gestor de arranque |
| SRAM             | 2KB ATmega328P   |
| EEPROM           | 1KB ATmega328P   |
| Velocidad de reloj | 16 MHz           |
| Longitud         | 68,6 mm          |
| Anchura          | 53,4 mm          |
| Peso             | 25 g             |

**Diagrama de pines**

![](Arduino-UNO-pines.jpg)

**Diagrama de completo**

![](arduino-Pinout.jpg)

----

## Conceptos básicos de electrónica 

### El circuito eléctrico

![](Circuito%20Electrico.png)

### Voltaje, Corriente y Resistencia
    
**Voltaje** se define como la cantidad de energía potencial entre dos puntos de un circuito. Uno punto tiene más carga que otro. La diferencia de carga entre los puntos se llama voltaje. El voltaje de mide en Voltios (V).

**Corriente** es la tasa con la que fluye la carga. La corriente electrica se mide en Amperios (A).

**Resistencia** es la tendencia de resistir el flujo de carga (corriente) de un materialLa resistencia se mide en Ohms (Ω)

![](Volt%20Amp%20Ohm.jpg)

## La Ley de Ohm

El voltaje, la corriente y la resistencia estan relacionadas mediante la ley de Ohm

![](https://www.electronics-tutorials.ws/wp-content/uploads/2018/05/dccircuits-dcp23.gif)

V= voltaje, I= corriente, R= resistencia

## Señal Digital Vs. Señal Analógica

Una señal Digital unicamente puede tener dos estados o dos valores, por ejemplo estos estados pueden ser "Encendido" o "Apagado", "Abierto" o  "Cerrado", "ON" o "OFF", "Verdadero" o "Falso", generalmente los representamos con los digitos 1 y 0, los cuales llamamos *bits*.

Una señal Analógica, puede tomar cualquier valor existente dentro de un rango determinado, por ejemplo son valores analógicos, la temperatura, el peso, la intensidad de la luz, la velocidad de un vehiculo, etc.

![](analog%20vs%20digital.png)

## Uso del Protoboard

![](http://1.bp.blogspot.com/_aiR9rtM3pn4/S7-7-00AqzI/AAAAAAAAAE0/KsKB3jdUKZ0/s1600/protoboard.bmp)


## Codigo de colores de las Resistencias

![](codigo%20colores.png)

### Heramienta de simulacion de circuitos: TINKERCAD

Tinkercad [(www.tinkercad.com)](www.tinkercad.com) es una herramienta en linea que nos permite la simulación de circuitos mediante la conexión de componentes electronicos virtuales,como protoboard, resistencia, leds, pulsadores, etc.

Tambien nos permite conectar y simular la programación de una placa Arduino UNO, como lo veremos mas adelante.

>Ejercicio 2-1
>
>Crear un pequeño circuito eléctrico, utilizando un LED, una resistencia de 220 ohm, y un boton pulsador en serie, utilizaremos la placa de Arduino UNO unicamente como fuente de energía.
>
>Calcular la corriente que pasa por el circuito, y luego medirla con un amperimetro y comparar ambos valores.
>
>Simularlo en Tinkercad, y luego crearlo con componentes reales.


