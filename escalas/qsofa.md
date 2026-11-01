---
layout: default
title: "qSOFA (quick Sequential Organ Failure Assessment)"
---
# qSOFA (quick Sequential Organ Failure Assessment)

> 📖 **Fuentes:** Singer M, Deutschman CS, Seymour CW, et al. *The Third International Consensus Definitions for Sepsis and Septic Shock (Sepsis-3).* JAMA. 2016;315(8):801-810. · Prescott HC, et al. *Surviving Sepsis Campaign International Guidelines 2026*. https://doi.org/10.1007/s00134-026-08361-1.

## Qué mide y para qué sirve

El **qSOFA** es una puntuación clínica de **riesgo pronóstico** (`es_qsofa_subtitle`, `es_qsofa_info_description`), no una herramienta de cribado única recomendada para identificar o descartar sepsis. Valora **3 criterios clínicos** —frecuencia respiratoria, estado mental y tensión arterial sistólica— que puntúan **1 punto cada uno**, con un total de **0 a 3**. En sospecha de infección, una puntuación alta identifica mayor riesgo y apoya una evaluación más profunda.

Sirve para:

- **Apoyar la estratificación pronóstica** en personas adultas con sospecha de infección.
- **Aportar información a la valoración**; no usar la puntuación como requisito para activar el protocolo local ni para indicar por sí sola fluidos o antimicrobianos.
- **Priorizar la valoración** y decidir el nivel de vigilancia.
- **Estandarizar la comunicación** de la sospecha de sepsis entre profesionales.

> El qSOFA **no diagnostica sepsis ni debe ser el único instrumento de cribado**. La decisión clínica integra sospecha de infección, disfunción orgánica y el sistema local de detección/respuesta; un resultado bajo no descarta sepsis.

## Población diana

- **Pacientes adultos con sospecha de infección** atendidos **fuera de la UCI**: urgencias, planta de hospitalización, atención prehospitalaria.
- Es aplicable a la mayoría de los adultos, con **precauciones** en pacientes con alteración crónica del estado mental (demencia, ictus previo).
- **No está validado** en **pacientes pediátricos** (existe un criterio específico pediátrico).
- En **UCI**, el qSOFA no sustituye al **SOFA**, que es el criterio de disfunción orgánica.

## Cómo se puntúa

Instrucción de la app (`es_qsofa_mark_criteria_hint`): *marca los criterios presentes. ≥ 2 = alto riesgo*. Cada criterio vale **1 punto**.

| # | Criterio | Detalle en la app | Puntos |
|---|---|---|---|
| 1 | **Frecuencia respiratoria ≥ 22 rpm** (`es_qsofa_resp_rate_le_22`) | Taquipnea (`es_qsofa_tachypnea`) | 1 |
| 2 | **Alteración del estado mental** (`es_qsofa_altered_mental_status`) | Glasgow < 15 (`es_qsofa_glasgow_lt_15`) | 1 |
| 3 | **TAS ≤ 100 mmHg** (`es_qsofa_systolic_bp_le_100`) | Hipotensión (`es_qsofa_hypotension`) | 1 |

### Total

| Concepto | Valor |
|---|---|
| Mínimo | 0 |
| Máximo | 3 (`es_total_qsofa`, `es_qsofa_total_value` = `%1$d / 3`) |
| Puntuación | 1 punto por criterio presente |

## Cómo explorar cada ítem (técnica)

1. **Frecuencia respiratoria.** Contar durante **1 minuto completo**, con el paciente en reposo. El criterio es **≥ 22 rpm**.
2. **Estado mental.** Valorar si existe **alteración respecto al basal**: desorientación, somnolencia, agitación o disminución del nivel de consciencia. En la app se concreta como **Glasgow < 15**. Es imprescindible comparar con el estado previo del paciente.
3. **Tensión arterial sistólica.** Medir con manguito del tamaño adecuado, en reposo y con la técnica correcta; el criterio es **TAS ≤ 100 mmHg**. Confirmar el valor si es limítrofe.

