# TFG - Adquisición y Publicación de Señales CAN vía MQTT (Nissan Leaf AZE0)

Este repositorio contiene el código Python desarrollado en el marco de un Trabajo Fin de Grado para la lectura, decodificación y publicación de señales CAN específicas del vehículo **Nissan Leaf AZE0**. Las señales capturadas son filtradas y enviadas mediante el protocolo **MQTT** a un broker remoto previamente configurado.

---

## Ejecución del script principal

El script principal de este proyecto es `CAN_FILTER.py`. Este archivo se encarga de:

- Leer tramas CAN desde un lector USB-CAN conectado por puerto serie.
- Decodificar las señales usando un archivo `.dbc`.
- Filtrar las señales definidas en el diccionario `SENIALES_PERMITIDAS`.
- Escalarlas y publicarlas vía MQTT.

---

## Requisitos del sistema

Este código ha sido probado en una máquina virtual con **Ubuntu**. Para ejecutarlo correctamente, es necesario asegurarse de tener instaladas las siguientes dependencias:

```bash
sudo apt update
sudo apt install python3 python3-pip
pip3 install python-can cantools paho-mqtt
```
---

## Configuración del broker MQTT

Antes de ejecutar el script:
- Se debe haber configurado un broker Mosquitto, ya sea local o remoto.
- En el archivo CAN_FILTER.py, se localiza la línea donde se define la IP del broker y se modifica la IP por la del servidor que se esté usando. Por ejemplo:
```bash
MQTT_BROKER = "195.0.1.60"
```
---

## Señales compatibles
Este script está diseñado específicamente para el Nissan Leaf AZE0 (2014).
Las señales extraídas y publicadas son un subconjunto predefinido en el diccionario SENIALES_PERMITIDAS, que incluye valores como:
- Velocidad de las ruedas.
- Temperatura del paquete de baterías.
- Posición del acelerador.
- Presiones de freno.
- Fuerza de frenado.
- Código de diagnóstico (DTC).


---

## Archivo .dbc
Dentro del repositorio se incluye una carpeta llamada dbc/ que contiene el archivo necesario para decodificar los mensajes CAN: dbc/Nissan_Leaf_AZE0.dbc

⚠️ IMPORTANTE:

Si cambias la ubicación del archivo .dbc o si ejecutas el código desde un sistema operativo distinto (por ejemplo, Windows), asegúrate de modificar la ruta en el código dentro de CAN_FILTER.py, en la sección donde se carga el archivo:
dbc_path = "dbc/Nissan_Leaf_AZE0.dbc"

---

## Ejecución
Una vez configurado todo, puedes ejecutar el script con:
```bash
python3 CAN_FILTER.py
```
