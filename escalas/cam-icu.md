# CAM-ICU (Confusion Assessment Method for the ICU)

> 📖 **Fuentes:** Ely EW, Inouye SK, Bernard GR, et al. *Delirium in mechanically ventilated patients: validity and reliability of the Confusion Assessment Method for the Intensive Care Unit (CAM-ICU).* JAMA. 2001;286(21):2703-2710. · Devlin JW, Skrobik Y, Gélinas C, et al. *Clinical Practice Guidelines for the Prevention and Management of Pain, Agitation/Sedation, Delirium, Immobility, and Sleep Disruption in Adult Patients in the ICU (PADIS).* Crit Care Med. 2018;46(9):e825-e873. · Chulay M, Burns SM. *AACN Essentials of Critical Care Nursing.* McGraw-Hill.

## Qué mide y para qué sirve

El **CAM-ICU (Confusion Assessment Method for the Intensive Care Unit)** es el instrumento de referencia para **detectar delirium en el paciente crítico**, incluido el paciente en ventilación mecánica que no puede comunicarse verbalmente. El delirium es un **síndrome cerebral agudo, fluctuante y con alteración de la atención**, que se asocia a mayor mortalidad, estancia prolongada y deterioro cognitivo a largo plazo (`es_info_prognosis`).

Sirve para:

- **Detectar delirium hipoactivo, hiperactivo y mixto.** El hipoactivo es el más frecuente y el que peor pronóstico tiene, y pasa desapercibido si no se aplica un algoritmo sistemático.
- **Monitorizar la evolución** del estado mental a lo largo del ingreso y evaluar la respuesta a las intervenciones.
- **Guiar el manejo**: corregir factores precipitantes, aplicar medidas no farmacológicas y valorar tratamiento farmacológico según protocolo.
- **Estandarizar la comunicación** entre enfermería y medicina sobre el estado cognitivo del paciente.

No es una escala de puntos: es un **algoritmo secuencial de 4 pasos** que se detiene en el primer paso que no cumple criterio. La app lo presenta como un asistente paso a paso (`es_algorithm_4_steps`) que finalmente muestra `DELIRIUM PRESENTE` o `NO DELIRIUM`.

## Población diana

- **Pacientes adultos críticos** ingresados en UCI, con o sin ventilación mecánica.
- Requiere un **nivel de consciencia explorable**: no es aplicable con **RASS −4 o −5** (paciente no despertable) ni con **bloqueo neuromuscular**.
- No es aplicable en pacientes con **sordera profunda, afasia grave o barrera idiomática importante**, ni en pacientes con **deterioro cognitivo avanzado** en los que no puede establecerse el estado basal.
- Debe aplicarse **cada turno** en todo paciente crítico y siempre ante cambios del estado mental.

## Cómo se puntúa (algoritmo de 4 pasos)

El algoritmo **se detiene en el primer paso que no cumple criterio** (`es_info_stops_at_first_failure`).

### Paso 1 · Cambio agudo o fluctuación (`es_step1_title`)

- ¿Hay evidencia de **cambio agudo del estado mental** respecto al basal? (`es_step1_acute_change_question`)
- ¿Ha **fluctuado** el estado mental en las últimas 24 h? (`es_step1_fluctuation_question`)

| Resultado | Consecuencia | Cadena en la app |
|---|---|---|
| No cumple (sin cambio ni fluctuación) | **NO delirium**, fin del algoritmo | `es_step1_no_criteria` |

### Paso 2 · Inatención — letras SAVEAHAART (`es_step2_title`)

Instrucciones (`es_step2_instructions`): *lea las letras en voz alta (una por segundo); el paciente debe apretar la mano cuando oiga la letra «A»*. Se cuentan los errores: apretar cuando no toca + no apretar cuando toca (`es_step2_errors_hint`).

| Criterio | Puntos | Cadena en la app |
|---|---|---|
| **≥ 3 errores** | Inatención presente (paso superado) | `es_step2_threshold` |
| < 3 errores | **NO delirium**, fin del algoritmo | `es_step2_no_delirium` |

El contador de errores de la app admite valores de 0 a 10 y se confirma con `es_confirm_step2` (`Confirmar paso 2`).

### Paso 3 · Nivel de consciencia (RASS) (`es_step3_title`)

Se valora el **RASS actual** del paciente (`es_step3_prompt`).

| Criterio | Consecuencia | Cadena en la app |
|---|---|---|
| **RASS ≠ 0** | **DELIRIUM presente** (fin del algoritmo) | `es_step3_rass_not_zero` |
| RASS = 0 | Se continúa al paso 4 | — |

La app ofrece las 10 opciones de RASS (`es_rass_plus4_combative` … `es_rass_minus5_unresponsive`).

