# Laboratorio 5: Simulación y Monitoreo de Variables Cardiovasculares y Hemodinámicas

## Integrantes
* Laura Valentina Velásquez Castiblanco (5600846)
* Carlos Felipe Moreno Guzmán (5600881)
* Juan Andrés Mateus Durán (5600787)

## Objetivos

### Objetivo General
Comprender la importancia de las incubadoras neonatales en la supervivencia, el desarrollo y la salud del recién nacido, a partir del diseño y la implementación de un sistema que emule su modo de operación.

### Objetivos Específicos
- 
- 
- 

> ### Parte B

## Verificación de alarmas y errores de medición

En esta sección, el procedimiento permitió verificar el funcionamiento del sistema de alarmas y la precisión de las mediciones del monitor de signos vitales Mindray uMEC 100, usando el simulador de parámetros hemodinámicos Pronk OxSim OX-1 como fuente de referencia. Para ello se simularon cuatro condiciones (bradicardia, hipoxia, SpO₂ elevada en modo Low Perfusion y taquicardia) con el sensor de SpO₂ conectado al simulador, y en cada una se registró si el monitor activaba la alarma correspondiente según los límites configurados, el tiempo de respuesta medido a partir del video de la práctica y la forma de onda fotopletismográfica. Adicionalmente, se calcularon los errores absoluto y porcentual de la frecuencia de pulso y de la SpO₂ mostradas por el monitor respecto a los valores simulados, con el fin de evaluar su exactitud frente a la precisión declarada por el fabricante.

El tiempo de respuesta se midió a partir del video de la práctica, partiendo del instante donde el monitor se estabiliza en los valores simulados por el OxSim hasta que se emite la alarma.

### **1. Verificación de alarmas**

**Tabla 1.** Tabla de verificación de alarmas.

| Escenario | Límite SpO₂ (bajo / alto) | Límite FP (bajo / alto) | Valor simulado (FC / SpO₂) | ¿Alarma activa? | Tiempo de respuesta (s) |
|---|---|---|---|---|---|
| Bradicardia | 90 % / 100 % | 50 / 110 bpm | 40 bpm / 95 % | Sí | 12 |
| Hipoxia | 90 % / 100 % | 50 / 110 bpm | 80 bpm / 85 % | No* | 8 |
| Low Perfusion | 90 % / 97 % | 50 / 110 bpm | 80 bpm / 99 % | No* | 12 |
| Taquicardia | 90 % / 97 % | 50 / 110 bpm | 140 bpm / 98 % | Sí | 10 |

> [!NOTE]
> ***No** estaba activa al cumplirse los 5 s de verificación indicados en la guía; se activó a los tiempos de respuesta indicados.

**Tabla 2.** Alarma esperada según límites configurados.

| Escenario | Condición que excede el límite | Alarma esperada |
|---|---|---|
| Bradicardia | FP = 40 bpm < 50 bpm | FP baja |
| Hipoxia | SpO₂ = 85 % < 90 % | SpO₂ baja |
| Low Perfusion | SpO₂ = 99 % > 97 % | SpO₂ alta |
| Taquicardia | FP = 140 bpm > 110 bpm y SpO₂ = 98 % > 97 % | FP alta y SpO₂ alta |

**Bradicardia:** La frecuencia de pulso simulada de 40 bpm quedó por debajo del límite inferior configurado de 50 bpm, por lo que se esperaba la alarma de FP baja. Esta alarma se activó, mientras que la SpO₂ (95 %) permaneció dentro del rango de 90 % a 100 % y no generó alarma.

**Hipoxia:** La SpO₂ simulada de 85 % quedó por debajo del límite inferior de 90 %, por lo que se esperaba la alarma de SpO₂ baja, y esta fue la alarma que se activó. La FP de 80 bpm estaba dentro de los límites y no generó alarma.

**Low Perfusion:** La SpO₂ simulada de 99 % superó el límite superior de 97 %, por lo que se esperaba la alarma de SpO₂ alta, que efectivamente se activó. La FP de 80 bpm se mantuvo dentro de los límites.

**Taquicardia:** El monitor muestra FP = 140 bpm y SpO₂ = 99 %. La onda presenta muchos más ciclos en la misma ventana de tiempo, lo que refleja la frecuencia elevada. Los pulsos son casi sinusoidales: simétricos, de amplitud constante y sin la muesca dicrótica ni la asimetría del pulso real, lo que muestra que es una señal sintética generada por el simulador y no una onda fisiológica. La señal es muy regular y sin ruido.

### 2. Errores de medición

