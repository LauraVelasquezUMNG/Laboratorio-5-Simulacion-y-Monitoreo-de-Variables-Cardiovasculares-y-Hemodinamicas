# Laboratorio 5: Simulación y Monitoreo de Variables Cardiovasculares y Hemodinámicas

## Integrantes
* Laura Valentina Velásquez Castiblanco (5600846)
* Carlos Felipe Moreno Guzmán (5600881)
* Juan Andrés Mateus Durán (5600787)

## Objetivos

### Objetivo General
Operar con el simulador Pronk OxSim (OX-1) y el monitor de signos vitales uMEC 100 para pruebas funcionales.

### Objetivos Específicos
- Identificar los modos de operación de un simulador de parámetros hemodinámicos (Pronk OxSim).
- Verificar los límites de medición de un monitor de signos vitales mediante simulación de variables hemodinámicas.
- Interpretar variaciones en los parámetros hemodinámicos asociadas a estados fisiológicos y patológicos.

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
> *No estaba activa al cumplirse los 5 s de verificación indicados en la guía; se activó a los tiempos de respuesta indicados.

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
| Bradicardia (40 bpm, 95 %) | <img width="500" alt="image" src="https://github.com/user-attachments/assets/3210dcd8-c5c5-4303-8943-7eebb847eebc" /> |
| Low Perfusion (SpO₂ = 99 %) | <img width="500" alt="image" src="https://github.com/user-attachments/assets/ec00cbf0-d0a5-42c4-90a4-718a41eeeb6b" /> |
| Taquicardia (140 bpm, 98 %) | <img width="500" alt="image" src="https://github.com/user-attachments/assets/7ce8fbe1-fe16-4757-8c1d-1acc718ed731" /> |

**Bradicardia:** El uMEC 100 muestra FP = 40 bpm y SpO₂ = 96 %. La onda fotopletismográfica presenta pulsos muy espaciados entre sí (solo tres ciclos en la ventana visible), coherentes con la frecuencia baja simulada. Cada pulso tiene un ascenso rápido seguido de un descenso lento, que es la morfología típica de un pulso arterial. La amplitud es amplia y la señal es limpia, sin ruido ni deformaciones evidentes.

**Low Perfusion:** El monitor muestra FP = 80 bpm y SpO₂ = 100 %. Se observan siete pulsos regulares y equiespaciados, con la misma forma de ascenso rápido y descenso lento, y en algunos se insinúa una pequeña inflexión después del pico. La señal se mantiene periódica y sin ruido apreciable; no se observa una distorsión evidente de la onda. La amplitud se ve menor que en el escenario 1, aunque esa comparación debe tomarse con cautela porque el monitor puede reescalar automáticamente la onda.

**Taquicardia:** La FP simulada de 140 bpm superó el límite superior de 110 bpm y la SpO₂ de 98 % superó el límite superior de 97 %, por lo que se esperaban las alarmas de FP alta y SpO₂ alta. Ambas se activaron simultáneamente.

En términos generales, en los cuatro escenarios **el monitor generó exactamente las alarmas correspondientes a los límites superados**, sin alarmas adicionales ni omitidas.

### 4. Respuestas a las preguntas de la guía

**¿La onda fotopletismográfica se distorsiona en el modo Low Perfusion?**

No se observa una distorsión evidente. Con SpO₂ = 99 % en modo Low Perfusion, el uMEC 100 mostró una onda periódica y regular, con pulsos equiespaciados, ascenso rápido y descenso lento, sin ruido ni deformaciones apreciables. Respecto a la onda del escenario 1, la amplitud se ve menor, aunque esta diferencia debe tomarse con cautela porque el monitor puede reescalar la onda automáticamente. El monitor mostró SpO₂ = 100 % y generó la alarma “SpO₂ alto > 97”, lo que indica que la señal fue suficiente para calcular la saturación.

**Con SpO₂ = 98 % y 140 bpm, ¿se dispara la alarma de frecuencia cardíaca elevada?**

Sí. Al simular 140 bpm con SpO₂ = 98 %, se activó la alarma de frecuencia cardíaca elevada (140 bpm superó el límite superior configurado) y se activó simultáneamente con la alarma de SpO₂ elevada (el valor de 98 % superó el límite superior de 97 %). En este escenario el monitor mostró FP = 140 bpm y SpO₂ = 99 %. La onda registrada presentó una mayor cantidad de ciclos en la misma ventana de tiempo, coherente con la frecuencia elevada.

