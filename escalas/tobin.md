# Índice de Tobin (RSBI · Rapid Shallow Breathing Index)

> 📖 **Fuentes:** Yang KL, Tobin MJ. *A prospective study of indexes predicting the outcome of trials of weaning from mechanical ventilation.* N Engl J Med. 1991;324(21):1441-1447. · Marino PL. *The ICU Book.* 4th ed. Wolters Kluwer.

## Qué mide y para qué sirve

El **índice de Tobin**, también llamado **RSBI** (*Rapid Shallow Breathing Index*), es un criterio de **destete ventilatorio** que cuantifica el **patrón respiratorio espontáneo**. Relaciona la **frecuencia respiratoria** con el **volumen tidal**: un patrón **rápido y superficial** (frecuencia alta con volumen bajo) da un índice elevado y predice **fracaso** del destete; un patrón lento y profundo da un índice bajo y predice **éxito**.

Sirve para:

- **Objetivar la tolerancia** a la prueba de respiración espontánea.
- **Predecir el resultado del destete** y evitar extubaciones fallidas y reintubaciones.
- **Documentar la evolución** del paciente durante el proceso de retirada de la ventilación mecánica.
- **Guiar la decisión** de continuar la prueba, suspenderla o volver al soporte.
- **Comunicar** de forma estandarizada el estado del destete entre turnos.

## Población diana

- **Pacientes adultos en ventilación mecánica** que cumplen los criterios generales para iniciar el destete: causa de la insuficiencia respiratoria resuelta o en mejoría, estabilidad hemodinámica, oxigenación aceptable con FiO₂ no elevada y PEEP baja, sin fiebre ni nuevas complicaciones, con nivel de consciencia adecuado y capacidad de toser.
- Requiere que el paciente tenga **esfuerzo respiratorio espontáneo**.
- **No es aplicable** en ventilación controlada sin esfuerzo, con bloqueo neuromuscular o en pacientes que no toleran la desconexión del ventilador.
- En pacientes con **debilidad muscular adquirida en UCI** el patrón rápido y superficial puede ser persistente; conviene completar con el **MRC Sum Score**.

## Cómo se puntúa

Fórmula que muestra la app (`es_formula_rsbi`):

**RSBI = FR (rpm) / VT (litros)**

| Entrada | Unidad | Cadena en la app |
|---|---|---|
| Frecuencia respiratoria (FR) | resp/min | `es_frecuencia_respiratoria` · sufijo `rpm` |
| Volumen tidal espontáneo (VT) | **mL** (la app lo convierte a litros dividiendo entre 1000) | `es_volumen_tidal_espontaneo` · sufijo `mL` |
| Resultado | resp/min/L | `es_rsbi_fr_vt_litros` (`RSBI (FR / VT en L)`) |

**Condiciones de medida** (`es_medir_respiracion_espontanea`): medir durante **respiración espontánea** (prueba de tubo en T o PSV baja) durante **1 minuto**.

## Cómo explorar cada ítem (técnica)

1. **Preparación.** Comprobar que el paciente cumple los criterios de inicio del destete. Explicar el procedimiento, aspirar secreciones si es necesario, colocar al paciente semisentado y asegurar una monitorización adecuada (SpO₂, ECG, frecuencia respiratoria).
2. **Prueba de respiración espontánea.** Conectar al **tubo en T** o mantener **PSV baja** (según protocolo) durante **1 minuto** de estabilización, sin fugas en el circuito.
3. **Frecuencia respiratoria.** Contar las respiraciones durante **1 minuto completo** (no extrapolar periodos cortos): la FR es el numerador del índice.
4. **Volumen tidal espontáneo.** Medir el VT en **mL** con el ventilador o el neumotacógrafo durante el mismo minuto; la app lo convierte a litros.
5. **Calcular el RSBI** e interpretarlo junto con el resto de criterios clínicos.

**Errores frecuentes:** medir con fugas o con agua en el circuito; contar la FR en periodos de 15-30 segundos y multiplicar; medir durante una fase de agitación, dolor o fiebre; no comprobar la sedación residual; y decidir el destete con un único valor aislado.

## Puntuación total e interpretación

| RSBI | Significado | Cadena en la app | Actuación de enfermería |
|---|---|---|---|
| **< 105** | Éxito probable del destete · probabilidad ≈ 80-90 % | `es_info_exito_probable` · `es_rsbi_under_105_detail` | Continuar/mantener la prueba, vigilar la tolerancia, oxigenación y signos de fatiga, y documentar |
| **105-130** | Zona intermedia · valorar junto al resto de criterios clínicos | `es_info_zona_intermedia` · `es_rsbi_105_130_detail` | Vigilancia estrecha; integrar con consciencia, secreciones, gasometría y hemodinámica; repetir la medición |
| **> 130** | Fracaso probable · alta probabilidad de fracaso del destete | `es_info_fracaso_probable` · `es_rsbi_over_130_detail` | **Suspender la prueba**, volver al soporte y corregir causas (dolor, secreciones, broncoespasmo, sobrecarga, debilidad, ansiedad); comunicar |

Etiquetas de resultado de la app: `es_exito_probable` (ÉXITO PROBABLE), `es_zona_intermedia` (ZONA INTERMEDIA) y `es_fracaso_probable` (FRACASO PROBABLE).