**Errores frecuentes:** medir la FR en periodos cortos; no conocer el estado mental basal (y confundir demencia crónica con alteración aguda); no confirmar la hipotensión con una segunda toma; y usar el qSOFA como diagnóstico, cribado único o condición para activar respuesta.

## Puntuación total e interpretación

| Puntos | Riesgo | Etiqueta de la app | Actuación de enfermería |
|---|---|---|---|
| **0-1** | Bajo riesgo — sin criterios qSOFA | `es_qsofa_interpretation_low_risk` (`es_qsofa_range_0_1_low_risk`) | Vigilancia según protocolo; **no descarta sepsis** si la sospecha clínica es alta |
| **2-3** | **Mayor riesgo de desenlace desfavorable** | `es_qsofa_interpretation_high_risk` (`es_qsofa_range_2_3_high_risk`) | Aumenta la preocupación clínica y requiere valoración/escala según protocolo local; no es diagnóstico ni un umbral obligatorio para activar respuesta. |

La etiqueta intermedia de la app (`es_qsofa_interpretation_intermediate_risk`, «Riesgo intermedio — vigilancia estrecha») se usa cuando hay un único criterio presente.

**qSOFA ≥ 2** puede señalar mayor riesgo en una persona con sospecha de infección, pero su sensibilidad no permite usarlo como cribado único ni como diagnóstico. Un qSOFA de 0-1 tampoco descarta sepsis. Activa la evaluación y el sistema de respuesta ante sospecha clínica o deterioro, conforme al protocolo local, sin esperar a alcanzar una puntuación determinada.

## Validez

El qSOFA fue propuesto en el consenso **Sepsis-3 (Singer et al., JAMA 2016)** a partir del análisis de bases de datos de pacientes con sospecha de infección, y validado en el estudio complementario de **Seymour et al. (JAMA 2016)**, realizado en **pacientes adultos hospitalizados fuera de la UCI**. El qSOFA mostró una **especificidad alta y una sensibilidad limitada** para predecir mortalidad y estancia prolongada: es decir, **identifica bien a los pacientes de alto riesgo, pero muchos pacientes con sepsis no cumplen ≥ 2 criterios al inicio**.

No está recomendado como **herramienta única de cribado** para decidir evaluación o tratamiento fuera de la UCI; aporta información pronóstica y no sustituye al **SOFA** ni al juicio clínico. No se incluyen cifras concretas de sensibilidad, especificidad o AUC porque varían según la población, el contexto y el desenlace; para el detalle deben consultarse los estudios de derivación y validación de Sepsis-3.

## Limitaciones y errores frecuentes

- Es una puntuación de riesgo; **no debe usarse como cribado único ni sustituye al SOFA** ni al diagnóstico clínico (`es_qsofa_info_description`).
- Tiene **baja sensibilidad**: muchos pacientes con sepsis no cumplen ≥ 2 criterios al inicio; **no debe usarse para descartar** la enfermedad.
- La alteración del estado mental debe ser **nueva o atribuible a la infección**; en pacientes con demencia o ictus previo la interpretación es difícil.
- La TAS puede estar artefactada por la técnica de medida; conviene confirmar la hipotensión.
- Los **betabloqueantes** pueden enmascarar la taquicardia y otras respuestas fisiológicas.
- No incorpora **parámetros analíticos** (lactato, leucocitos, creatinina), que son clave en la valoración de la sepsis.
- En **UCI** debe usarse el SOFA para definir la disfunción orgánica.

## Ejemplo práctico resuelto

**Caso.** Varón de 70 años en urgencias por fiebre y tos productiva. Constantes: FR 26 rpm, TAS 95 mmHg, Glasgow 14 (desorientado respecto a su estado basal, en el que estaba orientado).