> ### Parte C

### 1. Procedimiento General

La verificación se realizó con el monitor de signos vitales Mindray uMEC 100 en modo "monitor" y el simulador óptico de SpO₂ Pronk OxSim OX-1 como fuente de referencia. La pinza de pulsioximetría (sensor de SpO₂) del monitor se conectó al simulador, de manera que el monitor procesó las señales generadas por el OxSim en lugar de las de un paciente. Se simularon cuatro condiciones, cada una correspondiente a un modo predefinido del OX-1 [1], [2]: bradicardia (modo 2: 40 bpm, SpO₂ = 95 %), hipoxia (modo 1: 80 bpm, SpO₂ = 85 %), SpO₂ elevada en modo Low Perfusion (modo 5: 80 bpm, SpO₂ = 99 %, índice de perfusión ≈ 0.2) y taquicardia (modo 4: 140 bpm, SpO₂ = 98 %). En los modos 1 a 4 el índice de perfusión del simulador es ≈ 2.0 [2].

> [!NOTE]
> La guía menciona la configuración del desfibrilador BeneHeart D30 entre los resultados esperados. Este equipo no se utilizó porque el D30 disponible en la universidad no cuenta con medición de SpO₂; toda la práctica se realizó con el uMEC 100, como describe el procedimiento de la Parte B.

Para la verificación de alarmas, los límites de SpO₂ fueron 90 % (inferior) y 100 % (superior) en bradicardia e hipoxia, y 90 % / 97 % en Low Perfusion y taquicardia; los límites de frecuencia de pulso (FP) fueron 50 bpm (inferior) y 110 bpm (superior) en todos los escenarios. En hipoxia y Low Perfusion se esperaron 5 s tras fijar el valor simulado, como indica la guía, para comprobar si la alarma sonora/visual estaba activa. En cada escenario se registró además el tiempo de respuesta, medido a partir del video de la práctica desde el instante en que el monitor se estabilizó en los valores simulados hasta que se emitió la alarma.

Para evaluar la exactitud de las mediciones se calcularon el error absoluto y el error porcentual de la FP y de la SpO₂ en cada escenario, con las ecuaciones definidas en la Parte B. Los resultados se contrastaron con la exactitud declarada por el fabricante para el uMEC 100: ±2 % de SpO₂ (puntos porcentuales) entre 70 % y 100 % para pacientes adultos y pediátricos, y ±3 bpm en la frecuencia de pulso medida desde SpO₂ [3].

La forma de onda fotopletismográfica se registró a partir de capturas del video de la pantalla del monitor en los escenarios de bradicardia, Low Perfusion y taquicardia.

### 2. Resultados Obtenidos

En los cuatro escenarios el monitor generó la alarma correspondiente al límite excedido, sin alarmas adicionales ni omitidas. En bradicardia, la FP simulada de 40 bpm quedó por debajo del límite inferior de 50 bpm y se activó la alarma de FP baja a los 12 s. En hipoxia, la SpO₂ de 85 % quedó por debajo del límite de 90 % y la alarma de SpO₂ baja se activó a los 8 s; al cumplirse los 5 s indicados en la guía aún no estaba activa. En Low Perfusion, la SpO₂ de 99 % superó el límite superior de 97 % y la alarma de SpO₂ alta se activó a los 12 s, también después de los 5 s de verificación. En taquicardia, los 140 bpm superaron el límite de 110 bpm y la SpO₂ de 98 % superó el límite de 97 %, por lo que se activaron de forma simultánea las alarmas de FP alta y SpO₂ alta, a los 10 s.

En cuanto a la exactitud, la FP mostrada por el monitor coincidió con la simulada en los cuatro escenarios (40, 80, 80 y 140 bpm), con error absoluto y porcentual de 0. La SpO₂ coincidió en hipoxia (85 %) y presentó una diferencia de 1 punto en los otros tres escenarios: 96 % frente a 95 % en bradicardia (1.05 %), 100 % frente a 99 % en Low Perfusion (1.01 %) y 99 % frente a 98 % en taquicardia (1.02 %). Todas las diferencias, de 0 bpm en la FP y de 1 punto como máximo en la SpO₂, quedaron dentro de la exactitud declarada por el fabricante para el uMEC 100 [3].

