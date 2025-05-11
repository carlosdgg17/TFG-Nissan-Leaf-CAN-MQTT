# 📡 TFG - Adquisición y Publicación de Señales CAN vía MQTT (Nissan Leaf AZE0)

Este repositorio contiene el código Python desarrollado en el marco de un Trabajo Fin de Grado para la lectura, decodificación y publicación de señales CAN específicas del vehículo **Nissan Leaf AZE0**. Las señales capturadas son filtradas y enviadas mediante el protocolo **MQTT** a un broker remoto previamente configurado.

---

## 🚀 Ejecución del script principal

El script principal de este proyecto es `CAN_FILTER.py`. Este archivo se encarga de:

- Leer tramas CAN desde un lector USB-CAN conectado por puerto serie.
- Decodificar las señales usando un archivo `.dbc`.
- Filtrar las señales definidas en el diccionario `SENIALES_PERMITIDAS`.
- Escalarlas y publicarlas vía MQTT.

---

## 📦 Requisitos del sistema

Este código ha sido probado en una máquina virtual con **Ubuntu**. Para ejecutarlo correctamente, asegúrate de tener instaladas las siguientes dependencias:

```bash
sudo apt update
sudo apt install python3 python3-pip
pip3 install python-can cantools paho-mqtt
```
---

## 🖥️ Configuración del broker MQTT

Antes de ejecutar el script:
- Debes haber configurado un broker Mosquitto, ya sea local o remoto.
- En el archivo CAN_FILTER.py, localiza la línea donde se define la IP del broker y modifica la IP por la del servidor que estés usando. Por ejemplo:
MQTT_BROKER = "195.0.1.60"
