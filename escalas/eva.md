# EVA · Escala Visual Analógica del dolor (y escala numérica)

> 📖 **Fuentes:** Huskisson EC. *Measurement of pain.* Lancet. 1974;2(7889):1127-1131 (Escala Visual Analógica). · MSD Manual Professional: https://www.msdmanuals.com/professional

## Qué mide y para qué sirve

La **EVA** mide la **intensidad del dolor** que refiere el propio paciente. Es una escala **subjetiva, unidimensional y autoinformada**: el paciente cuantifica su dolor en una línea de **0 (sin dolor)** a **10 (el peor dolor imaginable)**. En la app se presenta como un **deslizador de 0 a 10** (`es_select_pain_level`, `SELECCIONA EL NIVEL DE DOLOR`) con la leyenda `es_scale_legend`: `0 = sin dolor · 10 = peor dolor imaginable`.

Sirve para:

- **Cuantificar la intensidad del dolor** y objetivar su evolución.
- **Guiar la analgesia**: decidir rescates, titular perfusiones y valorar la respuesta al tratamiento.
- **Evaluar la eficacia de las intervenciones** analgésicas y no farmacológicas.
- **Comunicar** el grado de dolor entre turnos y profesionales.
- **Detectar el dolor no controlado**, que es causa frecuente de agitación, delirium, taquicardia e hipertensión.

Requiere que el paciente **pueda comunicarse y comprender la escala**; para el paciente crítico no comunicativo deben usarse escalas observacionales como **CPOT** o **ESCID** (`es_info_note`).

## Población diana

- **Pacientes adultos conscientes y colaboradores**, capaces de comprender y expresar un número o marcar una línea: postoperatorio, traumatismos, dolor torácico, dolor musculoesquelético, dolor oncológico.
- Pacientes con **capacidad cognitiva suficiente**; en deterioro cognitivo leve puede usarse con ayuda, pero pierde fiabilidad.
- **No es válida** en sedación profunda, delirium grave, demencia avanzada, afasia, sordera profunda o barrera idiomática importante.
- En **niños** se emplean versiones adaptadas (caras, colores), no la EVA clásica.

## Cómo se puntúa

| Concepto | Valor |
|---|---|
| Rango | **0 – 10** |
| Tipo de escala | Autoinforme (el paciente indica el número o marca la línea) |
| Registro en la app | `PUNTUACIÓN EVA` (`es_eva_score`) |
| Extremos | 0 = sin dolor · 10 = peor dolor imaginable (`es_scale_legend`) |

La app muestra una etiqueta cualitativa según el valor seleccionado (`es_info_range` recuerda que el rango es «0-10 cm / puntos según versión»).

## Cómo explorar cada ítem (técnica)

La EVA **no tiene ítems**: es una única medida. La técnica consiste en aplicarla siempre igual:

1. **Explicar la escala** antes de pedir la respuesta: «0 significa que no tiene nada de dolor y 10 el peor dolor que pueda imaginar».
2. **Preguntar por el dolor actual** (no el de la mañana ni el de ayer), salvo que se quiera valorar el dolor en reposo y en movimiento por separado.
3. **Dejar que el paciente responda sin influir**: no sugerir números ni relativizar («no puede ser para tanto»).
4. **Registrar el valor, la hora y la situación** (en reposo, al movimiento, tras una cura, tras la analgesia).
5. **Repetir tras cada intervención analgésica**, habitualmente a los **30-60 minutos**, para valorar la respuesta.
6. **Valorar el dolor en reposo y en actividad** cuando proceda (movilización, fisioterapia, curas), ya que el dolor dinámico puede requerir un ajuste distinto.

**Errores frecuentes:** no explicar la escala; preguntar por «el dolor» sin concretar el momento; influir en la respuesta; usar la EVA en pacientes que no pueden comprenderla; y no reevaluar después de la analgesia.

## Puntuación total e interpretación

| Puntuación | Intensidad | Etiqueta de la app | Actuación de enfermería |
|---|---|---|---|
| 0 | Sin dolor | `es_no_pain` (`es_info_no_pain`) | Mantener analgesia pautada si procede; medidas no farmacológicas |
| 1-3 | Dolor leve | `es_cpot_mild_pain` (`es_info_mild_pain`) | Analgesia pautada, medidas no farmacológicas, reevaluar |
| 4-6 | Dolor moderado | `es_moderate_pain` (`es_info_moderate_pain`) | Valorar **rescate analgésico** según prescripción; comunicar si se repite |
| 7-8 | Dolor severo | `es_severe_pain` (`es_info_severe_pain`) | **Rescate y aviso** al equipo médico; reevaluar a los 30 min |
| 9-10 | Dolor insoportable | `es_unbearable_pain` (`es_info_unbearable_pain`) | **Actuación inmediata**: analgesia según protocolo, aviso médico y reevaluación estrecha |

En la selección de cada valor, la app colorea el resultado según el tramo (0-3 verde, 4-6 ámbar, 7-8 naranja, 9-10 rojo).

La EVA es el parámetro que guía la **analgesia multimodal** (paracetamol, AINE según contraindicaciones, opioides) y la titulación de la analgesia en el paciente despierto. Un dolor que no cede o que empeora a pesar del tratamiento obliga a **buscar otras causas** (isquemia, retención, úlcera, complicaciones postoperatorias, síndrome compartimental).

