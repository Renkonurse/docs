---
layout: default
title: "SOFA (Sequential Organ Failure Assessment)"
---
# SOFA (Sequential Organ Failure Assessment)

> 📖 **Fuentes:** Vincent JL, Moreno R, Takala J, et al. *The SOFA (Sepsis-related Organ Failure Assessment) score to describe organ dysfunction/failure.* Intensive Care Med. 1996;22(7):707-710. · Singer M, Deutschman CS, Seymour CW, et al. *The Third International Consensus Definitions for Sepsis and Septic Shock (Sepsis-3).* JAMA. 2016;315(8):801-810. · Marino PL. *The ICU Book.* 4th ed. Wolters Kluwer.

## Qué mide y para qué sirve

El **SOFA** cuantifica la **disfunción de 6 sistemas orgánicos** —respiratorio, coagulación, hepático, cardiovascular, sistema nervioso central y renal— (`es_sofa_info_description`). Cada sistema se puntúa de **0 a 4** según el grado de deterioro, con un **total de 0 a 24**. Se usa en los **criterios de sepsis (Sepsis-3)** y para valorar la **evolución del paciente crítico**.

Sirve para:

- **Identificar la disfunción orgánica** asociada a la sepsis (criterio de Sepsis-3).
- **Cuantificar la gravedad** del paciente crítico y seguir su evolución.
- **Evaluar la respuesta al tratamiento** y detectar el deterioro o la mejoría.
- **Estratificar el pronóstico** de forma orientativa.
- **Estandarizar la comunicación** del estado del paciente entre turnos y unidades.

## Población diana

- **Pacientes adultos críticos** ingresados en UCI, con o sin infección.
- **Pacientes con sospecha de infección** en los que hay que valorar disfunción orgánica (Sepsis-3).
- Requiere **analítica** (gasometría, plaquetas, bilirrubina, creatinina) y **parámetros hemodinámicos y ventilatorios**.
- **No es una herramienta de cribado** a pie de cama. Para identificar deterioro se debe usar el sistema validado localmente (p. ej., NEWS2 u otro); qSOFA puede aportar información pronóstica, pero no debe ser el cribado único.
- No está diseñado para **población pediátrica** (existe el pSOFA) ni para pacientes no críticos.

## Cómo se puntúa

Instrucción de la app (`es_sofa_prompt`): *selecciona la puntuación de cada sistema (0 – 4)*. La app pide todas las puntuaciones (`es_sofa_select_all_scores`) y muestra el progreso (`es_sofa_progress`).

### Respiratorio (`es_sofa_system_respiratory`)

| Puntos | Criterio | Cadena en la app |
|---|---|---|
| 0 | PaO₂/FiO₂ ≥ 400 | `es_sofa_resp_pf_ge_400` |
| 1 | PaO₂/FiO₂ < 400 | `es_sofa_resp_pf_lt_400` |
| 2 | PaO₂/FiO₂ < 300 | `es_sofa_resp_pf_lt_300` |
| 3 | PaO₂/FiO₂ < 200 con soporte respiratorio | `es_sofa_resp_pf_lt_200_support` |
| 4 | PaO₂/FiO₂ < 100 con soporte respiratorio | `es_sofa_resp_pf_lt_100_support` |

### Coagulación (`es_sofa_system_coagulation`)

| Puntos | Plaquetas (×10³/µL) | Cadena en la app |
|---|---|---|
| 0 | ≥ 150 | `es_sofa_coag_platelets_ge_150` |
| 1 | < 150 | `es_sofa_coag_platelets_lt_150` |
| 2 | < 100 | `es_sofa_coag_platelets_lt_100` |
| 3 | < 50 | `es_sofa_coag_platelets_lt_50` |
| 4 | < 20 | `es_sofa_coag_platelets_lt_20` |

### Hepático (`es_sofa_system_hepatic`)

| Puntos | Bilirrubina (mg/dL) | Cadena en la app |
|---|---|---|
| 0 | < 1,2 | `es_sofa_hepatic_bilirubin_lt_1_2` |
| 1 | 1,2 – 1,9 | `es_sofa_hepatic_bilirubin_1_2_1_9` |
| 2 | 2,0 – 5,9 | `es_sofa_hepatic_bilirubin_2_0_5_9` |
| 3 | 6,0 – 11,9 | `es_sofa_hepatic_bilirubin_6_0_11_9` |
| 4 | > 12,0 | `es_sofa_hepatic_bilirubin_gt_12_0` |

### Cardiovascular (`es_sofa_system_cardiovascular`)

| Puntos | Criterio | Cadena en la app |
|---|---|---|
| 0 | PAM ≥ 70 mmHg | `es_sofa_cv_map_ge_70` |
| 1 | PAM < 70 mmHg | `es_sofa_cv_map_lt_70` |
| 2 | Dopamina ≤ 5 o dobutamina (cualquier dosis) | `es_sofa_cv_dopamine_le_5_or_dobutamine` |
| 3 | Dopamina > 5, epinefrina ≤ 0,1 o norepinefrina ≤ 0,1 | `es_sofa_cv_dopamine_gt_5_epi_le_0_1_or_norepi_le_0_1` |
| 4 | Dopamina > 15, epinefrina > 0,1 o norepinefrina > 0,1 | `es_sofa_cv_dopamine_gt_15_epi_gt_0_1_or_norepi_gt_0_1` |

