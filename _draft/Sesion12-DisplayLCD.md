# Conexión de Display LCD 16x2

## Display LCD 16x2 con Arduino

Para Arduino, se debe utilizar la libreria llamada LiquidCrystal, la cual nos permite controlar los display LCD que son compatibls con el driver Hitachi HD44780. Generalmente estas traen una interfaz de 16 pines.

En este sketch de ejemplo, se muestra como imprimir "Hola Mundo" en la LCD, y se muestra el tiempo en segundos desde que el Arduino fue reiniciado.

![](Arduino_lcd_example.png)v

Las LCD tienen una interfaz paralela, lo que significa que el microcontrolador tiene que manipular varios pines de la interfaz al mismo tiempo para controlar el display. La interfaz consiste en los siguientes pines:


**RegisteReSelect (RS):** este pin controla en que parte de la memoria de la LCD se escriben los datos. Se puede seleccionar ya sea los registros de datos, lo cual guarda lo que se muestra en la pantalla, o el registro de instrucciones, el cual guarda las instrucciones que debe realizar el controlador de la LCD.

**Read/Write (R/W):** con este pin se selecciona el modo lectura o escritura.

**Enable:** este pin habilita la escritura en los registros.

**8 pines de datos (D0 -D7):** El estado de estos pines (alto o bajo) son los valores de los bits que se escriben en el registro al momento  de escribir, asi como los valores que se leen al momento de leer.

Tambien hay un pin de **Contraste del display (Vo)**, pines de **alimentacion**, y pines **energia del LED de la luz de fondo**,pin para **controlar el contraste** del display, y para **encender o apagar el led** de fondo respectivamente.

El proceso de controlar el display consiste en colcoar los datos que forman la imagen que queremos desplegar en los registros de datos, y luego poner las instrucciones en el registro de instrucciones. La libreria LiquiedCrystal simplifica este proceso, para no tener que conocer las instrucciones de bajo nivel. 

Las LCD compatibles con el driver Hitachi pueden ser controladas en dos modos: 4-bits y 8-bits. El modo 4-bit requiere 7 pines E/S del Arduino, mientras el modo 8 bits requiere 11 pines. Para desplegar el texto en la pantalla, se puede hacer casi todo en el modo 4-bits, por lo que el ejemplo muestra como controlar una pantalla 16x2 en modo 4-bits.

### Material requerido

* Placa Arduino o Genuino
* Pantalla LCD  (compatible con el drier Hitachi HD44780)
* Potenciometro de 10k ohm
* Resistencia de 220 ohm
* Jumpers
* Protoboard

### Conexión del circuito

La conexión de va de la siguiente manera:

* pin RS de la LCD al pin digital 12 del Arduino
* pin Enable de la LCD al pin digital 11 del Arduino
* pin D4 de la LCD al pin digital 5 del Arduino
* pin D5 de la LCD al pin digital 4 del Arduino
* pin D6 de la LCD al pin digital 3 del Arduino
* pin D7 de la LCD al pin digital 2 del Arduino

Adicionalmente se debe cablear un potenciometro de 1Kohm a +5V y GND, y la salida de este al pin VO de la LCD (pin 3). 

Conectar el LED de la luz de fondo (pin 15 y 16) con una resistencia de 220ohm para proteger el LED.

![](arduino_lcd16x2.png)

### Esquematico

![](arduino-lcd-squematic.png)v

### Codigo

```cpp
/*
  LiquidCrystal Library - Hello World

 Demonstrates the use a 16x2 LCD display.  The LiquidCrystal
 library works with all LCD displays that are compatible with the
 Hitachi HD44780 driver. There are many of them out there, and you
 can usually tell them by the 16-pin interface.

 This sketch prints "Hello World!" to the LCD
 and shows the time.

  The circuit:
 * LCD RS pin to digital pin 12
 * LCD Enable pin to digital pin 11
 * LCD D4 pin to digital pin 5
 * LCD D5 pin to digital pin 4
 * LCD D6 pin to digital pin 3
 * LCD D7 pin to digital pin 2
 * LCD R/W pin to ground
 * LCD VSS pin to ground
 * LCD VCC pin to 5V
 * 10K resistor:
 * ends to +5V and ground
 * wiper to LCD VO pin (pin 3)

 Library originally added 18 Apr 2008
 by David A. Mellis
 library modified 5 Jul 2009
 by Limor Fried (http://www.ladyada.net)
 example added 9 Jul 2009
 by Tom Igoe
 modified 22 Nov 2010
 by Tom Igoe

 This example code is in the public domain.

 http://www.arduino.cc/en/Tutorial/LiquidCrystal
 */

// include the library code:
#include <LiquidCrystal.h>

// initialize the library with the numbers of the interface pins
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

void setup() {
  // set up the LCD's number of columns and rows:
  lcd.begin(16, 2);
  // Print a message to the LCD.
  lcd.print("hola, mundo!");
}

void loop() {
  // set the cursor to column 0, line 1
  // (note: line 1 is the second row, since counting begins with 0):
  lcd.setCursor(0, 1);
  // print the number of seconds since reset:
  lcd.print(millis() / 1000);
}
```