La onda fotopletismográfica fue periódica y regular en los tres escenarios registrados. En bradicardia se observaron pocos ciclos en la ventana visible, con ascenso rápido, descenso lento y amplitud amplia. En Low Perfusion se observaron siete pulsos equiespaciados con la misma morfología y una amplitud menor, coherente con el índice de perfusión de este modo (≈ 0.2 frente a ≈ 2.0 en los demás) [2], sin distorsión ni ruido apreciables. En taquicardia la ventana contuvo muchos más ciclos, con pulsos casi sinusoidales, simétricos y de amplitud constante, sin muesca dicrótica.

### 3. Análisis de Resultados

**Análisis 1: Diferencias entre los valores simulados y los mostrados por el monitor, frente a la exactitud declarada**

Con una medición por escenario (n = 4 por variable), la evaluación se limitó a estadística descriptiva. En la FP, el error absoluto fue 0 bpm en los cuatro escenarios, frente a una exactitud declarada de ±3 bpm [3]. En la SpO₂, el error absoluto fue de 0 a 1 punto, con una media de **0.75 puntos** (desviación estándar muestral de 0.5) y un error porcentual medio de **0.77 %**, con un máximo de 1.05 %. La comparación con la especificación se hizo sobre el error absoluto, porque el fabricante expresa su exactitud en puntos de SpO₂: la diferencia máxima de 1 punto se encuentra dentro de los ±2 puntos declarados para el rango de 70 % a 100 %, que cubre los valores simulados de 85 % a 99 % [3]. El monitor nunca mostró valores por debajo de los simulados: la diferencia siempre fue nula o positiva, de 1 punto. Como la resolución de la SpO₂ del uMEC 100 es de 1 % [3] y los valores del simulador son los nominales de cada modo, una diferencia de 1 punto equivale al paso mínimo de visualización y no puede atribuirse únicamente al monitor.

> [!NOTE]
> La exactitud de SpO₂ declarada por el fabricante se establece según la norma ISO 80601-2-61, que la evalúa frente a la saturación arterial medida en voluntarios sometidos a hipoxia controlada. La comparación con un simulador, con un solo registro por escenario, es una verificación funcional y no sustituye esa evaluación.

**Análisis 2: Relación entre la forma de onda del monitor y la frecuencia de pulso / saturación de oxígeno**

La forma de onda mostró una relación directa con la FP: al aumentar la frecuencia simulada, la cantidad de ciclos contenidos en la misma ventana de tiempo creció, desde pocos ciclos a 40 bpm hasta una señal densa a 140 bpm. Con la SpO₂ no se observó una relación morfológica directa. Entre los escenarios con SpO₂ de 95 % y 99 % la forma del pulso se mantuvo (ascenso rápido y descenso lento), y la diferencia visible en amplitud entre bradicardia (índice de perfusión ≈ 2.0) y Low Perfusion (≈ 0.2) estuvo asociada al índice de perfusión del modo seleccionado [2] y no al valor de saturación. Esto es coherente con el principio de la pulsioximetría, en el que la SpO₂ se calcula a partir de la absorción de luz a dos longitudes de onda y la onda mostrada refleja principalmente el pulso y su amplitud.

> [!NOTE]
> La comparación de amplitud entre bradicardia y Low Perfusion debe tomarse con cautela, porque el monitor puede reescalar la onda de forma automática y la amplitud mostrada no es una medida absoluta de la perfusión.

### 4. Preguntas para la Discusión

**Pregunta 1: ¿Cuál es el principio de operación del Pronk OxSim OX-1 para simular una onda pulsátil?**

El OxSim OX-1 es un simulador óptico de SpO₂: opera a través del propio sensor de la pinza, de modo que la prueba incluye el sensor, la extensión y el monitor completos [2]. Reconoce automáticamente el tipo de sensor conectado, por lo que no requiere indicar el fabricante del oxímetro bajo prueba. Cada modo del simulador fija tres variables: la saturación (85, 95, 98 o 99 %), la frecuencia de pulso (40, 80 o 140 bpm) y el índice de perfusión (≈ 2.0, o ≈ 0.2 en el modo Low Perfusion) [1], [2]. Para el monitor, la señal equivale a la de un dedo con pulso arterial: la componente pulsátil se repite a la frecuencia programada, su amplitud relativa corresponde al índice de perfusión y la saturación calculada corresponde al valor del modo seleccionado. Esto explica que, en las capturas, la onda fuera periódica, simétrica, de amplitud constante y sin muesca dicrótica, características de una señal generada por el simulador y no de un pulso arterial fisiológico.