## Validez

La **Escala Visual Analógica** del dolor fue introducida por Huskisson (Lancet 1974) y es una de las medidas de dolor más utilizadas y estudiadas en el paciente adulto que puede comunicarse. Es **válida, fiable y sensible al cambio** en el dolor agudo y crónico, y se considera una referencia frente a la que se comparan otras escalas. Se correlaciona bien con escalas numéricas y verbales.

Su limitación principal no es psicométrica sino de **aplicabilidad**: pierde validez en pacientes que no comprenden la escala (deterioro cognitivo, delirium, barrera idiomática) y sufre un efecto de «regresión a la media» con medidas repetidas. No se incluyen cifras concretas de sensibilidad o especificidad porque la EVA no es una prueba diagnóstica, sino una medida autoinformada de intensidad.

## Limitaciones y errores frecuentes

- Requiere **capacidad de comunicación y comprensión**; no es válida en sedación profunda, delirium grave, demencia avanzada, afasia o barrera idiomática.
- Es una medida **subjetiva**: influyen la ansiedad, el miedo, el contexto y las expectativas.
- El paciente puede **infravalorar o sobrevalorar** el dolor; hay que correlacionarlo con signos objetivos (taquicardia, hipertensión, sudoración, expresión facial).
- **No mide otras dimensiones** del dolor (localización, características, impacto funcional, dolor neuropático); debe completarse con la valoración clínica.
- Puede existir **discrepancia** entre la EVA y las escalas observacionales; en el paciente no comunicativo, usar siempre la observacional.
- En **deterioro cognitivo leve** los resultados deben interpretarse con cautela.

## Ejemplo práctico resuelto

**Caso.** Varón de 45 años, segundo día de postoperatorio de laparotomía. Refiere dolor en la herida quirúrgica, que aumenta al moverse. Se le explica la escala y responde: **EVA 7 en reposo** y **EVA 9 al incorporarse**.

**Interpretación:** dolor **severo-insoportable**, con componente dinámico importante.

**Actuación de enfermería:** administrar el **rescate analgésico** prescrito, avisar al equipo médico por la intensidad, colocar al paciente en una posición cómoda, aplicar medidas no farmacológicas (frío local si procede, apoyo de la herida al toser, movilización asistida), **reevaluar la EVA a los 30 minutos** y registrar el valor inicial, la intervención, la hora y la respuesta. Si a los 30 minutos la EVA sigue ≥ 7, comunicarlo de nuevo para reconsiderar el plan analgésico.

## Relación con otras escalas

- **ESCID y CPOT:** escalas observacionales para el paciente que no puede comunicarse; sustituyen a la EVA en ese contexto.
- **BPS:** otra escala observacional de dolor validada en UCI.
- **CAM-ICU:** el dolor no controlado es causa frecuente de delirium y agitación.
- **RASS:** la agitación puede ser secundaria al dolor; valorar el dolor antes de aumentar la sedación.
- **NEWS2:** el dolor intenso puede elevar la frecuencia cardiaca y la tensión arterial, modificando la puntuación de alerta precoz.

## Registro y comunicación

- Documentar el resultado con **fecha y hora** y el profesional que lo valora.
- Registrar los **datos que alimentan la puntuación** (no solo el total) para poder recalcularla.
- Anotar las **intervenciones realizadas** y la respuesta obtenida.
- Incluir el resultado en el **traspaso entre turnos** y comunicar los cambios relevantes al equipo médico.
- Reevaluar de forma **seriada** y registrar la tendencia.
- Anotar la **situación** de la medición (reposo, movimiento, tras una cura o tras la analgesia).

## Autoevaluación rápida

1. ¿Qué mide y en quién se aplica? → La **intensidad del dolor autoinformada** en el paciente que puede comunicarse.
2. ¿Cuál es su rango y su punto de corte? → **0-10**; 1-3 leve, 4-6 moderado, 7-8 severo, 9-10 insoportable.
3. ¿Qué hacer ante un resultado de riesgo (7-10)? → **Analgesia** según protocolo, aviso al equipo médico y reevaluación estrecha.
4. ¿Cuándo se reevalúa? → A los **30-60 minutos** de cada intervención analgésica.

## Preguntas frecuentes

- **¿Es válida en el paciente sedado o con delirium?** No: usar escalas observacionales (**CPOT** o **ESCID**).
- **¿Es una medida objetiva?** No: es subjetiva y debe correlacionarse con signos objetivos.
- **¿Qué hacer si el dolor no cede?** Buscar otras causas (isquemia, retención, úlcera, complicaciones).

## Puntos clave

- Mide la **intensidad del dolor autoinformada** de **0 a 10**.
- **0** sin dolor; **1-3** leve; **4-6** moderado; **7-8** severo; **9-10** insoportable.
- Explicar siempre la escala de la misma forma y **no influir** en la respuesta.
- **Reevaluar a los 30-60 minutos** tras cada intervención analgésica.
- No es válida en el paciente que no puede comunicarse: usar **ESCID/CPOT**.
- Es subjetiva: correlacionarla con signos objetivos.
- Un dolor que no cede obliga a **buscar otras causas**.
- Registrar el valor, la hora, la situación y la respuesta al tratamiento.
