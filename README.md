# Electronica_Lab_FPGA_CYCLONE_IV_Finite_State_Machine
Implementacion de una maquina de estados finitos en FPGA CYCLONE IV EP4CE6E22C8

<img width="1086" height="710" alt="image" src="https://github.com/user-attachments/assets/040b6bc0-ea5c-46d1-9aff-f5773e9f8c73" />


Implementacion del ejercicio 2
https://youtu.be/t3R79dXACjQ

<img width="818" height="607" alt="image" src="https://github.com/user-attachments/assets/7052545a-04d6-429d-b172-ddbb187ffc27" />


RESUMEN TÉCNICO: IMPLEMENTACIÓN DE SISTEMAS LÓGICOS SECUENCIALES

1. ARQUITECTURA DE CONTROL (MÁQUINA DE ESTADOS)
El diseño implementa un modelo de Máquina de Estados Finito (FSM) para la automatización de un sistema de peaje.
- Entradas de control: `btn_open_falling` (apertura) y `sensor_pass_falling` (detección).
- Gestión temporal: Uso de `timer_count` con un umbral (`LIMIT-1`) para definir ciclos de tiempo.
- Estados definidos: `LOCKED`, `OPENING`, `OPENED`, `PASSING`, `CLOSING`, `ALARM_STATE`.

2. ESPECIFICACIONES TÉCNICAS DE SALIDA
El comportamiento del hardware es determinado por la lógica de estados:
- Actuadores (`motor_open`): Activación condicionada por el estado actual del sistema.
- Señalización (`led_alarm`): Gestión de indicadores visuales de alarma, con lógica de inhibición en `ALARM_STATE`.

3. IMPLEMENTACIÓN Y ENTORNO
- Lenguaje: VHDL (estándar IEEE STD_LOGIC_1164).
- Hardware: FPGA Cyclone IV  EP4CE6E22C8 (1.2V).
- Flujo de trabajo: Desarrollo en Quartus Prime, incluyendo simulación funcional e implementación de filtros antirrebote por hardware para la estabilidad de las entradas.
