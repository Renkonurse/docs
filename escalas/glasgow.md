# Escala de Glasgow (GCS · Glasgow Coma Scale)

> 📖 **Fuentes:** Teasdale G, Jennett B. *Assessment of coma and impaired consciousness: a practical scale.* Lancet. 1974;2(7872):81-84. · Chulay M, Burns SM. *AACN Essentials of Critical Care Nursing.* McGraw-Hill.

## Qué mide y para qué sirve

La **Escala de Glasgow (GCS)** cuantifica el **nivel de consciencia** a partir de tres respuestas independientes: **apertura ocular (O)**, **respuesta verbal (V)** y **respuesta motora (M)**. No mide la gravedad de una lesión concreta, sino el **grado de afectación funcional del encéfalo** en el momento de la exploración.

Sirve para:

- **Detectar y cuantificar el deterioro neurológico** de forma seriada y reproducible.
- **Decidir la protección de la vía aérea**: el umbral clásico de intubación es **GCS ≤ 8**.
- **Estratificar la gravedad** del traumatismo craneoencefálico (leve, moderado, grave) y orientar el destino del paciente (planta, UCI, quirófano).
- **Comunicar** el estado neurológico entre turnos, profesionales y unidades con un lenguaje común.
- **Alimentar otras escalas**: el componente de consciencia del **SOFA (SNC)** y la valoración **ACVPU del NEWS2** se relacionan directamente con el Glasgow.

La puntuación se compone del **total (3-15)** y del **desglose O + V + M** (`es_gcs_components_summary`, formato `O%1$d · V%2$d · M%3$d`). El desglose es imprescindible: dos pacientes con un total de 8 pueden tener perfiles neurológicos y pronósticos muy distintos.

## Población diana

- **Adultos** con cualquier causa de alteración de la consciencia: traumatismo craneoencefálico, ictus isquémico o hemorrágico, hemorragia subaracnoidea, encefalopatía metabólica o infecciosa, coma posanóxico, intoxicaciones, estatus epiléptico.
- **Pacientes neurocríticos** en UCI (monitorización seriada) y **pacientes no neurológicos** en los que se quiere objetivar el nivel de consciencia.
- **Niños mayores** (existe una versión pediátrica específica para lactantes y preescolares).
- **No es aplicable** de forma fiable en el paciente con **sedación profunda, bloqueo neuromuscular o relajación muscular**, ni en el paciente intubado sin registrar la limitación del componente verbal.

## Cómo se puntúa

Se aplica el estímulo necesario y se anota la **mejor respuesta** en cada uno de los tres componentes. El total es la **suma O + V + M**.

### 👁️ Apertura ocular (O) — 1 a 4 puntos

| Puntos | Respuesta | Cadena en la app |
|---|---|---|
| 4 | Espontánea | `es_gcs_eye_spontaneous` |
| 3 | A la voz | `es_gcs_eye_to_voice` |
| 2 | Al dolor | `es_gcs_eye_to_pain` |
| 1 | Ninguna | `es_none_feminine` |

### 🗣️ Respuesta verbal (V) — 1 a 5 puntos

| Puntos | Respuesta | Cadena en la app |
|---|---|---|
| 5 | Orientada | `es_gcs_verbal_oriented` |
| 4 | Confusa | `es_gcs_verbal_confused` |
| 3 | Palabras inapropiadas | `es_gcs_verbal_inappropriate_words` |
| 2 | Sonidos incomprensibles | `es_gcs_verbal_incomprehensible_sounds` |
| 1 | Ninguna | `es_none_feminine` |

### 💪 Respuesta motora (M) — 1 a 6 puntos

| Puntos | Respuesta | Cadena en la app |
|---|---|---|
| 6 | Obedece órdenes | `es_gcs_motor_obeys_commands` |
| 5 | Localiza el dolor | `es_four_motor_localizes_pain` |
| 4 | Retira al dolor | `es_gcs_motor_withdraws_from_pain` |
| 3 | Flexión anormal | `es_gcs_motor_abnormal_flexion` |
| 2 | Extensión anormal | `es_gcs_motor_abnormal_extension` |
| 1 | Ninguna | `es_none_feminine` |