| Criterio | ¿Presente? |
|---|---|
| FR ≥ 22 rpm | Sí |
| Alteración del estado mental (Glasgow < 15) | Sí |
| TAS ≤ 100 mmHg | Sí |
| **Total** | **3 / 3** |

**qSOFA = 3 → señal de mayor riesgo pronóstico; no confirma sepsis ni sustituye la valoración clínica.**

**Actuación de enfermería:** ante sospecha clínica o deterioro, activar la respuesta local sin esperar al qSOFA. Obtener lactato y hemocultivos cuando estén indicados (sin demorar antimicrobianos), asegurar accesos, iniciar monitorización y tratamientos prescritos según protocolo, valorar el foco y registrar hallazgos y tiempos. El resultado qSOFA aporta contexto, pero no dicta por sí solo fluidos ni antimicrobianos.

## Relación con otras escalas

- **SOFA:** herramienta para cuantificar disfunción orgánica; qSOFA aporta señal pronóstica y no es cribado diagnóstico.
- **NEWS2:** alerta precoz de deterioro global; puede aplicarse simultáneamente.
- **Glasgow:** cuantifica la alteración del estado mental.
- **Killip:** clasifica la gravedad en el IAM; relevante si el foco es cardiaco.
- **NEMS:** la sepsis grave incrementa la carga de cuidados de enfermería.

## Registro y comunicación

- Documentar el resultado con **fecha y hora** y el profesional que lo valora.
- Registrar los **datos que alimentan la puntuación** (no solo el total) para poder recalcularla.
- Anotar las **intervenciones realizadas** y la respuesta obtenida.
- Incluir el resultado en el **traspaso entre turnos** y comunicar los cambios relevantes al equipo médico.
- Reevaluar de forma **seriada** y registrar la tendencia.

## Autoevaluación rápida

1. ¿Qué mide y en quién se aplica? → El **riesgo de sepsis** mediante 3 criterios clínicos, en pacientes con sospecha de infección fuera de la UCI.
2. ¿Cuál es su rango y su punto de corte? → **0-3**; **≥ 2** indica alto riesgo.
3. ¿Qué hacer ante un resultado de riesgo (≥ 2)? → **Activar el protocolo de sepsis**: lactato, hemocultivos, antibiótico precoz y control del foco.

## Puntos clave

- Cribado **rápido de sepsis** con **3 criterios** de **1 punto**; total **0-3**.
- **FR ≥ 22 rpm**, **alteración del estado mental (Glasgow < 15)** y **TAS ≤ 100 mmHg**.
- **≥ 2 puntos = alto riesgo** → activar protocolo de sepsis.
- **Sensibilidad limitada**: un qSOFA bajo **no descarta** sepsis.
- No sustituye al **SOFA** ni al juicio clínico.
- Se aplica **fuera de la UCI**; en UCI usar SOFA.
- La alteración del estado mental debe ser **nueva** respecto al basal.
- Registrar el resultado y **reevaluar con frecuencia**: el deterioro puede ser rápido.

---

## Evidencia y referencias

- **Singer M, et al.** The Third International Consensus Definitions for Sepsis and Septic Shock (Sepsis-3). *JAMA* 2016;315:801-810.
- **Evans L, et al.** Surviving Sepsis Campaign: International Guidelines for Management of Sepsis and Septic Shock 2021. *Intensive Care Med* 2021.
- **Seymour CW, et al.** Assessment of clinical criteria for sepsis. *JAMA* 2016;315:762-774.

> qSOFA es un cribado fuera de la UCI; no descarta sepsis y no debe usarse solo para decidir. La SSC 2021 recomienda no emplearlo como única herramienta de cribado.

---

## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **qSOFA** | Cribado de sepsis |
| **SOFA** | Disfunción orgánica |
| **Código sepsis** | Activación y tratamiento |
| **NEWS2** | Deterioro clínico |