### Libreria

Enlace a la libreria <a href="https://www.arduino.cc/en/Reference/LiquidCrystal" target="_blank">LiquidCrystal.h</a>


## Display LCD 16x2 con Raspberry Pi

El siguiente ejemplo muestra controlar una pantalla LCD 16x2 a traves de Python en la Rapsberry Pi, el programa envía la fecha y la hora, y la dirección IP del RPI para que se muestre en la pantalla.

### Conexión

Este ejemplo aplica para un display de 5V, pero unicamente se envían datos del Rpi a la pantalla, no se leen datos de la memoria hacia el RPI, por lo que el pin RW (read/write) del display se conecta a GND, ya que no se quiere que el display envie 5V a los pines del GPIO del RPI.


| LCD                      | RPI                                 |
|--------------------------|-------------------------------------|
| pin # 1                  | GND                                 |
| pin # 2                  | +5V                                 |
| pin # 3  (Vo)            | al medio de un potenciometro de 10K |
| pin # 4 (RS)             | GPIO22                              |
| pin # 5 (RW)             | a GND                               |
| pin # 6 (EN)             | GPIO17                              |
| pins # 7, # 8, # 9, # 10 | no conectar                         |
| pin # 11 (D4)            | GPIO25                              |
| pin # 12 (D5)            | GPIO24                              |
| pin # 13 (D6)            | GPIO23                              |
| pin # 14 (D7)            | GPIO18                              |
| pin # 15 (LED+)          | +5V                                 |
| pin # 15 (LED-)          | a GND con una resistencia de 220ohm |

### Paquetes necesarios

**Instalar pip3**

`$ sudo apt-get install python3-pip`

**Instalar la libreria adafruit-blinka**

`$ sudo pip3 install adafruit-blinka`

**Instalar la libreria adafruit-circuitpython-charlcd**

`$ sudo pip3 install adafruit-circuitpython-charlcd`

### Script en Python

```python
from subprocess import Popen, PIPE
from time import sleep
from datetime import datetime
import board
import digitalio
import adafruit_character_lcd.character_lcd as characterlcd

# Modify this if you have a different sized character LCD
lcd_columns = 16
lcd_rows = 2

# compatible with all versions of RPI as of Jan. 2019
# v1 - v3B+
lcd_rs = digitalio.DigitalInOut(board.D22)
lcd_en = digitalio.DigitalInOut(board.D17)
lcd_d4 = digitalio.DigitalInOut(board.D25)
lcd_d5 = digitalio.DigitalInOut(board.D24)
lcd_d6 = digitalio.DigitalInOut(board.D23)
lcd_d7 = digitalio.DigitalInOut(board.D18)


# Initialise the lcd class
lcd = characterlcd.Character_LCD_Mono(lcd_rs, lcd_en, lcd_d4, lcd_d5, lcd_d6,
                                      lcd_d7, lcd_columns, lcd_rows)

# looking for an active Ethernet or WiFi device
def find_interface():
    find_device = "ip addr show"
    interface_parse = run_cmd(find_device)
    for line in interface_parse.splitlines():
        if "state UP" in line:
            dev_name = line.split(':')[1]
    return dev_name

# find an active IP on the first LIVE network device
def parse_ip():
    find_ip = "ip addr show %s" % interface
    find_ip = "ip addr show %s" % interface
    ip_parse = run_cmd(find_ip)
    for line in ip_parse.splitlines():
        if "inet " in line:
            ip = line.split(' ')[5]
            ip = ip.split('/')[0]
    return ip

# run unix shell command, return as ASCII
def run_cmd(cmd):
    p = Popen(cmd, shell=True, stdout=PIPE)
    output = p.communicate()[0]
    return output.decode('ascii')

# wipe LCD screen before we start
lcd.clear()

# before we start the main loop - detect active network device and ip address
sleep(2)
interface = find_interface()
ip_address = parse_ip()

while True:

    # date and time
    lcd_line_1 = datetime.now().strftime('%b %d  %H:%M:%S\n')

    # current ip address
    lcd_line_2 = "IP " + ip_address

    # combine both lines into one update to the display
    lcd.message = lcd_line_1 + lcd_line_2

    sleep(2)
```

### Ejecutar el codigo

Si guardamos el script con el nombre *"LCD_16x2_en_Raspberry_pi.py"*, lo ejecutamos con la siguiente instrucción en la linea de comandos

`$ sudo python3 ./LCD_16x2_en_Raspberry_pi.py`

## Control de Pantalla LCD con NODE-RED en Raspberry Pi

El nodo llamado *node-red-node-pilcd*  que permite controlar las pantallas LCD que se basan el el driver Hitachi HD44780 mediante un Raspberry Pi.

![](node-rpi-lcd.png)v  

En enlace a la documentación se encuentra <a href="https://flows.nodered.org/node/node-red-node-pilcd" target="_blank">aqui</a>.