### Total

| Concepto | Valor |
|---|---|
| Mínimo posible | 3 (O1 + V1 + M1) |
| Máximo posible | 15 (O4 + V5 + M6) |
| Registro en la app | `TOTAL GLASGOW` (`es_gcs_total_glasgow`) + resumen O · V · M |

## Cómo explorar cada ítem (técnica)

**Preparación.** Paciente en decúbito supino, cabeza centrada, sin estímulos dolorosos recientes ni sedación/analgesia administradas en los minutos previos. Explorar siempre en el mismo orden y con el mismo tipo de estímulo para poder comparar entre turnos.

**1. Apertura ocular (O).** Primero **observar** al paciente sin intervenir. Si no abre los ojos, **llamarle por su nombre** en tono normal y pedirle que abra los ojos. Si no responde, aplicar un **estímulo doloroso** (presión sobre el lecho ungueal, sobre el trapecio o presión supraorbitaria) y observar la apertura. Errores típicos: puntuar 3 cuando el paciente solo abre los ojos tras el dolor (debe ser 2) o confundir la apertura refleja con la voluntaria.

**2. Respuesta verbal (V).** Iniciar con una **conversación espontánea**: preguntar nombre, lugar, fecha y motivo de ingreso. Si el paciente habla, valorar el **contenido**: orientado (5), confuso pero conversa (4), palabras sueltas o inapropiadas sin conversación (3), solo sonidos/gemidos (2), ninguna respuesta (1). No se debe inducir la respuesta ni corregir al paciente antes de puntuar.

**3. Respuesta motora (M).** Empezar con una **orden sencilla** («apriéteme la mano», «levante el pulgar», «mire hacia el techo»). Si no obedece, aplicar **estímulo doloroso** y observar: **localiza** (5, lleva la mano al punto de estímulo), **retira** (4, flexión rápida de retirada), **flexión anormal** (3, descorticación: flexión lenta de brazos y extensión de piernas), **extensión anormal** (2, descerebración: extensión y pronación de brazos, extensión de piernas), **ninguna** (1).

**Regla de oro:** puntuar la **mejor respuesta obtenida** en cada componente y **registrar los tres por separado** además del total (`es_gcs_note_record_components`). En el paciente intubado, registrar la limitación del componente verbal como 'V1' o 'Vt' (`es_gcs_limitation_intubated_patient`).

## Puntuación total e interpretación

| Puntuación | Gravedad | Cadena en la app | Actuación de enfermería |
|---|---|---|---|
| 15 | Normal | `es_gcs_bullet_15_normal` | Monitorización habitual y reevaluación por turnos |
| 13-14 | Leve | `es_gcs_bullet_13_14_mild` | Vigilar tendencia, registrar O+V+M, comunicar cualquier descenso ≥ 2 puntos |
| 9-12 | Moderado | `es_gcs_bullet_9_12_moderate` | Monitorización estrecha, control de vía aérea, avisar al equipo médico, registrar por turnos |
| ≤ 8 | Grave (**indicación de intubación**) | `es_gcs_bullet_8_severe_intubation` | **Aviso inmediato** al intensivista; preparar material de vía aérea; posición lateral de seguridad si procede; registrar hora y estímulos |

Las etiquetas de clasificación de la app son `es_gcs_mild` (leve), `es_gcs_moderate` (moderado) y `es_gcs_severe` (grave).

Un **descenso ≥ 2 puntos** respecto a la valoración previa es un **signo de alarma neurológica** y obliga a comunicarlo de inmediato aunque el total siga siendo alto.

## Validez

La GCS fue descrita por Teasdale y Jennett en 1974 y es la escala de consciencia más utilizada y estudiada del mundo. Está validada en **traumatismo craneoencefálico, ictus y coma de diversa etiología** en adultos y niños, y se correlaciona con la mortalidad y con el pronóstico funcional a largo plazo.