> Dosis de catecolaminas en µg/kg/min.

### Sistema nervioso central · SNC (`es_sofa_system_cns`)

| Puntos | Glasgow | Cadena en la app |
|---|---|---|
| 0 | 15 | `es_sofa_cns_glasgow_15` |
| 1 | 13 – 14 | `es_sofa_cns_glasgow_13_14` |
| 2 | 10 – 12 | `es_sofa_cns_glasgow_10_12` |
| 3 | 6 – 9 | `es_sofa_cns_glasgow_6_9` |
| 4 | < 6 | `es_sofa_cns_glasgow_lt_6` |

### Renal (`es_sofa_system_renal`)

| Puntos | Creatinina (mg/dL) / diuresis | Cadena en la app |
|---|---|---|
| 0 | < 1,2 | `es_sofa_renal_creatinine_lt_1_2` |
| 1 | 1,2 – 1,9 | `es_sofa_renal_creatinine_1_2_1_9` |
| 2 | 2,0 – 3,4 | `es_sofa_renal_creatinine_2_0_3_4` |
| 3 | 3,5 – 4,9 o diuresis < 500 mL/d | `es_sofa_renal_creatinine_3_5_4_9_or_urine_lt_500` |
| 4 | > 5,0 o diuresis < 200 mL/d | `es_sofa_renal_creatinine_gt_5_0_or_urine_lt_200` |

### Total

| Concepto | Valor |
|---|---|
| Sistemas | 6 × (0-4 puntos) |
| Mínimo | 0 |
| Máximo | 24 (`es_total_sofa`, `es_sofa_total_value` = `%1$d / 24`) |

## Cómo explorar cada ítem (técnica)

1. **Respiratorio.** Obtener **gasometría arterial** con la FiO₂ del momento y calcular la **PaO₂/FiO₂**; registrar si el paciente recibe **soporte respiratorio** (ventilación invasiva o no invasiva, CNAF) porque condiciona los puntos 3 y 4.
2. **Coagulación.** Solicitar **plaquetas** en el hemograma; usar el valor más bajo del día si hay varias determinaciones.
3. **Hepático.** Solicitar **bilirrubina total**; en pacientes con ictericia u obstrucción biliar es imprescindible.
4. **Cardiovascular.** Medir la **PAM** (o calcularla: (TAS + 2 × TAD)/3) y registrar las **dosis de vasoactivos en µg/kg/min** (dopamina, dobutamina, epinefrina, norepinefrina) en el momento de la valoración.
5. **SNC.** Valorar el **Glasgow** con la técnica habitual (mejor respuesta O+V+M).
6. **Renal.** Registrar la **creatinina** y la **diuresis de 24 h** (o por horas, si se dispone); usar el criterio más grave de los dos.

**Errores frecuentes:** calcular la PaO₂/FiO₂ con una FiO₂ distinta a la del momento de la gasometría; no registrar las dosis de vasoactivos; usar la creatinina sin considerar la diuresis (o viceversa); y valorar el Glasgow en pacientes sedados sin tenerlo en cuenta (la sedación sobreestima la disfunción neurológica).

## Puntuación total e interpretación

| Total | Disfunción | Etiqueta / mortalidad (app) | Actuación de enfermería |
|---|---|---|---|
| 0-6 | Leve | `es_sofa_dysfunction_mild` · `es_sofa_mortality_lt_10` (mortalidad estimada < 10 %) | Monitorización y cuidados según el sistema afectado; reevaluar cada 24 h |
| 7-9 | Moderada | `es_sofa_dysfunction_moderate` · `es_sofa_mortality_15_20` (≈ 15-20 %) | Vigilancia estrecha, optimizar el soporte orgánico, comunicar al equipo |
| 10-12 | Grave | `es_sofa_dysfunction_severe` · `es_sofa_mortality_40_50` (≈ 40-50 %) | Cuidados intensivos, revisión del foco y del tratamiento, vigilancia continua |
| ≥ 13 | Muy grave | `es_sofa_dysfunction_very_severe` · `es_sofa_mortality_gt_80` (> 80 %) | Máximo soporte; valorar con el equipo los objetivos terapéuticos; comunicación con la familia |

**SOFA ≥ 2** en un paciente con infección sospechada es criterio de **disfunción orgánica** asociada a sepsis (Sepsis-3); un **aumento ≥ 2 puntos** respecto al basal orienta a disfunción orgánica aguda (`es_sofa_info_recommendation`). Se recomienda calcularlo **al ingreso y cada 24 h**: la **evolución del SOFA** es más informativa que un valor aislado.

## Validez

