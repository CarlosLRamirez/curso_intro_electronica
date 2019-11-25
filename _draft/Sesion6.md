# Sesion No. 6
 
# Uso de Funciones con Arduino

Una funcion permite a un programador segmentar el codigo y crear piezas modulares de codigo para realizar tareas definidas y luego retornar al area de codigo en donde la funcion fue "llamada".

Una función es de ayuda cuando necesitamos realizar la misma acción multiples veces en un mismo programa.

Una funcion recibe parametros y devuelve un resultado

![](anatomia-funcion-c.png)

### Ejemplo 1
```cpp
void setup(){
  Serial.begin(9600);
}

void loop() {
  int operando1 = 2;
  int operando2 = 3;
  int resultado;

  resultado = funcionMultiplicacion(operando1, operando2); // k now contains 6
  Serial.println(resultado);
  delay(500);
}

int funcionMultiplicacion(int x, int y){
  int result;
  result = x * y;
  return result;
}
```
### Ejemplo 2

Es posible que una funcion no devuelva ningun valor como resultado, en este caso debemos agregar la palabra void en la declaración de la función.
```cpp
void setup()
{
  pinMode(10, OUTPUT);
  
}


void loop()
{
  encender_led(10);
  delay(1000);
  apagar_led(10);
  delay(1000);
}


void encender_led(int pin){
  digitalWrite(pin,HIGH);
}

void apagar_led(int pin){
  digitalWrite(pin,LOW);
}
```

### Ejemplo 3
Tambien es posible que la función no reciba ningun parametro.

```cpp
void setup()
{
  pinMode(13, OUTPUT);
  pinMode(10, OUTPUT);
  
}


void loop()
{
  led_integrado_on();
  delay(1000);
  led_integrado_off();
  delay(1000);
}


void led_integrado_on(){
  digitalWrite(13,HIGH);
}

void led_integrado_off(){
  digitalWrite(13,LOW);
}


```

# Arduino: Fotocelda

Una fotocelda o fotoresistencia, como su nombre lo dice, varía su valor según la luz que recibe. El valor de resistencia es muy alto en la oscuridad y puede llegar hasta 150 Ω en plena luz.

Para poder convertir este valor de resistencia variable de modo que podamos medirlo con Arduino, debemos convertirlo a un voltaje. Esto lo podemos hacer en combinación con una resistencia de valor fijo. 

![](fotocelda-arduino.png)

La resistencia y la fotocelda en conjunto actúan como un potenciómetro. Cuando la luz es muy alta, la resistencia en la fotocelda es muy baja comparada con el valor de la resistencia fija, lo que es similar a que si un potenciómetro estuviera en su valor máximo.

Cuando la fotocelda se encuentra en la oscuridad, la resistencia toma un valor alto comparado con la resistencia fija, lo que es similar a un potenciómetro girado a GND.

## EJEMPLO

### Conexion (Circuito)

![](Leccion6.Fotocelda.png)

### Programa en bloques

Los bloques y el codigo es el mismo utilizado para leer un valor analógico
![](arduino-fotocelda-bloques.png)

### Codigo

```cpp
void setup()
{
  pinMode(A0, INPUT);
  Serial.begin(9600);

}

void loop()
{
  Serial.println(analogRead(A0));
  delay(1000); // Wait for 1000 millisecond(s)
}
```

> ### Reto No. 1
> Cree un solución que active un LED cuando sea de noche, y lo apague cuando sea de día.

> ### Reto No. 2
> Crear un circuito que detecte tres niveles de luz (mañana, tarde y noche). Y cambie el color en un LED RGB de acuerdo a estos tres niveles.

---

# Arduino: Sensor Ultrasonico

Vamos a ver el sensor de distancia de tipo ultrasónico, el cual se conoce como HC-SR04.

![](hc-sr04-diagram.png)

El sensor HC-SR04 utiliza 4 pines:
* VCC --> conectar 5VDC
* GND --> conectar GND
* TRIG --> conectar a una salida Digital
* ECHO --> conectar a una entrada Digital

Cuando el sensor recibe un pulso de 10 μs este realiza la medición de distancia y nos devuelve en el pin ECHO un pulso cuya duración es proporcional a la distancia medida.

## Ejemplo 