**Pregunta 2: ¿Por qué la SpO₂ baja puede ser un falso positivo (falsa alarma) en una situación de mala perfusión?**

La SpO₂ se calcula a partir de la componente pulsátil de la señal. Cuando la perfusión periférica es baja, esa componente se vuelve pequeña frente al ruido de la medición (movimiento, luz ambiental, interferencia eléctrica), y la relación entre los canales rojo e infrarrojo se estima con mayor error. En esas condiciones el monitor puede mostrar un valor bajo que no corresponde a la saturación arterial real, y la alarma refleja una limitación de la medición y no una hipoxemia del paciente.

El fabricante diseñó el modo Low Perfusion del OxSim (índice de perfusión ≈ 0.2) como una prueba exigente que no todos los monitores o sensores logran medir [1]. En esta práctica el uMEC 100 mantuvo una señal estable en ese modo, mostró SpO₂ = 100 % y la alarma que se activó (SpO₂ alta) correspondió a un límite realmente superado, por lo que no se reprodujo una falsa alarma.

> [!NOTE]
> El OxSim entrega una señal sin ruido, por lo que el modo Low Perfusion reduce el índice de perfusión, pero no reproduce la degradación de la señal que ocurre con una perfusión deficiente real.

### 5. Conclusiones

La detección oportuna de variaciones peligrosas de la frecuencia de pulso y de la saturación de oxígeno depende de que los monitores de signos vitales emitan alarmas cuando se superan los límites configurados, lo que exige poder recrear esas condiciones de forma controlada y sin un paciente. En esta práctica se empleó el simulador Pronk OxSim OX-1 para verificar el funcionamiento del monitor uMEC 100 en cuatro escenarios (bradicardia, hipoxia, SpO₂ elevada en modo Low Perfusion y taquicardia). El monitor generó en todos los casos la alarma correspondiente al límite excedido, sin alarmas adicionales ni omitidas, con tiempos de respuesta entre 8 y 12 s; mostró la frecuencia de pulso sin diferencia respecto al simulador y la SpO₂ con una diferencia máxima de 1 punto (error porcentual máximo de 1.05 %), valores dentro de la exactitud declarada por el fabricante de ±3 bpm y ±2 % de SpO₂, y la onda fotopletismográfica conservó una morfología regular en los tres escenarios registrados, con más ciclos por ventana a mayor frecuencia y sin distorsión en Low Perfusion. Estos resultados muestran que el uMEC 100 responde de forma coherente con los límites configurados y con los valores simulados, y que el OxSim permite comprobar alarmas y mediciones de manera controlada y rápida, lo que permite emplearlo en verificaciones funcionales de rutina de monitores antes de su uso clínico. Como limitación, la señal del simulador es regular y sin ruido, de modo que no reproduce las condiciones patológicas que degradan la medición en un paciente real, como la mala perfusión con artefactos, y con un registro por escenario la comparación con la exactitud declarada es una verificación funcional y no una evaluación metrológica. Como siguiente paso, sería conveniente repetir cada escenario varias veces para estimar la repetibilidad de los errores y de los tiempos de respuesta, compararlos con el retardo de alarma documentado en el manual del equipo, y complementar la verificación con registros en voluntarios sanos para contrastar el desempeño del monitor con señales fisiológicas reales.

### 6. Referencias

[1] Pronk Technologies, "OxSim SpO2 Simulator Operator's Manual (OX-1)," [En línea]. Disponible en: https://www.pronktech.com/wp-content/uploads/2015/02/501-0603-OX-1-Op-Manual-Rev-O.pdf.

[2] MedWrench, "Pronk Technologies - OX-1 OxSim," [En línea]. Disponible en: https://www.medwrench.com/equipment/3862/pronk-technologies-ox-1-oxsim.

[3] Shenzhen Mindray Bio-Medical Electronics Co., Ltd., "uMEC 100/120/150 Patient Monitor Data Sheet," [En línea]. Disponible en: https://storage.mtender.gov.md/get/02d98f27-11fb-4591-ae5f-e054acfdda95-1778679439594 y https://storage.mtender.gov.md/get/2bd79673-4f1f-48f0-b1d1-44fb22629788-1773411341584.
