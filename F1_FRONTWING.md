# 🔧 Proyecto 1 – Sistema de Telemetría para Ala Frontal de F1

## 📌 1. Resumen Ejecutivo
Breve descripción del proyecto, justificación y objetivo.

**Objetivo general:**  
Diseñar un sistema de adquisición y visualización de datos de presión en tiempo real para una maqueta de ala frontal de F1, utilizando un microcontrolador STM32F446RE y una Raspberry Pi 4.

**Objetivos específicos:**
- Leer sensores de presión desde el STM32.
- Transmitir los datos mediante protocolo CAN.
- Visualizar en tiempo real los datos en la Raspberry Pi con un dashboard en Python.
- Comparar los datos reales con una simulación CFD.

**Tecnologías utilizadas:**  
STM32F446RE, MCP2551, CAN Bus, Python, Dash/Plotly, Siemens NX/Fusion 360 (CFD), Raspberry Pi 4.

---

## 📐 2. Diseño del Sistema

### 📊 Diagrama de bloques
_(Aquí debes insertar un esquema general del flujo de datos)_

### 🔌 Arquitectura de comunicación
- STM32 → CAN TX/RX → MCP2551 → Bus CAN → Raspberry Pi (CAN-USB)

### 🔧 Componentes usados

| Componente | Modelo     | Descripción                          |
|------------|------------|--------------------------------------|
| MCU        | STM32F446RE| Lectura de sensores y envío de datos|
| Sensor     | MPX5010    | Captura de presión aerodinámica     |
| Transceptor CAN | MCP2551 | Conversión de señal CAN           |
| Receptor   | RPi 4      | Visualización y análisis de datos   |
| Dashboard  | Dash (Py)  | Interfaz gráfica en tiempo real     |

---

## 🧪 3. Selección y Pruebas de Hardware

### 📋 Lista de materiales
- STM32F446RE
- MCP2551
- MPX5010
- Raspberry Pi 4
- Cables y resistencias de 120Ω

### 🔬 Pruebas iniciales
- Prueba de lectura analógica del sensor.
- Prueba de envío CAN desde STM32 a PC o Pi.

---

## 💻 4. Desarrollo del Firmware STM32

### 🧠 Estructura del código
- Setup: ADC + CAN config
- Loop: Leer sensor, empaquetar datos, enviar por CAN

### 📎 Snippet ejemplo
```c
HAL_CAN_AddTxMessage(&hcan1, &TxHeader, TxData, &TxMailbox);
