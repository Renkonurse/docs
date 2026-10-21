# Escala FOUR (Full Outline of UnResponsiveness)

> 📖 **Fuentes:** Wijdicks EFM, Bamlet WR, Maramattom BV, Manno EM, McClelland RL. *Validation of a new coma scale: the FOUR score.* Ann Neurol. 2005;58(4):585-593. · Chulay M, Burns SM. *AACN Essentials of Critical Care Nursing.* McGraw-Hill.

## Qué mide y para qué sirve

La **FOUR Score (Full Outline of UnResponsiveness)** es una escala de coma **alternativa al Glasgow** que valora **cuatro componentes**: apertura ocular, respuesta motora, **reflejos de tronco encefálico** y **patrón respiratorio**. Cada componente puntúa de **0 a 4**, con un total de **0 a 16**.

Sirve para:

- Valorar el **nivel de consciencia en pacientes intubados y/o sedados**, en los que el componente verbal del Glasgow no es valorable.
- **Explorar el tronco encefálico** (reflejos pupilar, corneal y tusígeno) y el **patrón respiratorio**, lo que permite detectar síndromes de enclaustramiento, estados de vigilia sin respuesta y la **progresión rostro-caudal** hacia la muerte encefálica (`es_four_info_advantage`).
- Realizar un **seguimiento seriado** en el paciente neurocrítico, con menos dependencia del lenguaje que el Glasgow.
- **Comunicar** de forma estructurada el estado neurológico entre turnos y unidades.

## Población diana

- **Pacientes críticos adultos** con alteración de la consciencia: traumatismo craneoencefálico, ictus, hemorragia intracraneal, encefalopatía posanóxica, infecciones del sistema nervioso central, coma de cualquier causa.
- Especialmente indicada en **pacientes intubados o con sedación**, donde el Glasgow pierde el componente verbal.
- También útil en **pacientes no intubados** en los que se quiere registrar el patrón respiratorio y los reflejos de tronco.
- **Limitada** en el paciente con **bloqueo neuromuscular** (no puede valorarse la respuesta motora ni la respiración espontánea) y en el paciente con **lesión ocular o facial** que impida explorar reflejos.

## Cómo se puntúa

Se elige **una sola opción por componente** y se suman los cuatro. Cada componente puede puntuar 0, 1, 2, 3 o 4.

### 1. Ojos (E)

| Puntos | Respuesta | Cadena en la app |
|---|---|---|
| 4 | Abre los ojos espontáneamente | `es_four_eyes_open_spontaneously` |
| 3 | Abre los ojos a la orden | `es_four_eyes_open_to_command` |
| 2 | Abre los ojos al dolor | `es_four_eyes_open_to_pain` |
| 1 | No abre los ojos | `es_four_eyes_does_not_open` |
| 0 | No evaluable (edema, ptosis, etc.) | `es_four_eyes_not_testable` |

> Diferencia con Glasgow: aquí **sí existe el 0**, reservado para el ojo **no evaluable**; la ausencia de apertura puntúa 1.

### 2. Motor (M)

| Puntos | Respuesta | Cadena en la app |
|---|---|---|
| 4 | Obedece órdenes / pulgar arriba | `es_four_motor_obeys_thumbs_up` |
| 3 | Localiza el dolor | `es_four_motor_localizes_pain` |
| 2 | Flexión al dolor | `es_four_motor_flexion_to_pain` |
| 1 | Extensión al dolor | `es_four_motor_extension_to_pain` |
| 0 | No responde | `es_four_motor_no_response` |

### 3. Reflejos de tronco (B · brainstem)

| Puntos | Respuesta | Cadena en la app |
|---|---|---|
| 4 | Reflejos pupilar y corneal presentes | `es_four_brainstem_pupillary_corneal_present` |
| 3 | Una pupila fija y dilatada | `es_four_brainstem_one_pupil_fixed_dilated` |
| 2 | Reflejos pupilares o corneal ausentes | `es_four_brainstem_pupils_or_corneal_absent` |
| 1 | Reflejos pupilar y corneal ausentes | `es_four_brainstem_pupils_and_corneal_absent` |
| 0 | Reflejos pupilar, corneal y tusígeno ausentes | `es_four_brainstem_pupils_corneal_cough_absent` |

### 4. Respiración (R)

