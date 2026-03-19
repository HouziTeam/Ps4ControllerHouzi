# PS4-esp32
Usa un mando de PS4 con un ESP32

Este proyecto se basa en gran medida en el trabajo de Jeffery Pernis para conectar un mando de PS3 a un ESP32. Puedes encontrarlo aquí: https://github.com/jvpernis/esp32-ps3

Aquí tienes un vídeo sobre cómo se creó esta librería.

Puedes descargar este repositorio como un archivo ZIP e importarlo al IDE de Arduino como una librería.

## Installation
The instructions on how to do this are base off what can be found [here](https://github.com/jvpernis/esp32-ps3/issues/3#issuecomment-517141523)
> The instructions below may no longer work. If they do not work for you, try applying changes from the various forks of this repo.
1. You can add the ESP32 boards to your Arduino IDE by adding them to the Boards Manager:
    1. Open `File -> Preferences`
    1. Paste the following URL in the `Additional Boards Manager URLs` field:
    `https://dl.espressif.com/dl/package_esp32_index.json`
    1. Open the Boards Manager with `Tools -> Board: "xxx" -> Boards Manager`
    1. Look for `esp32` (probably the last one in the list), and click `install` (version 1.0.3 works best)
    1. Select the ESP32 board you have with `Tools -> Board: "xxx"` under the section `ESP32 Arduino`
1. To install this library into your Arduino IDE:
    1. Click on the "Code" button in the top right of this page
    1. Select "Download Zip" (It's always a good idea to look through the code on this page first to make sure you know what you're downloading)
    1. In the Arduino IDE, navigate to `Sketch -> Include Library -> Add .ZIP Library`, then select the file you just downloaded 

## Emparejamiento del mando de PS4:

Cuando un mando de PS4 se "empareja" con una consola PS4, significa que ha almacenado la dirección MAC Bluetooth de la consola, que es el único dispositivo al que se conectará el mando. Normalmente, este emparejamiento se produce al conectar el mando a la consola PS4 mediante un cable USB y pulsar el botón PS. Esto inicia la escritura de la dirección MAC de la consola en el mando.

Por lo tanto, si quieres conectar tu mando de PS4 al ESP32, necesitas averiguar cuál es la dirección MAC Bluetooth de tu consola PS4 y configurar la dirección del ESP32 con ella, o bien cambiar la dirección MAC almacenada en el mando de PS4.

Sea cual sea el método que elijas, es posible que necesites una herramienta para leer y/o escribir la dirección MAC actualmente emparejada del mando de PS4. Puedes probar sixaxispairer para este propósito.

Si optaste por cambiar la dirección MAC del ESP32, deberás incluir la dirección IP en la función PS4.begin() dentro de la función setup() de Arduino como se muestra a continuación, donde 1a:2b:3c:01:01:01 es la dirección MAC (ten en cuenta que la dirección MAC debe ser unicast):
```
void setup()
{
    PS4.begin("1a:2b:3c:01:01:01");
    Serial.println("Ready.");
}
```