Su **fiabilidad interobservador** es moderada-buena para el total y algo menor para el componente verbal; la **respuesta motora es el componente más reproducible y con mayor valor pronóstico** (`es_gcs_limitation_motor_most_predictive`). El principal factor de variabilidad es la técnica de estimulación (voz frente a dolor) y el momento de la valoración respecto a la sedación. No se incluyen aquí cifras concretas de sensibilidad, especificidad o AUC porque varían mucho según la población y el punto de corte, y deben consultarse en el estudio original.

## Limitaciones y errores frecuentes

- **Paciente intubado:** la respuesta verbal no es valorable → registrar 'V1' o 'Vt' (`es_gcs_limitation_intubated_patient`); no inventar una puntuación verbal.
- **Paciente sedado:** interpretar con cautela, ya que la sedación deprime la puntuación (`es_gcs_limitation_sedated_patient`).
- **Afasia o barrera idiomática:** pueden infravalorar la puntuación (`es_gcs_limitation_aphasia_language_barrier`).
- **Estímulo inadecuado:** usar siempre el mismo estímulo; la presión supraorbitaria y la del lecho ungueal inducen respuestas distintas.
- **Confundir retirada con flexión anormal** o puntuar la apertura ocular refleja como respuesta a la voz.
- **Registrar solo el total:** dificulta la comparación y oculta el deterioro de un componente.
- **Olvidar el efecto de la sedación, la analgesia y el bloqueo neuromuscular** en la valoración seriada.
- Un único valor tiene poca información: lo relevante es la **tendencia**.

## Ejemplo práctico resuelto

**Caso.** Varón de 54 años, traumatismo craneoencefálico grave tras accidente de tráfico, intubado y con sedoanalgesia en perfusión.

- **Ojos:** no abre los ojos ni espontáneamente ni a la voz; abre al estímulo doloroso → **O2**.
- **Verbal:** portador de tubo endotraqueal, no valorable → **V1 (Vt)**.
- **Motora:** no obedece órdenes; al estímulo doloroso retira el brazo de forma rápida → **M4**.

**Total: O2 + V1 + M4 = 7 puntos** → **GCS grave (≤ 8)**, con indicación de protección de la vía aérea (ya intubado).

**Actuación de enfermería:** registrar el desglose O2-Vt-M4 y la hora, comprobar fijación y permeabilidad del tubo, mantener cabecero a 30°, vigilar reflejos pupilares y signos de hipertensión intracraneal, avisar al intensivista y repetir la valoración en el siguiente control. Dado que el componente verbal no es valorable, complementar con la **FOUR Score**, que explora tronco y respiración.

## Relación con otras escalas

- **FOUR Score:** alternativa en intubados; añade reflejos de tronco y patrón respiratorio y también puntúa el ojo no evaluable.
- **RASS:** mide agitación/sedación; es más adecuada cuando el paciente está sedado y permite aplicar el CAM-ICU.
- **CAM-ICU:** usa el nivel de consciencia (RASS) como paso 3; no usa el Glasgow.
- **SOFA (SNC):** el componente neurológico del SOFA se puntúa con el Glasgow (15 → 0 puntos; < 6 → 4 puntos).
- **qSOFA y NEWS2:** la «alteración del estado mental» (Glasgow < 15 en qSOFA; ACVPU en NEWS2) forma parte de sus criterios de gravedad.

## Puntos clave

- Mide **nivel de consciencia** en tres componentes: O, V y M; el total va de **3 a 15**.
- Registrar **siempre O + V + M por separado**, no solo el total.
- **GCS ≤ 8** es el umbral clásico de **protección de la vía aérea**.
- Un **descenso ≥ 2 puntos** es un signo de alarma y debe comunicarse.
- La **respuesta motora** es el componente más reproducible y con mayor valor pronóstico.
- En intubados, el componente verbal se registra como **V1/Vt**; valorar cambiar a **FOUR**.
- La sedación, la analgesia y el bloqueo neuromuscular falsean la puntuación.
- Lo importante es la **evolución seriada**, no un valor aislado.
- La app muestra el total con el desglose y permite enviar el resultado a Monitorización.