| Puntos | Respuesta | Cadena en la app |
|---|---|---|
| 4 | No intubado, respiración regular | `es_four_resp_not_intubated_regular` |
| 3 | No intubado, Cheyne-Stokes | `es_four_resp_not_intubated_cheyne_stokes` |
| 2 | No intubado, respiración irregular | `es_four_resp_not_intubated_irregular` |
| 1 | Respira por encima de la frecuencia del ventilador | `es_four_resp_breathing_above_ventilator` |
| 0 | Respira al ritmo del ventilador o apnea | `es_four_resp_breathing_with_ventilator_or_apnea` |

### Total

| Concepto | Valor |
|---|---|
| Mínimo | 0 (0+0+0+0) |
| Máximo | 16 (4+4+4+4) |
| Componentes | 4 (ojos, motor, tronco, respiración) |

La app muestra el total y el desglose por componente (`es_four_subtitle`: «Valora 4 componentes (0-4 cada uno, total 0-16)»).

## Cómo explorar cada ítem (técnica)

**1. Ojos (E).** Observar sin estimular → si no abre, dar una **orden verbal** clara («abra los ojos») → si no responde, aplicar **estímulo doloroso** (presión supraorbitaria o lecho ungueal). Si el ojo no puede explorarse por edema palpebral, ptosis, traumatismo o midriáticos, puntuar **0 (no evaluable)**, que no equivale a «peor respuesta».

**2. Motor (M).** Empezar con órdenes sencillas: «levante el pulgar», «apriéteme la mano», «mire hacia el techo». Si no obedece, aplicar estímulo doloroso y observar si **localiza** el estímulo (3), si hay **flexión** (2, descorticación) o **extensión** (1, descerebración), o si **no hay respuesta** (0).

**3. Reflejos de tronco (B).**

- **Pupilar:** iluminar cada pupila con una linterna y valorar el reflejo fotomotor (tamaño, simetría y reactividad).
- **Corneal:** estimular la córnea con una gasa estéril o suero frío y observar el cierre palpebral.
- **Tusígeno:** estimular la tráquea mediante aspiración o catéter y valorar la tos.
- Puntuar según cuántos reflejos están presentes: ambos (4), una pupila fija y dilatada (3), ausencia de pupilares o corneal (2), ausencia de pupilar y corneal (1), ausencia de pupilar, corneal y tusígeno (0).

**4. Respiración (R).** En el paciente **no intubado**, observar el patrón: regular (4), Cheyne-Stokes (3, ciclos de hiperpnea y apnea), irregular (2). En el paciente **en ventilación mecánica**, valorar si respira **por encima** de la frecuencia del ventilador (1, esfuerzo espontáneo presente) o si **respira al ritmo del ventilador o está en apnea** (0).

**Errores frecuentes:** explorar con el paciente recién sedado o en relajación; no comprobar el tamaño y la reactividad pupilar antes de administrar midriáticos; confundir la respiración del ventilador con respiración espontánea; no registrar qué reflejos se han explorado.

## Puntuación total e interpretación

| Puntuación | Significado | Cadena en la app | Actuación de enfermería |
|---|---|---|---|
| 16 | Normal | `es_four_info_row_16_normal` | Monitorización y reevaluación por turnos |
| 13-15 | Deterioro leve | `es_four_info_row_13_15_mild_impairment` | Vigilar tendencia, registrar desglose por componentes, comunicar cambios |
| 9-12 | Deterioro moderado | `es_four_info_row_9_12_moderate_impairment` | Monitorización estrecha, control de vía aérea, avisar al equipo médico |
| 5-8 | Coma profundo | `es_four_info_row_5_8_deep_coma` | Aviso al intensivista, cuidados neuroprotectores, vigilancia de reflejos y respiración |
| 0-4 | Muerte cerebral probable | `es_four_info_row_0_4_brain_death` | **Comunicación inmediata**; documentar reflejos explorados y condiciones; activar protocolo de valoración de muerte encefálica |

Etiquetas de resultado de la app: `es_four_interp_coma_absent_normal` (coma no presente / normal), `es_four_interp_mild_impairment`, `es_four_interp_moderate_impairment`, `es_four_interp_deep_coma` y `es_four_interp_probable_brain_death`.

## Validez

La FOUR Score fue descrita y validada por Wijdicks et al. (Ann Neurol 2005) en **pacientes críticos con alteración de la consciencia de diversas causas**, incluidos pacientes intubados, en los que el componente verbal del Glasgow no puede valorarse. El estudio original mostró **buena fiabilidad interobservador** y capacidad para reflejar la gravedad neurológica, y estudios posteriores la han validado como alternativa al Glasgow en UCI, con ventaja en la detección de patrones de tronco encefálico y en la predicción de evolución.