En este ejemplo vamos a aprender a utilizar librerías con Arduino.  Las librerías son muy útiles y nos permiten reutilizar codigo más complejo, lo cual nos facilita mucho el trabajo.  En este ejemplo vamos utilizar la librería **NewPing**, la cual se puede descargar [aqui](https://github.com/CarlosLRamirez/curso-intro-iot-arduino/blob/master/librerias/NewPing_v1.8.zip). 

Para inicializar el sensor, utilizamos el método constructor, indicando la entrada donde está cableado el pin de disparo, así como el de respuesta. El parámetro `max_cm_distance` es opcional. 

`NewPing sonar(trigger_pin, echo_pin [, max_cm_distance]);`

Para obtener la lectura de distancia del sensor en cm, utilizamos el metodo `sonar.ping_cm()`.

### Conexión

![](arduino-ultrasonico-circuito.png)

### Codigo

```cpp
/*
Codigo Ejemplo: Sensor Ultrasonica HC-SR04
Uso de la libreria NewPing
https://playground.arduino.cc/Code/NewPing/
*/

#include <NewPing.h>
 
#define PIN_DISPARO  8
#define PIN_RESPUESTA     9
#define DISTANCIA_MAX 200
 
NewPing sonar(PIN_DISPARO, PIN_RESPUESTA, DISTANCIA_MAX);
 
void setup() {
  Serial.begin(115200);
}
 
void loop() {
  delay(50);
  Serial.print("Ping: ");
  Serial.print(sonar.ping_cm());
  Serial.println("cm");
}
```
> 
> ## Reto No. 1
> Cree una solución que si detecta un objeto a menos de 20cm, encienda un LED.


> ## Reto No. 2
> Cree una solución que si detecta que un objeto esta a menos de 50cm, y durante al menos un minuto, encienda un LED.
>  
> 
> Y apague el LED, cuando ya no detecte el objeto por un minuto.

> ## Reto No. 3
> Cree una solución que pueda medir la longitud de los lados de una caja cuadrara y pueda calcular su área.



# Arduino: Sensor de Temperatura LM35

En esta Ejemplo vamos a aprender a utilizar el sensor de temperatura LM35 y el TMP36 los cuales funcionan de manera similar. Este sensor lo alimentamos con 5V y GND, y este devuelve un voltaje analógico el cual es directamente proporcional al valor de temperatura medido en °C, especificamente 10 miliVolts por cada °C. 

Por ejemplo, el sensor LM35, para una temperatura de 30°C nos devuelve en su salida 300mV, es decir 0.3V. 

La diferencia del sensor TMP36 es que este aplica una compensación de 0.5V, es decir que para una temperatura de 30°C, este devolvería 0.8V (0.5V + 0.3V). Lo cual lo debemos de tener en cuenta al momento de calcular la temperatura medida.

Para obtener el valor en °C a partir del valor medido por la entrada analogica del Arduino debemos de aplicar la fórmula siguiente:

> LM35:
> Temperatura=100*(5*analogRead/1024) 

> TMP36:
> Temperatura=100*[5*analogRead/1024)-0.5] 

# Conexión

![](arduino-lm35-sensor_temperatura.PNG)

# Codigo

```cpp
//Sensor de Temperatura LM35 y TMP36 con Arduino

//Usamos el pin A0 como entrada analogica que viene del sensor de temperatura
int pinSensor =0;

//utilice dcOffset = 0V para el sensor LM35 o 0.5V para el sensor TMP36
float dcOffset=0.0;
//float dcOffset=0.5;


// La rutina setup se ejecuta cuando encendemos el Arduino, 
// o presionamos el boton de reset:
void setup() {

  //analogReference(INTERNAL);
  Serial.begin(9600); //inicializamos el puerto serial a 9600 baudrate
  Serial.println("Aprendiendo Internet de las Cosas");
  Serial.println("Intecap - Centro Tics");
}

//La rutina loop se ejecuta una y otra vez, de forma infinita:
void loop() {
  //leemos el valor analogico del pin A0 y lo guardamos en una variable 
  int valorSensor  = analogRead(pinSensor); 
  //escribimos el valor de la variable en el puerto serial
  Serial.print("Valor del Sensor: ");
  Serial.print(valorSensor);

  float voltaje = (valorSensor/1024.0) * 5.0 ;
  Serial.print(", Volts: ");
  Serial.print(voltaje);
  
  float temperatura = (voltaje - dcOffset) * 100.0;
  Serial.print(", Temperatura en °C: ");
  Serial.println(temperatura);
  
  delay(2000);
}
```





