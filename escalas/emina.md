---
layout: default
title: "EMINA (Escala de valoración del riesgo de úlceras por presión)"
---
# EMINA (Escala de valoración del riesgo de úlceras por presión)

> 📖 **Fuentes:** GNEAUPP (Grupo Nacional para el Estudio y Asesoramiento en Úlceras por Presión y Heridas Crónicas). *Escala EMINA de valoración del riesgo de úlceras por presión.* https://gneaupp.info · Roca-Biosca A, Garcia-Fernandez FP, Chacon-Garcés S, et al. *Validación de las escalas de valoración de riesgo de úlceras por presión EMINA y EVARUCI en pacientes críticos.* Enferm Intensiva. 2015;26(1):15-23. · SEEIUC: https://www.seeiuc.org

## Qué mide y para qué sirve

La **EMINA** es una escala **validada en España** (`es_emina_info_description`, `es_emina_subtitle`) que valora el **riesgo de úlceras por presión (UPP)** mediante **5 factores**: estado mental, movilidad, incontinencia, nutrición y actividad. Cada factor puntúa de **0 a 3**, con un **total de 0 a 15**. **Punto de corte habitual: > 4 indica riesgo** (`es_emina_criteria`, `es_emina_cutoff_note`).

Sirve para:

- **Detectar el riesgo de UPP** en el paciente hospitalizado con un instrumento validado en el entorno español.
- **Graduar el riesgo** e indicar la intensidad de las medidas preventivas.
- **Orientar la intervención** en cada factor alterado.
- **Documentar y comunicar** el riesgo entre turnos.
- **Evaluar la evolución** del riesgo durante el ingreso.

## Población diana

- **Pacientes adultos hospitalizados** con riesgo de UPP, tanto en planta como en unidades de críticos.
- Es aplicable al **ingreso** y en las **reevaluaciones periódicas**.
- Está validada también en **pacientes críticos** (Roca-Biosca et al., Enferm Intensiva 2015).
- **No está diseñada** para población pediátrica.

## Cómo se puntúa

Se elige **una opción por factor** (la app exige completar todos, `es_cj_select_all`) y se suman los puntos.

### 1. Estado mental (`es_factor_mental_state`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 0 | Alerta / orientado | `es_option_alert_oriented` |
| 1 | Somnoliento / confuso | `es_option_drowsy_confused` |
| 2 | Inconsciente / agitado | `es_option_unconscious_agitated` |
| 3 | Coma | `es_coma` |

### 2. Movilidad (`es_factor_mobility`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 0 | Completa | `es_complete` |
| 1 | Ligeramente limitada | `es_cj_mobility_limited` |
| 2 | Limitada | `es_limited` |
| 3 | Inmóvil | `es_cj_mobility_immobile` |

### 3. Incontinencia (`es_factor_incontinence`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 0 | Continente | `es_cj_incont_continent` |
| 1 | Ocasional (orina) | `es_occasional_urine` |
| 2 | Habitual (orina/heces) | `es_regular_urine_stool` |
| 3 | Total | `es_total` |

### 4. Nutrición (`es_factor_nutrition`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 0 | Adecuada | `es_adequate` |
| 1 | Ocasionalmente inadecuada | `es_occasionally_inadequate` |
| 2 | Inadecuada / NPT | `es_inadequate_npt` |
| 3 | Muy deficiente / ayuno | `es_very_poor_fasting` |

### 5. Actividad (`es_factor_activity`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 0 | Deambula | `es_walks` |
| 1 | Deambula con ayuda | `es_walks_with_help` |
| 2 | Sedestación / sillón | `es_sitting_chair` |
| 3 | Encamado | `es_bedridden` |

### Total

| Concepto | Valor |
|---|---|
| Mínimo | 0 |
| Máximo | 15 |
| Registro en la app | `TOTAL EMINA` (`es_total_emina`) |

## Cómo explorar cada ítem (técnica)

1. **Estado mental.** Valorar el nivel de consciencia y la orientación durante la interacción: alerta y orientado (0), somnoliento o confuso (1), inconsciente o agitado (2), coma (3).
2. **Movilidad.** Valorar la capacidad de **cambiar de posición en la cama** de forma autónoma: completa, ligeramente limitada, limitada o inmóvil.
3. **Incontinencia.** Registrar el patrón de continencia: continente, ocasional (orina), habitual (orina y heces) o total.
4. **Nutrición.** Valorar la **ingesta** y su adecuación: adecuada, ocasionalmente inadecuada, inadecuada o con nutrición parenteral, muy deficiente o en ayuno.
5. **Actividad.** Valorar el **nivel de actividad**: deambula, deambula con ayuda, sedestación o encamado.

**Errores frecuentes:** valorar el estado mental sin considerar la sedación; no preguntar por la incontinencia nocturna; estimar la nutrición sin datos; y confundir movilidad (cambio de posición) con actividad (desplazamiento).

## Puntuación total e interpretación