El SOFA fue desarrollado por **Vincent et al. (Intensive Care Med 1996)** a partir de un consenso de expertos y validado en una **amplia cohorte multicéntrica de pacientes críticos**, donde mostró una **relación graduada entre la puntuación y la mortalidad**. En **Sepsis-3 (Singer et al., JAMA 2016)**, un **aumento del SOFA ≥ 2 puntos** en pacientes con sospecha de infección se asoció a un riesgo de mortalidad intrahospitalaria **en torno al 10 %**, y el SOFA se consolidó como el criterio de disfunción orgánica para definir la sepsis.

Es una de las escalas de gravedad más utilizadas en UCI y se ha validado en múltiples poblaciones y contextos. No se incluyen cifras concretas de sensibilidad, especificidad o AUC porque el SOFA no es una prueba diagnóstica, sino una medida de disfunción orgánica; las cifras de mortalidad de la tabla son **orientativas** y proceden de series clásicas.

## Limitaciones y errores frecuentes

- No es una escala de **cribado** a pie de cama: requiere analítica y parámetros que no siempre están disponibles de inmediato. Usa el sistema local de alerta y respuesta; qSOFA no es un sustituto de cribado validado (`qsofa.md`).
- Puede verse alterado por **tratamientos instaurados** (vasoactivos, ventilación, diálisis) que modifican la puntuación sin cambiar la fisiología de base.
- En pacientes con **insuficiencia hepática o renal crónica** los valores basales pueden estar alterados y sobreestimar la disfunción aguda.
- En pacientes **sedados o con bloqueo neuromuscular** el componente neurológico (Glasgow) sobreestima la disfunción.
- Es un **predictor poblacional**, no individual: no debe usarse solo para decisiones de limitación terapéutica.
- La puntuación debe calcularse con los **peores valores del día** de forma homogénea; mezclar momentos distintos introduce error.
- No sustituye a la valoración clínica global ni a los criterios de **Killip** o **TIMI** en el SCA.

## Ejemplo práctico resuelto

**Caso.** Varón de 67 años con shock séptico de origen abdominal, en ventilación mecánica con FiO₂ 0,50 y PEEP 10.

| Sistema | Dato | Puntos |
|---|---|---|
| Respiratorio | PaO₂ 75 mmHg / FiO₂ 0,50 = 150 con soporte | 3 |
| Coagulación | Plaquetas 90 ×10³/µL | 2 |
| Hepático | Bilirrubina 2,4 mg/dL | 2 |
| Cardiovascular | Norepinefrina 0,08 µg/kg/min | 3 |
| SNC | Glasgow 12 | 2 |
| Renal | Creatinina 2,1 mg/dL | 2 |
| **Total** | | **14** |

**SOFA = 14 → disfunción muy grave (≥ 13)**, con mortalidad estimada orientativa > 80 %.

**Actuación de enfermería:** registrar el SOFA con el desglose y la hora, asegurar el soporte orgánico (ventilación protectora, vasoactivos, fluidoterapia, control del foco), vigilar la perfusión y la diuresis, administrar el antibiótico precoz según protocolo, controlar el dolor y la sedación, y **comunicar al equipo**. Dada la gravedad, revisar conjuntamente los objetivos terapéuticos y la información a la familia. Repetir el SOFA cada 24 h para valorar la respuesta.

## Relación con otras escalas

- **qSOFA:** puntuación de riesgo pronóstico; no es cribado diagnóstico ni sustituye al SOFA.
- **Glasgow y FOUR:** fuente del componente neurológico del SOFA.
- **Murray (LIS):** cuantifica específicamente la lesión pulmonar.
- **Killip y TIMI:** escalas específicas del síndrome coronario agudo.
- **NEMS:** mide la carga de trabajo de enfermería, complementaria a la gravedad.

## Puntos clave

- Cuantifica la **disfunción de 6 sistemas orgánicos**; total **0-24**.
- **SOFA ≥ 2** con infección sospechada = **disfunción orgánica** (Sepsis-3).
- Un **aumento ≥ 2 puntos** respecto al basal indica disfunción aguda.
- Calcular **al ingreso y cada 24 h**; la evolución importa más que el valor aislado.
- Requiere **analítica y parámetros hemodinámicos/ventilatorios**; no es cribado a pie de cama.
- La **sedación** sobreestima el componente neurológico.
- Los tratamientos instaurados (vasoactivos, diálisis, ventilación) modifican la puntuación.
- Es un **predictor poblacional**, no una herramienta individual de decisión.

---

## Evidencia y referencias

- **Vincent JL, et al.** The SOFA (Sepsis-related Organ Failure Assessment) score to describe organ dysfunction/failure. *Intensive Care Med* 1996;22:707-710.
- **Singer M, et al.** The Third International Consensus Definitions for Sepsis and Septic Shock (Sepsis-3). *JAMA* 2016;315:801-810.
- **Evans L, et al.** Surviving Sepsis Campaign 2021. *Intensive Care Med* 2021.

> SOFA describe disfunción orgánica; no es una herramienta de triaje ni de decisión aislada. Se asume una puntuación basal de 0 si no hay datos previos, lo que puede sobreestimar el cambio.

---

## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **SOFA** | Disfunción orgánica |
| **qSOFA** | Cribado de sepsis |
| **Código sepsis** | Activación y tratamiento |
| **Gasometría / hemodinámica** | Datos para el cálculo |