No se incluyen aquí cifras concretas de sensibilidad, especificidad o AUC porque varían según la población, el momento de la valoración y el desenlace evaluado. La escala **no sustituye a la exploración neurológica completa** ni al protocolo de muerte encefálica.

## Limitaciones y errores frecuentes

- Requiere explorar **reflejos de tronco** (pupilar, corneal, tusígeno), lo que exige formación y técnica cuidadosa; el reflejo tusígeno puede requerir aspiración.
- El **0 en ojos** significa «no evaluable», no «peor respuesta»; no debe confundirse con el 0 de los demás componentes.
- El **edema palpebral, el traumatismo ocular, la cirugía oftalmológica o los midriáticos** alteran los componentes E y B.
- En **bloqueo neuromuscular** no pueden valorarse la respuesta motora ni la respiración espontánea.
- La sedación profunda puede simular un deterioro de tronco; hay que interpretar la puntuación junto con la dosis de sedantes.
- Registrar **solo el total** oculta qué componente se deteriora; documentar siempre el desglose.
- Un valor aislado es poco informativo: lo relevante es la **tendencia** y la comparación entre exploradores.

## Ejemplo práctico resuelto

**Caso.** Mujer de 71 años, hemorragia subaracnoidea, intubada y con sedación ligera.

- **Ojos:** abre los ojos a la orden verbal → **E3**.
- **Motor:** no obedece órdenes; localiza el estímulo doloroso en la región supraorbitaria → **M3**.
- **Tronco:** reflejos pupilar y corneal presentes, simétricos → **B4**.
- **Respiración:** en ventilación mecánica, presenta esfuerzos espontáneos por encima de la frecuencia programada → **R1**.

**Total: E3 + M3 + B4 + R1 = 11 puntos** → **deterioro moderado (9-12)**.

**Actuación de enfermería:** registrar el desglose y la hora, comprobar la sedación (RASS) para descartar que el deterioro sea farmacológico, vigilar pupilas y patrón respiratorio, mantener cabecero a 30°, controlar la presión de perfusión cerebral según protocolo, avisar al intensivista y repetir la valoración en el siguiente control. La presencia de esfuerzo respiratorio espontáneo (R1) es un dato relevante para el destete y para el ajuste de la sedación.

## Relación con otras escalas

- **Glasgow (GCS):** escala de referencia; la FOUR la complementa en intubados y añade tronco y respiración.
- **RASS:** mide agitación/sedación y es imprescindible para interpretar la FOUR en pacientes sedados.
- **CAM-ICU:** detecta delirium; requiere un nivel de consciencia explorable (RASS).
- **SOFA (SNC):** utiliza el Glasgow, no la FOUR, para su componente neurológico.
- **NEWS2:** la alteración de la consciencia (ACVPU) es uno de sus parámetros de alerta precoz.

## Puntos clave

- Valora **4 componentes** (ojos, motor, tronco, respiración) de **0 a 4** cada uno; total **0-16**.
- Diseñada para el **paciente intubado y/o sedado**, donde el Glasgow pierde el componente verbal.
- **Añade reflejos de tronco y patrón respiratorio**, ausentes en el Glasgow.
- El **0 en ojos** significa **no evaluable**, no ausencia de respuesta.
- **0-4 puntos** obligan a comunicar de inmediato y a valorar el protocolo de muerte encefálica.
- La exploración de reflejos exige **técnica y formación**; documentar qué reflejos se han explorado.
- La sedación y el bloqueo neuromuscular modifican la puntuación.
- Registrar siempre el **desglose por componentes**, no solo el total.
---
## Evidencia y referencias

- **Wijdicks EFM, et al.** Validation of a new coma scale: the FOUR score. *Ann Neurol* 2005;58:585-593.
- **ENLS 6.0.** Neurocritical Care Society, 2024.

> Evalúa respuesta ocular, motora, reflejos de tronco y respiración; es útil en intubados. No sustituye la tendencia del Glasgow ni la exploración neurológica completa.

---
## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **Escala FOUR** | Coma y tronco encefálico |
| **Glasgow** | Comparación y seguimiento |
| **TCE / HIC** | Deterioro neurológico |
| **Vía aérea** | Intubación y protección |