| Puntuación | Riesgo | Etiqueta de la app | Actuación de enfermería |
|---|---|---|---|
| **0** | Sin riesgo | `es_no_risk` | Cuidados habituales; reevaluación periódica |
| **≤ 4** | Sin riesgo / bajo | `es_braden_riesgo_bajo` (`es_dialog_range_0_4`) | Higiene, observación de la piel y movilización |
| **5-7** | Riesgo moderado | `es_cj_risk_moderate` (`es_dialog_range_5_7`) | Cambios posturales programados, superficies de apoyo y cuidado de la humedad |
| **8-10** | Riesgo alto | `es_adiva_high_risk` (`es_dialog_range_8_10`) | Medidas preventivas intensivas; revisar el plan cada turno |
| **> 10** | Riesgo muy alto | `es_braden_riesgo_muy_alto` (`es_dialog_range_over_10`) | Prevención máxima, superficies especiales y vigilancia continua de la piel |

Un total **> 4** indica riesgo de UPP y obliga a instaurar un **plan de prevención**. Debe **reevaluarse cada 24-48 h** (`es_emina_cutoff_note`) y siempre ante cambios clínicos. El factor **nutrición** permite coordinar la valoración con la dietista/unidad de nutrición; el factor **actividad/movilidad** orienta la movilización precoz.

## Validez

La EMINA es una escala **desarrollada y difundida por el GNEAUPP** y **validada en el entorno español**, incluida su **validación en pacientes críticos** junto con la escala EVARUCI (Roca-Biosca et al., Enferm Intensiva 2015). Los estudios muestran propiedades psicométricas adecuadas para identificar el riesgo de UPP y su utilidad en la práctica clínica, con buena aplicabilidad por enfermería.

No se incluyen cifras concretas de sensibilidad, especificidad o AUC porque varían según la población, el punto de corte y la incidencia de UPP. Es una escala **predictiva**, no diagnóstica.

## Limitaciones y errores frecuentes

- Es una escala **propia del ámbito español (GNEAUPP)**, por lo que los puntos de corte no son directamente comparables con otras escalas (Braden, Norton).
- No incluye factores específicos del paciente crítico (vasopresores, dispositivos, ventilación mecánica).
- La valoración del **estado mental** puede verse dificultada por la **sedación**; hay que interpretarla según el nivel de consciencia real.
- La **nutrición** se valora de forma global y puede no reflejar el estado nutricional real.
- **No sustituye a la inspección de la piel** ni a la valoración clínica individual.
- La puntuación puede variar entre valoradores; conviene formación y consenso.

## Ejemplo práctico resuelto

**Caso.** Mujer de 82 años ingresada por neumonía, somnolienta pero despertable, con movilidad limitada, incontinencia urinaria ocasional y ayuno por disnea.

| Factor | Valor | Puntos |
|---|---|---|
| Estado mental | Somnoliento / confuso | 1 |
| Movilidad | Limitada | 2 |
| Incontinencia | Ocasional (orina) | 1 |
| Nutrición | Muy deficiente / ayuno | 3 |
| Actividad | Encamado | 3 |
| **Total** | | **10** |

**EMINA = 10 → riesgo alto (8-10).**

**Actuación de enfermería:** instaurar medidas preventivas intensivas (cambios posturales cada 2 h, superficies de apoyo, protección de prominencias), manejar la incontinencia con absorbentes y protección cutánea, revisar la piel en cada movilización, coordinar con el equipo la **valoración nutricional** y el inicio de soporte, fomentar la movilización progresiva y **reevaluar cada 24 h**.

## Relación con otras escalas

- **Braden:** escala alternativa de riesgo de UPP, de uso internacional.
- **Cubbin & Jackson:** específica del paciente crítico.
- **Barthel:** la dependencia funcional se relaciona con el riesgo de UPP.
- **NUTRIC/mNUTRIC:** el riesgo nutricional agrava el riesgo de UPP.
- **Morse/Downton:** la inmovilidad y el deterioro mental también aumentan el riesgo de caídas.

## Puntos clave

- Valora el **riesgo de UPP** con **5 factores** de **0 a 3**; total **0-15**.
- **Punto de corte: > 4** indica riesgo.
- **≤ 4** bajo; **5-7** moderado; **8-10** alto; **> 10** muy alto.
- Reevaluar **cada 24-48 h** y ante cambios clínicos.
- Es una escala **española (GNEAUPP)**, validada también en pacientes críticos.
- No sustituye a la **inspección de la piel**.
- El factor **nutrición** permite coordinar con la unidad de nutrición.
- Formación y consenso del equipo para reducir la variabilidad.

---

## Evidencia y referencias

- **Roca-Biosca A, et al.** Validación de las escalas de valoración de riesgo de úlceras por presión EMINA y EVARUCI en pacientes críticos. *Enferm Intensiva* 2015;26:15-23.
- **GNEAUPP.** Escala EMINA de valoración del riesgo de úlceras por presión.
- **Pancorbo-Hidalgo PL, et al.** Risk assessment scales for pressure ulcer prevention: a systematic review. *J Adv Nurs* 2006.

> Escala validada en España, con punto de corte > 4. Como toda escala, debe acompañarse de inspección de la piel y de medidas preventivas.

---

## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **EMINA** | Riesgo de UPP |
| **Braden** | Alternativa de uso internacional |
| **Prevención de UPP** | Medidas según riesgo |
| **Cuidados de la piel** | Inspección y registro |