### Paso 4 · Pensamiento desorganizado (`es_step4_title`)

Solo se aplica si RASS = 0. Consta de **4 preguntas** (`es_step4_questions_header`) y **2 comandos** (`es_step4_commands_header`):

**4 preguntas (respuesta correcta entre paréntesis):**

| Nº | Pregunta | Respuesta correcta |
|---|---|---|
| 1 | ¿Puede flotar una piedra en el agua? | No (`es_step4_question1`) |
| 2 | ¿Existen peces en el mar? | Sí (`es_step4_question2`) |
| 3 | ¿Pesa 1 kg más que 2 kg? | No (`es_step4_question3`) |
| 4 | ¿Se puede usar un martillo para clavar un clavo? | Sí (`es_step4_question4`) |

**2 comandos:**

| Comando | Instrucción | Cadena en la app |
|---|---|---|
| A | «Levante estos dedos» (mostrar 2 dedos) | `es_step4_command_a` |
| B | «Ahora con la otra mano» (o «Añada otro dedo»), sin mostrar de nuevo | `es_step4_command_b` |

| Criterio | Resultado | Cadena en la app |
|---|---|---|
| **≥ 2 errores** | Pensamiento desorganizado → **DELIRIUM** | `es_step4_threshold` |
| < 2 errores | **NO delirium** | `es_result_no_delirium` |

El contador de errores de la app admite valores de 0 a 6 y se confirma con `es_confirm_step4` (`Confirmar paso 4`).

## Cómo explorar cada ítem (técnica)

**Preparación.** Comprobar primero el **RASS**. Con RASS −4 o −5 el paciente no es explorable: no aplicar el CAM-ICU y reevaluar más tarde. Presentarse, asegurar que el paciente oye (audífono si lo precisa) y que no hay barrera idiomática manifiesta.

**Paso 1.** Preguntar a la familia o consultar la historia clínica sobre el **estado mental basal** y compararlo con el actual; revisar el registro de las últimas 24 h para detectar fluctuaciones (somnolencia y agitación alternantes, desorientación intermitente).

**Paso 2 (inatención).** Leer la secuencia **SAVEAHAART** a un ritmo de una letra por segundo, con voz clara y sin enfatizar la «A». El paciente debe **apretar la mano** del explorador cada vez que oiga la «A». Se considera error tanto apretar cuando no corresponde como no apretar cuando corresponde. Alternativa válida en pacientes que no pueden apretar la mano: prueba de imágenes (10 imágenes, 5 repetidas). Contar y registrar el número total de errores (0-10).

**Paso 3 (nivel de consciencia).** Aplicar la **RASS** con su secuencia habitual (observar → voz → estímulo físico). Si la RASS es distinta de 0, el paciente cumple criterio de delirium y **no es necesario continuar**.

**Paso 4 (pensamiento desorganizado).** Solo si RASS = 0. Realizar las 4 preguntas (respuesta sí/no) y los 2 comandos. En los comandos, mostrar 2 dedos y pedir «levante estos dedos»; después pedir «ahora con la otra mano» **sin volver a mostrar** los dedos. Contar el total de errores (0-6); el corte es **≥ 2 errores**.

**Errores frecuentes:** explorar con el paciente recién sedado o en RASS −4/−5; no verificar el estado basal; leer las letras demasiado rápido o enfatizando la «A»; ayudar al paciente en los comandos; no registrar el número de errores; y confundir la falta de colaboración por dolor o disnea con inatención.

## Puntuación total e interpretación

| Resultado en la app | Etiqueta | Actuación de enfermería |
|---|---|---|
| Positivo | `DELIRIUM PRESENTE` (`es_result_delirium`) | `es_result_delirium_advice`: documentar y comunicar al equipo médico; valorar causas precipitantes (infección, dolor, fármacos, hipoxia, trastornos metabólicos); aplicar medidas no farmacológicas; garantizar seguridad |
| Negativo | `NO DELIRIUM` (`es_result_no_delirium`) | `es_result_no_delirium_advice`: reevaluar según protocolo; en pacientes de riesgo, al menos cada turno |

Resumen del algoritmo (como lo muestra la app):

- Paso 1 sin cambio ni fluctuación → **NO delirium** (`es_info_bullet_step1`).
- Paso 2 con < 3 errores → **NO delirium** (`es_info_bullet_step2`).
- Paso 3 con RASS ≠ 0 → **DELIRIUM** (`es_info_bullet_step3`).
- Paso 4 con ≥ 2 errores → **DELIRIUM** (`es_info_bullet_step4`).