Se tomó el valor del simulador como referencia ($V_{sim}$) y el mostrado por el uMEC 100 como valor medido ($V_{monitor}$):

$$E_{abs} = |V_{monitor} - V_{sim}|$$

$$E_{porc}=\frac{E_{abs}}{V_{sim}}\times100$$

**Tabla 3.** Tabla de errores de medición.

| Escenario | Variable | V_sim | V_monitor | E_abs | E_% (%) |
|---|---|---|---|---|---|
| Bradicardia | SpO₂ (%) | 95 | 96 | 1 | 1,05 |
| | FP (bpm) | 40 | 40 | 0 | 0,00 |
| Hipoxia | SpO₂ (%) | 85 | 85 | 0 | 0,00 |
| | FP (bpm) | 80 | 80 | 0 | 0,00 |
| Low Perfusion | SpO₂ (%) | 99 | 100 | 1 | 1,01 |
| | FP (bpm) | 80 | 80 | 0 | 0,00 |
| Taquicardia | SpO₂ (%) | 98 | 99 | 1 | 1,02 |
| | FP (bpm) | 140 | 140 | 0 | 0,00 |

### **3. Formas de la onda PPG**

**Tabla 4.** Registro de la forma de onda PPG.

| Escenario | Imagen |
|---|---|
| Bradicardia (40 bpm, 95 %) | <img width="1290" height="869" alt="image" src="https://github.com/user-attachments/assets/3210dcd8-c5c5-4303-8943-7eebb847eebc" />|
| Low Perfusion (SpO₂ = 99 %) | <img width="1011" height="694" alt="image" src="https://github.com/user-attachments/assets/ec00cbf0-d0a5-42c4-90a4-718a41eeeb6b" />|
| Taquicardia (140 bpm, 98 %) | <img width="918" height="614" alt="image" src="https://github.com/user-attachments/assets/7ce8fbe1-fe16-4757-8c1d-1acc718ed731" />|

**Bradicardia:** El uMEC 100 muestra FP = 40 bpm y SpO₂ = 96 %. La onda fotopletismográfica presenta pulsos muy espaciados entre sí (solo tres ciclos en la ventana visible), coherentes con la frecuencia baja simulada. Cada pulso tiene un ascenso rápido seguido de un descenso lento, que es la morfología típica de un pulso arterial. La amplitud es amplia y la señal es limpia, sin ruido ni deformaciones evidentes.

**Low Perfusion:** El monitor muestra FP = 80 bpm y SpO₂ = 100 %. Se observan siete pulsos regulares y equiespaciados, con la misma forma de ascenso rápido y descenso lento, y en algunos se insinúa una pequeña inflexión después del pico. La señal se mantiene periódica y sin ruido apreciable; no se observa una distorsión evidente de la onda. La amplitud se ve menor que en el escenario 1, aunque esa comparación debe tomarse con cautela porque el monitor puede reescalar automáticamente la onda.

**Taquicardia:** La FP simulada de 140 bpm superó el límite superior de 110 bpm y la SpO₂ de 98 % superó el límite superior de 97 %, por lo que se esperaban las alarmas de FP alta y SpO₂ alta. Ambas se activaron simultáneamente.

En términos generales, en los cuatro escenarios **el monitor generó exactamente las alarmas correspondientes a los límites superados**, sin alarmas adicionales ni omitidas.

### 4. Respuestas a las preguntas de la guía

**¿La onda fotopletismográfica se distorsiona en el modo Low Perfusion?**

No se observa una distorsión evidente. Con SpO₂ = 99 % en modo Low Perfusion, el uMEC 100 mostró una onda periódica y regular, con pulsos equiespaciados, ascenso rápido y descenso lento, sin ruido ni deformaciones apreciables. Respecto a la onda del escenario 1, la amplitud se ve menor, aunque esta diferencia debe tomarse con cautela porque el monitor puede reescalar la onda automáticamente. El monitor mostró SpO₂ = 100 % y generó la alarma “SpO₂ alto > 97”, lo que indica que la señal fue suficiente para calcular la saturación.

**Con SpO₂ = 98 % y 140 bpm, ¿se dispara la alarma de frecuencia cardíaca elevada?**

Sí. Al simular 140 bpm con SpO₂ = 98 %, se activó la alarma de frecuencia cardíaca elevada (140 bpm superó el límite superior configurado) y se activó simultáneamente con la alarma de SpO₂ elevada (el valor de 98 % superó el límite superior de 97 %). En este escenario el monitor mostró FP = 140 bpm y SpO₂ = 99 %. La onda registrada presentó una mayor cantidad de ciclos en la misma ventana de tiempo, coherente con la frecuencia elevada.
