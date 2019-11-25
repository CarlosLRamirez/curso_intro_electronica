# Arduino: Salidas Digitales

En esta sesión vamos a aprender a crear el circuito y programa básico de Arduino. El "Hola Mundo" de la electrónica, el cual consiste en encender y apagar un LED.

##  Preparación

* Descargar e Instalar el Software [Arduino IDE ](https://www.arduino.cc/en/Main/Software)
* Conectar el Arduino con el cable USB
* Instalar drivers (si fuera necesario)
* Verificar la conexión de placa con el Arduino IDE

## Simulación con Tinkercad

Antes de empezar a "meter mano" con nuestra placa de Arduino, vamos a simular nuestro primer "Hola Mundo" utilizando Tinkercad.

### Programación por bloques
Tinkercad nos permite simular la conexión del Arduino, y crear "programas" mediante la union bloques, como si estuviarmos jugando con Legos, lo cual es de mucha ayuda si usted no tiene experiencia en programación, ya que nos permite comprender de mejor manera la "logica" de un programa.

NOTA: *Se recomienda colocar el idioma en ingles, ya que las traducciones de los bloques suelen ser un poco confusas.*

Este es el "Hola Mundo" en bloques, para encender y apagar de forma intermitente el LED integrado que viene incluido en la placa de Arduino UNO

![bloques hola mundo led integrado](hola-mundo-led-integrado.png)

Tinkercad tambien nos muestra el equivalente en código Arduino, el cual podemos guardar y cargar en nuestra placa real.

```cpp
void setup()
{
  pinMode(13, OUTPUT);
}

void loop()
{
  digitalWrite(13, HIGH);
  delay(1000); // Wait for 1000 millisecond(s)
  digitalWrite(13, LOW);
  delay(1000); // Wait for 1000 millisecond(s)
}
```


Aqui vemos el led integrado parpadeando o "blinkeando"


![](hola%20mundo%20led%20integrado.gif)

## EJEMPLO 2-1: 

Parpadeo de un LED conectado a la pin 10, el cual lo podemos utilizar como una SALIDA DIGITAL.

### Conexión del circuito

![](hola-mundo-pin-10-circuito.png)

### Programa (Bloques)

![](hola-mundo-pin-10.png)

### Programa (Codigo)

```c++
//Ejemplo salidas digitales -  Hola Mundo

// La rutina setup se ejecuta cuando encendemos el Arduino, 
// o presionamos el boton de reset:
void setup() {
  // inicializa el pin 10 como SALIDA (OUTPUT)
  pinMode(10, OUTPUT);
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

### Resultado

![](hola%20mundo%20pin10.gif)


### RETO No. 1
Modificar el codigo para que la luz se encienda por 100 milisegundos y se apage por 900 milisegundos. Con esto creamos un temporizador de 1 segundo.

### RETO No. 2
Crear un circuito y programa que encienda y apague dos led de forma alterna, es decir; enciende el primero, apaga el segundo, apaga el primero, enciende el segundo, sucesivamente.

### RETO No. 3
Crear el circuito y programa para hacer un semaforo, debe de permanecer en verde, luego parpadear 5 veces antes de pasar a amarillo, y luego pasar a rojo, luego iniciar la secuencia nuevamente. 

### RETO No. 4
Con varios LEDS, crear el efecto "Kit El Auto fantastico"

![](efecto%20kit.gif)

# Arduino: Entradas Digitales

-- en contruccion --