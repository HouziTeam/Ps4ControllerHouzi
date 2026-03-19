# PS4-esp32
Usa un mando de PS4 con un ESP32

Este proyecto se basa en gran medida en el trabajo de Jeffery Pernis para conectar un mando de PS3 a un ESP32. Puedes encontrarlo aquí: https://github.com/jvpernis/esp32-ps3

Aquí tienes un vídeo sobre cómo se creó esta librería.

Puedes descargar este repositorio como un archivo ZIP e importarlo al IDE de Arduino como una librería.

## Instalación
Las instrucciones sobre cómo hacer esto se basan en lo que se puede encontrar [CLICK](https://github.com/jvpernis/esp32-ps3/issues/3#issuecomment-517141523)
> Es posible que las instrucciones que aparecen a continuación ya no funcionen. Si no le funcionan, intente aplicar los cambios de las distintas versiones de este repositorio.
1. Puedes añadir las placas ESP32 a tu IDE de Arduino agregándolas al Administrador de placas:

    A. Abre `Archivo -> Preferencias`

    B. Pega la siguiente URL en el campo `URLs adicionales del Administrador de placas`:

        `https://dl.espressif.com/dl/package_esp32_index.json`

    C. Abre el Administrador de placas con `Herramientas -> Placa: "xxx" -> Administrador de placas`

    D. Busca `esp32` (probablemente la última de la lista) y haz clic en `Instalar` (la versión             1.0.3 funciona mejor)

    E. Selecciona la placa ESP32 que tienes con `Herramientas -> Placa: "xxx"` en la sección `ESP32`
2. Para instalar esta biblioteca en tu IDE de Arduino:

    A. Haz clic en el botón "Código" en la esquina superior derecha de esta página.

    B. Selecciona "Descargar ZIP" (siempre es recomendable revisar el código de esta página primero         para asegurarte de saber qué estás descargando).

    C. En el IDE de Arduino, ve a `Programa -> Incluir biblioteca -> Agregar biblioteca .ZIP` y               selecciona el archivo que acabas de descargar.

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
