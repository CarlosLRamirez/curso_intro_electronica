---
layout: post
title: "Introducción a Arduino"
date:   2019-11-25 12:02:22 -0600
permalink: /introduccion_arduino/
categories: apuntes_curso
---

# ¿Qué es Arduino?

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

![](../images/Arduino-UNO-pines.jpg)

**Diagrama de completo**

![](../images/arduino-Pinout.jpg)

# Programación de Arduino

##  Preparación

* Descargar e Instalar el Software [Arduino IDE ](https://www.arduino.cc/en/Main/Software)
* Conectar el Arduino con el cable USB
* Instalar drivers (si fuera necesario)
* Verificar la conexión de placa con el Arduino IDE

## Uso de Salidas Digitales

En esta sesión vamos a aprender a crear el circuito y programa básico de Arduino. El "Hola Mundo" de la electrónica, el cual consiste en encender y apagar el LED integrado que trae la placa Arduino.

### EJEMPLO 1

#### Conexión

En este caso no necesitamos conexión ya que el LED que vamos a encender y apagar viene integrado en la placa Arduino, y conrresponde con el pin 13.

#### Simulación en  Tinkercad

Tinkercad nos permite simular la conexión del Arduino, y crear "programas" mediante la union bloques, lo cual es de mucha ayuda si usted no tiene experiencia en programación, ya que nos permite comprender de mejor manera la "logica" de un programa.

NOTA: *Se recomienda colocar el idioma en ingles, ya que las traducciones de los bloques suelen ser un poco confusas.*

Este es el "Hola Mundo" en bloques, para encender y apagar de forma intermitente el LED integrado que viene incluido en la placa de Arduino UNO

![bloques hola mundo led integrado](../images/hola-mundo-led-integrado.png)

#### Codigo

Este sería el equivalente en código Arduino, el cual podemos guardar y cargar en nuestra placa real,

```cpp
void setup()
{
  pinMode(13, OUTPUT); //definimos el pin 13 como salida, en este pin se encuentra el LED_INTEGRADO
}

void loop()
{
  digitalWrite(13, HIGH); //encendemos el LED INTEGRADO
  delay(1000); // esperamos 1000 millisecond(s)
  digitalWrite(13, LOW); //apagamos el LED INTEGRADO
  delay(1000); // esperamos 1000 millisecond(s)
}
```

#### Resultado

Aqui vemos el led integrado parpadeando

![](../images/hola%20mundo%20led%20integrado.gif)

### EJEMPLO 2: 

Ahora vamos a modificar el ejemplo anterior, pero vamos a cambiar el LED hacia el pin 10. Para esto debemos de cablearlo utilizando el protoboard y una resistencia de al menos 220ohm.

> **RECUERDE, SIEMPRE UTILIZAR UNA RESISTENCIA CUANDO CONECTE UN LED A UNA SALIDA DE ARDUINO, EL NO HACERLO PUEDE DAÑAR LA PLACA ARDUINO Y EL LED.**


#### Conexión

![](../images/hola-mundo-pin-10-circuito.png)

#### Programa (Bloques)

![](../images/hola-mundo-pin-10.png)

#### Programa (Codigo)

```c++
//Ejemplo salidas digitales -  Hola Mundo

// La rutina setup se ejecuta cuando encendemos el Arduino, 
// o presionamos el boton de reset:
void setup() {
  pinMode(10, OUTPUT); // inicializa el pin 10 como SALIDA (OUTPUT)
}

//La rutina loop se ejecuta una y otra vez, de forma infinita:
void loop() {
  digitalWrite(10, HIGH);   // Enciente el LED (voltaje HIGH)
  delay(1000);               // espera un segundo
  digitalWrite(10, LOW);    // Apaga el LED (voltaje LOW)
  delay(1000);               // espera un segundo
}

```

Como podemos ver en el codigo, la instrucción para "encender" o "apagar " una salida digital en Arduino es `digitalWrite()`.

La instrucción `delay()` nos permite hacer una pausa en el programa para que podamos notar el encendido y apagado del LED, en este caso es de 1000 milisegundos que es igual a 1 segundo.

#### Resultado

![](../images/hola%20mundo%20pin10.gif)


### RETO No. 1
Modificar el codigo para que la luz se encienda por 100 milisegundos y se apage por 900 milisegundos. Con esto creamos un temporizador de 1 segundo.

### RETO No. 2
Crear un circuito y programa que encienda y apague dos led de forma alterna, es decir; enciende el primero, apaga el segundo, apaga el primero, enciende el segundo, sucesivamente.

### RETO No. 3
Crear el circuito y programa para hacer un semaforo, debe de permanecer en verde, luego parpadear 5 veces antes de pasar a amarillo, y luego pasar a rojo, luego iniciar la secuencia nuevamente. 

### RETO No. 4
Con varios LEDS, crear el efecto "Kit El Auto fantastico"

![](../images/efecto%20kit.gif)

---

## Uso Entradas Digitales

### Ejemplo # 1

En esta sección, veremos como utilizar un boton pulsador como entrada digital para encender un LED, mientras este se mantenga presionado.

### Conexión

![](../images/arduino_boton_led.png)

### Codigo

```cpp

int pinBoton=9;
int pinLed=5;

void setup()
{
  pinMode(pinBoton, INPUT_PULLUP); //pin conectado al boton
  pinMode(pinLed, OUTPUT); //led

}

void loop()
{
  if (digitalRead(pinBoton) == LOW) //si se presiono el boton
  {
     digitalWrite(pinLed,HIGH); //enciende el led
     delay(50); //delay para evitar rebotes con el boton
  
  }else
  {
    digitalWrite(pinLed,LOW);    
  }
}
```

La primera parte del sketch define dos variables para los dos pines que se va a utilizar. El 'pinLed' es un pin de salida y el 'pinBoton" se refiere al pulsador.

La función 'setup' define el pinBoton como una SALIDA, pero ahora tenemos una entradas que manejar. En este caso, utilizamos el pinMode como 'INPUT_PULLUP' según se muestra aqui:

```cpp
pinMode(pinBoton, INPUT_PULLUP); //pin conectado al boton
```
El modo de pin INPUT_PULLUP significa que el pin será utilizado como entrada, pero ademas le indica al Arduino que conecte internamente el pin con una resistencia de "pull-up", es decir que si no hay nada conectado a la entrada, este se conectara a VCC, por lo que recibirá un estado HIGH. cuando se presione el boton, el Arduino recibirá un estado LOW.

![](../images/internal-pull-up.png)

Esto lo debemo hacer cada vez que conectemos un boton a GND.

Debido a que la entrada es normalmente HIGH, y unicamente se cambia a LOW cuando el boton esta presionado, la logica que manejaremos en el boton sera "alreves".

### Ejemplo # 2:

Vamos a modificar el programa anterior para que al presionar el boton, el LED cambie de  estado, es decir, si el LED esta encendido que se apague, y si el LEDesta apagado que se encienda

### Conexión

La conexión es la misma que el ejemplo anterior

### Código

```cpp
boolean led_activo = false; //variable que nos servira para registra el estado del LED

void setup()
{
  pinMode(9, INPUT_PULLUP); //pin conectado al boton
  pinMode(5, OUTPUT); // pin conectado al LED
  digitalWrite (5, LOW); //inicializamos el LED en estado apagado
  led_activo=false; //iniciamos la variable de control el false, porque el led se inicia apagado
}

void loop()
{
  if (digitalRead(9) == LOW) //si se ha presionado el boton, entonces:
  {
    if (led_activo) //verificamos si el led esta encendido, mediante la variable de control
    {
      digitalWrite(5, LOW); //
      led_activo = false;
   
    }else
    {
      digitalWrite(5,HIGH);
    	led_activo=true;

  	}
  }
 
  delay(10);
}
```

## Uso de Salidas Analógicas

PENDIENTE ACTUALIZAR

## Uso de Entradas Analógicas

PENDIENTE ACTUALIZAR


## Ejercicio indicador de volumen



```cpp
// the setup routine runs once when you press reset:
void setup() {
  // initialize serial communication at 9600 bits per second:
  Serial.begin(9600);
   pinMode(10,OUTPUT); //pin con salida PWM para controlar brillo de LED
    pinMode(5,OUTPUT); 
    pinMode(6,OUTPUT); 
    pinMode(7,OUTPUT); 
}

// the loop routine runs over and over again forever:
void loop() {
  // read the input on analog pin 0:
  int sensorValue = analogRead(A0);
  // print out the value you read:
  Serial.println(sensorValue);
  sensorValue=(sensorValue+1)/4; // cambio de escala de 0 a 255
  analogWrite(10,sensorValue);

  if (sensorValue<=60) {
    digitalWrite(5,LOW);
    digitalWrite(6,LOW);
    digitalWrite(7,LOW);
   }else{
      if (sensorValue<=120){
        digitalWrite(5,HIGH);
        digitalWrite(6,LOW);
        digitalWrite(7,LOW);
       }else{
          if (sensorValue<=180){
              digitalWrite(5,HIGH);
              digitalWrite(6,HIGH);
              digitalWrite(7,LOW);
           }else{
              digitalWrite(5,HIGH);
              digitalWrite(6,HIGH);
              digitalWrite(7,HIGH);
           }
       }
    }
 
  delay(10);        // delay in between reads for stability
}
```


## Comunicacion Serial Con Arduino

### Envio de Datos desde Arduino

#### Ejercicio 1

Realizar un programa que envíe el texto "Hola Mundo" cuando se presione un boton

#### Ejercicio 2

Realizar un programa que vaya incrementando un número hasta llegar a 10 y lo envie por el puerto serie, por ejemplo, la primera vez que presiones debe enviar uno 1, la segunda vez debe enviar un 2, y sucesivamente.

#### Ejercicio 3

Modificar el programa anterior, para que al llegar el contador a 10, envíe un mensaje y reinicie el contador a 0.

### Recepcion de datos del Arduino

#### Ejemplo 1

Lectura de un caracter por el Arduino, lo desplegamos como **caracter** y como **entero**.

Los datos que enviamos desde la PC hacia el Arduino se envían en codigo ASCII.

```cpp
void setup()
{
  Serial.begin(9600);
}

void loop()
{
  if (Serial.available())
  {
  	char data = Serial.read();
    Serial.print("Tu me enviaste un caracter: ");
    Serial.print(data);
    Serial.print(" cuyo codigo ASCII es: ");
    Serial.println((int)data);
  }
}
```

### Ejercicios

Basado en el ejemplo, realize los siguientes ejercicios:

Reto No. 1

Hacer un programa que al recibir un caracter "a" encienda un LED, y al recibir una "b" apague el LED

Reto No. 2

Hacer un programa que haga parpadear un LED a 3 *velocidades* diferentes
- Cuando reciba una "q", parpadea *despacio*.
- Cuando reciba una "w", parpadea *medio*.
- Cuando reciba una "e", parpadea *rapido*.
EXTRA: cuando reciba una "x", que deje de parpadear.

Reto No. 3

Hacer un programa que al recibir un numero 1 al 9, lo multiplique por 100 y me devuelva el resultado. Si se recibe un caracter diferente, devuelva un mensaje de error.

Reto No. 4

Hacer un programa que al recibir un número del 1 al 7, calcule el FACTORIAL y devuelva el resultado, si se recibe un caracter diferente, devuelva un mensaje de error.
EXTRA: modificar el programa para que pueda recibir del 1 al 9, calcular el factoria.

