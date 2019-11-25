# Sesion No. 5

# Arduino: Puerto Serial

En el ejemplo anterior enviamos los datos analogicos leidos por el Arduino hacia la PC por medio del puerto serial, ahora vamos a aprender más cosas sobre el puerto serial; por ejemplo como recibir en mensaje enviado desde la PC para controlar cosas como el encendido de un LED.

## Envio de datos por el puerto serial

Por el puerto serie podemos enviar caracteres, los cuales en realidad son convertidos en codigo [ASCII](https://www.ascii-code.com) antes de ser enviados por el puerto serial, en forma de bits.

### Ejemplo

El siguiente ejemplo, enviamos los numeros del 1 al 20 por el puerto serial, y luego volvemos a comenzar la cuenta.

Tambien veremos el uso del ciclo "for".

#### Conexion (Circuito)

En este caso no es necesaria ninguna conexión, mas que el Arduino conectado a nuestra computadora con el cable USB.

#### Programa (bloques)

![](cuenta-puerto-serie-bloques.png)

#### Programa (codigo)

```cpp
//variable "cuenta": nos sirve para llevar la cuenta del numero a imprimir por el puerto serie
int cuenta = 0;

//variable "counter": variable interna utilizada en el ciclo for
int counter;

void setup()
{ 
  //Siempre se debe inicializar el puerto, e indicar la velocidad, en este caso a 9600 bits por segundo
  Serial.begin(9600);

}

void loop()
{
  Serial.println("Hola, empezare a contar de 1 a 20");
  delay(300); //Espera de 300 millisecond(s)
  cuenta = 1;
  for (counter = 0; counter < 20; ++counter) {
    Serial.println(cuenta);
    cuenta += 1;
    delay(200); // Espera de 200 millisecond(s)
  }
  Serial.println("Termine de contar, empezare de nuevo");
  delay(300); // Espera de 300 millisecond(s)
}
```

#### Resultado

![](conteo-serie.gif)

### Reto No. 1
Modifique el codigo para enviar solo numeros pares del uno al 20.

### Reto No. 2
Modifique el programa para que envie los numeros de 1 hasta 20 de forma ascendente y luego continue de forma descendente, es decir, ..19, 18, 17... hasta regresar a 1, y continue sucesivamente.


## Recepción de datos por el puerto serial

Por medio del puerto serie, tambien podemos leer los datos recibidos y ejecutar alguna acción dependiendo del valor recibido.

### Ejemplo

En el siguiente ejemplo vamos leer un caracter recibido por el puerto serial, y encender el LED integrado en caso se reciba la letra "e" , o apagar en caso se reciba la letra "a".

#### Conexion (circuito)

No es necesaria ningun circuito, unicamente tener el Arduino conectado a la computadora por el cable USB

#### Programa en Bloques

![](leer-puerto-serial.png)

#### Codigo

```cpp
int caracter = 0;

void setup()
{
  Serial.begin(9600);

  pinMode(13, OUTPUT);
}

void loop()
{
  if (Serial.available() >= 1) {
    caracter = Serial.read();
    if (caracter == 101) {
      digitalWrite(13, HIGH);
    }
    if (caracter == 97) {
      digitalWrite(13, LOW);
    }
    Serial.println(caracter);
  }
  delay(10); // Delay a little bit to improve simulation performance
}
```

### Reto No. 3
Modifique el codigo del ejemplo, para que trabaje con los caracteres "1" para encender, y "0" para apagar.

### Reto No. 4
Modifique el codigo del ejemplo, para que en caso se reciba un caracter diferente a "e" o "a", devuelva un mensaje por el puerto serial indicando "caracter incorrecto"

### Reto No. 5
Cree un circuito que al recibir por medio del puerto serie los numero del "1" al "3", cambie el estado de tres leds diferente. 

Es decir, si recibe un "1", y el primer LED esta apagado, que lo encienda, pero si esta encendido, que lo apague.

Lo mismo al recibir un "2" con un segundo LED y al recibir "3" con un tercer LED.

Al recibir una "x" debe apagar todos los LED, independientemente del estado de los mismos.

En caso recibir un caracter diferente, se debe recibir por el puerto serie un mensaje indicando que el caracter es incorrecto.

### Reto No. 6
Conecte dos Arduinos por el puerto serial, y haga un circuito que al presionar un boton en el Arduino 1, este le envíe un caracter al Arduino 2, el Arduino 2 al recibir ese caracter especifico debe encender un LED.

PISTA: investigue el uso de los pines 0 y 1 en el Arduino UNO

---


