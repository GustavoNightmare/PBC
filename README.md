# Sistema de Monitoreo de Temperatura y Humedad — ESP32-E
Proyecto de la asignatura **Énfasis II – Diseño de Componentes** (Universidad del Cauca).

> PCB + esquemáticos (EasyEDA) + modelo 3D de la carcasa (Fusion 360) para un sistema de medición de temperatura y humedad con precisión suficiente para conservar compuestos farmacéuticos en condiciones óptimas.


---

## Tabla de contenido
- [Objetivo](#objetivo)
- [Características](#características)
- [Arquitectura del sistema](#arquitectura-del-sistema)
- [Hardware](#hardware)
- [Diseño PCB y esquemáticos](#diseño-pcb-y-esquemáticos)
- [Carcasa y modelo 3D](#carcasa-y-modelo-3d)
- [Firmware (opcional)](#firmware-opcional)
- [Montaje y puesta en marcha](#montaje-y-puesta-en-marcha)
- [Calibración](#calibración)
- [BOM — Lista de materiales](#bom--lista-de-materiales)
- [Estructura del repositorio](#estructura-del-repositorio)
- [Licencia](#licencia)
- [Autores](#autores)
- [Agradecimientos](#agradecimientos)

---

## Objetivo
Desarrollar un dispositivo compacto que mida **temperatura** y **humedad relativa** con buena precisión, basado en **ESP32-E**, integrando:
- Electrónica propia (PCB de 2 capas),
- Sensado de T/H,
- Regulación de 5 V → 3.3 V,
- Carcasa impresa en 3D para encapsular la placa y asegurar la protección mecánica.

## Características
- **MCU / Conectividad:** ESP32-E (Wi-Fi/Bluetooth).
- **Alimentación:** 5 V de entrada, regulada a 3.3 V para la lógica.
- **Sensor T/H:** (reemplazar por el modelo exacto, p. ej. *SHT31-D* o *DHT22*).
- **PCB:** diseñado en **EasyEDA**.
- **Carcasa:** modelada en **Fusion 360** (tapas superior e inferior, separadores y guías).
- **Uso previsto:** monitoreo de condiciones para almacenamiento de compuestos farmacéuticos.

## Arquitectura del sistema
1. Fuente de 5 V → regulador → **3.3 V** para ESP32 y sensor.  
2. **ESP32-E** lee el sensor de T/H (I²C o 1-Wire según el sensor que elijas).  
3. (Opcional) Publicación de datos por Wi-Fi (HTTP/MQTT) o visualización local por USB/Serial.  
4. Carcasa 3D que **encapsula** la PCB y facilita el montaje.

## Hardware
- **Microcontrolador:** ESP32-E.
- **Regulación 5 V → 3.3 V:** LDO o step-down (indicar modelo real usado; p. ej. AMS1117-3.3 o MP1584).  
- **Sensor T/H:** indicar referencia y protocolo.  
- **Conectores:** alimentación, programación (UART), y encabezados para el sensor.  
- **Protecciones sugeridas:** diodo de protección de polaridad, TVS/ESD en líneas de señal (si aplica).  
- **Fijación:** orificios para tornillería **M3** y separadores impresos/nylon.

## Diseño PCB y esquemáticos
- Herramienta: **EasyEDA**.  
- Capas: 2 (espesor y cobre según proveedor).  
- Reglas típicas: clearances y anchos de pista compatibles con 1 oz; ajustar si el proveedor cambia.  
- Archivos incluidos:
  - `hardware/esquematicos/` → archivos del esquema y PDF exportado.
  - `hardware/pcb/` → diseño PCB.
  - `hardware/gerbers/` → **Gerbers** listos para fabricar.
- **Notas:** se añadieron las conexiones a ESP32-E, la etapa de regulación 5 V→3.3 V y el footprint del sensor T/H.

## Carcasa y modelo 3D
- Herramienta: **Autodesk Fusion 360**.  
- Contenido:
  - `mechanical/fusion/` → archivo fuente (.f3d).  
  - `mechanical/stl/` → piezas para impresión (tapa superior, base, soportes).  
- Recomendaciones de impresión:
  - Material: **PLA** o **PETG** (para mayor resistencia térmica, preferir PETG).
  - Altura de capa: 0.2 mm; relleno 20–30 %.
  - Tolerancias: dejar **0.3–0.5 mm** de holgura para encajes.
  - Tornillería: M3 x (longitud según separación de la PCB).