Un **RSBI < 105** apoya la retirada de la ventilación mecánica, pero **no decide por sí solo** el destete. La app recuerda que hay que **integrar el índice con el resto de criterios clínicos** (`es_info_rsbi_descripcion`): nivel de consciencia, abundancia de secreciones y capacidad de toser, gasometría, estabilidad hemodinámica, ausencia de fiebre y de nuevas complicaciones.

## Validez

El índice de Tobin fue descrito y validado por **Yang y Tobin (N Engl J Med 1991)** en **pacientes adultos en ventilación mecánica sometidos a pruebas de destete**. En el estudio original, un **RSBI < 105** mostró una **alta sensibilidad (en torno al 97 %)** y un **elevado valor predictivo negativo (en torno al 95 %)** para el éxito del destete, con una especificidad menor (en torno al 64 %). Es decir, **descarta bien el fracaso cuando es bajo**, pero un valor alto no siempre implica fracaso.

Su gran ventaja es que se mide de forma sencilla, no invasiva y a pie de cama, y su gran limitación es la **variabilidad** según las condiciones de medida y el estado del paciente. Estas cifras proceden del estudio original y de validaciones posteriores, y pueden variar según la población y el protocolo de destete.

## Limitaciones y errores frecuentes

- **Un solo valor no decide el destete** (`es_info_rsbi_descripcion`); deben repetirse las determinaciones y valorar la tendencia.
- El índice puede verse alterado por la **ansiedad, el dolor, la fiebre o la sedación residual**.
- Requiere que el paciente tenga un **esfuerzo respiratorio espontáneo valorable** y que el volumen tidal se mida con precisión (en mL, como pide la app).
- La **especificidad es limitada**: un RSBI 105-130 no contraindica el destete, pero obliga a valorar el conjunto de criterios.
- En pacientes con **debilidad muscular adquirida en UCI** el patrón puede ser rápido y superficial de forma persistente.
- No debe medirse en **ventilación controlada** ni con fugas importantes en el circuito.
- En **pacientes pediátricos** los valores de referencia no son directamente extrapolables.

## Ejemplo práctico resuelto

**Caso.** Mujer de 68 años, en ventilación mecánica por neumonía en resolución, que cumple criterios de destete. Se realiza prueba de tubo en T.

- Tras 1 minuto de estabilización se contabilizan **22 respiraciones/min** y un volumen tidal de **480 mL** (0,48 L).
- **RSBI = 22 / 0,48 = 45,8** → **< 105 → éxito probable**.

**Actuación de enfermería:** mantener la prueba, vigilar la frecuencia respiratoria, la SpO₂, el uso de musculatura accesoria, la sudoración y el nivel de consciencia; documentar el RSBI con la FR y el VT utilizados; y comunicar la buena tolerancia. Si aparecieran signos de fatiga o el RSBI subiera por encima de 105, repetir la medición y comunicarlo para valorar la continuación del destete.

## Relación con otras escalas

- **Glasgow/FOUR y RASS:** el nivel de consciencia es un criterio previo al destete.
- **MRC Sum Score:** la debilidad adquirida en UCI condiciona el patrón respiratorio y el éxito del destete.
- **ROX:** valora la respuesta a la cánula nasal de alto flujo, paso previo o posterior a la ventilación invasiva.
- **Murray (LIS):** cuantifica la gravedad de la lesión pulmonar, que condiciona la duración de la ventilación.
- **VAS (asincronía):** la asincronía puede alterar la medición del patrón respiratorio.

## Registro y comunicación

- Documentar el resultado con **fecha y hora** y el profesional que lo valora.
- Registrar los **datos que alimentan la puntuación** (no solo el total) para poder recalcularla.
- Anotar las **intervenciones realizadas** y la respuesta obtenida.
- Incluir el resultado en el **traspaso entre turnos** y comunicar los cambios relevantes al equipo médico.
- Reevaluar de forma **seriada** y registrar la tendencia.

## Autoevaluación rápida

1. ¿Qué mide y en quién se aplica? → El **patrón respiratorio espontáneo (RSBI)** en el paciente en ventilación mecánica candidato a destete.
2. ¿Cuál es su rango y su punto de corte? → **< 105** éxito probable; **105-130** zona intermedia; **> 130** fracaso probable.
3. ¿Qué hacer ante un resultado de riesgo (> 130)? → **Suspender la prueba**, volver al soporte y corregir las causas.
4. ¿Cuándo se mide? → En **tubo en T o PSV baja**, tras 1 minuto de estabilización.

## Preguntas frecuentes

- **¿Decide por sí solo el destete?** No: debe integrarse con el resto de criterios clínicos.
- **¿En qué unidades se introduce el VT?** En **mL** (la app lo convierte a litros).
- **¿Es válido en ventilación controlada?** No: requiere esfuerzo respiratorio espontáneo.

## Puntos clave

- Mide el **patrón respiratorio espontáneo**: **RSBI = FR / VT (L)**.
- **< 105** éxito probable; **105-130** zona intermedia; **> 130** fracaso probable.
- Se mide en **tubo en T o PSV baja**, tras **1 minuto** de estabilización.
- **Sensibilidad y valor predictivo negativo altos**; especificidad limitada.
- **No decide por sí solo** el destete: integrarlo con el resto de criterios clínicos.
- Si es **> 130**, suspender la prueba y corregir causas.
- Documentar FR y VT medidos, no solo el índice.
- Repetir y valorar la **tendencia**.