Ante un CAM-ICU positivo: tratar la **causa** (dolor, infección, hipoxia, retención urinaria, fármacos, alteraciones metabólicas), aplicar medidas no farmacológicas (orientación, ciclo sueño-vigilia, movilización precoz, presencia de la familia, gafas y audífonos) y, si procede, tratamiento farmacológico según protocolo (haloperidol con vigilancia del QT; dexmedetomidina como alternativa). El botón `es_restart` (REINICIAR) permite repetir la valoración completa.

## Validez

El CAM-ICU fue validado por Ely et al. (JAMA 2001) en **pacientes críticos, incluidos pacientes en ventilación mecánica que no podían comunicarse verbalmente**. En la validación original mostró una **alta sensibilidad (en torno al 93-100 %) y una alta especificidad (en torno al 98-100 %)** frente al diagnóstico de referencia de un psiquiatra, con buena fiabilidad interobservador. Es la herramienta **recomendada por las guías PADIS 2018** para la detección del delirium en UCI y está validada en múltiples idiomas, incluido el español.

Estas cifras proceden del estudio original y de validaciones posteriores; pueden variar según la prevalencia de delirium, el tipo de UCI y la formación de los exploradores.

## Limitaciones y errores frecuentes

- No es aplicable en **sordera, afasia o barrera idiomática** importantes, ni en pacientes con **sedación profunda (RASS −4/−5)** o **bloqueo neuromuscular**.
- La prueba de letras exige que el paciente **oiga y comprenda** la instrucción y pueda apretar la mano; en caso contrario, usar la prueba de imágenes.
- Un resultado negativo **no descarta delirium** si el paciente estaba profundamente sedado en el momento de la valoración; hay que repetir la exploración.
- El delirium **hipoactivo** se confunde con sedación, depresión o fatiga: solo se detecta aplicando el algoritmo de forma sistemática.
- La exploración debe hacerse en un entorno lo más tranquilo posible, con el paciente despierto, y siempre con el mismo tipo de estímulo.
- El CAM-ICU **detecta** el delirium, pero no graduúa su gravedad; para ello puede usarse el **CAM-ICU-7**.
- Requiere **formación** del equipo; la falta de familiaridad con la prueba de letras reduce su fiabilidad.

## Ejemplo práctico resuelto

**Caso.** Mujer de 78 años, neumonía grave, en ventilación mecánica, sedación suspendida por la mañana. RASS actual: 0 (alerta y calmada).

- **Paso 1:** la familia refiere que en su domicilio estaba orientada y autónoma; en el turno anterior estuvo somnolienta y ahora está despierta y algo desorientada → **cambio agudo y fluctuación: sí**.
- **Paso 2:** prueba de letras SAVEAHAART: aprieta la mano en 2 letras que no son «A» y no aprieta en una «A» → **3 errores** → inatención presente.
- **Paso 3:** RASS = 0 → se continúa al paso 4.
- **Paso 4:** responde correctamente a las 4 preguntas, pero en los comandos levanta los dedos de una mano y no realiza el segundo comando → **1 error** (< 2).

**Resultado: NO DELIRIUM.**

**Actuación de enfermería:** registrar el resultado y los errores de cada paso, mantener las medidas de orientación y el ciclo sueño-vigilia, movilización precoz, control del dolor y de la oxigenación, y **repetir el CAM-ICU en el siguiente turno** (la paciente tiene factores de riesgo: edad, infección, ventilación mecánica y fluctuación previa).

## Relación con otras escalas

- **RASS:** es el paso 3 del algoritmo y condiciona la aplicabilidad del CAM-ICU.
- **CAM-ICU-7:** escala derivada que graduúa la gravedad del delirium a partir de los mismos dominios.
- **Glasgow y FOUR:** valoran el nivel de consciencia, pero no detectan delirium.
- **CPOT y ESCID:** el dolor no tratado es una causa frecuente de agitación y delirium.
- **SOFA y NEWS2:** la disfunción neurológica y el deterioro clínico global se relacionan con el delirium.

## Puntos clave

- Detecta **delirium** en el paciente crítico, incluso en ventilación mecánica.
- Es un **algoritmo de 4 pasos** que se detiene en el primer fallo.
- Paso 1: **cambio agudo o fluctuación**; paso 2: **inatención** (≥ 3 errores); paso 3: **RASS ≠ 0**; paso 4: **pensamiento desorganizado** (≥ 2 errores).
- Requiere **RASS explorable** (no −4/−5) y ausencia de bloqueo neuromuscular.
- Alta **sensibilidad y especificidad** en la validación original; recomendado por PADIS.
- El delirium **hipoactivo** es el más frecuente y el más infradiagnosticado.
- Aplicarlo **cada turno** y siempre ante cambios del estado mental.
- Ante un resultado positivo: **buscar y tratar la causa** y aplicar medidas no farmacológicas.
