---
layout: default
title: "Escala de Downton (riesgo de caídas en el paciente hospitalizado)"
---
# Escala de Downton (riesgo de caídas en el paciente hospitalizado)

> 📖 **Fuentes:** Downton JH. *Falls in the elderly.* 1993 (origen del índice de riesgo de caídas de Downton). · Nyberg L, Gustafson Y. *Using the Downton index to predict those prone to falls in stroke rehabilitation.* Stroke. 1996;27(10):1821-1824. · MSD Manual Professional: https://www.msdmanuals.com/professional

## Qué mide y para qué sirve

La **escala de Downton** valora el **riesgo de caídas en el paciente hospitalizado** (`es_downton_subtitle`). Consta de **5 apartados**: caídas previas, medicamentos, déficit sensorial, estado mental y deambulación (`es_downton_info_description`). Los apartados de **medicamentos** y **déficit sensorial** son **listas de comprobación**: cada fármaco o déficit presente **suma 1 punto**. Un resultado **≥ 3 indica riesgo de caídas** y obliga a aplicar medidas preventivas.

Sirve para:

- **Identificar al paciente con riesgo de caídas** al ingreso y durante la hospitalización.
- **Indicar medidas preventivas** proporcionadas al riesgo.
- **Revisar los factores modificables**, especialmente la **medicación**.
- **Documentar y comunicar** el riesgo entre turnos.
- **Evaluar el efecto** de las intervenciones preventivas.

## Población diana

- **Pacientes adultos hospitalizados**, especialmente ancianos, pacientes con deterioro cognitivo, con alteraciones de la marcha o polimedicados.
- Es aplicable en **planta, urgencias y unidades de críticos** (cuando el paciente deambula o puede levantarse).
- Se recomienda valorarlo **al ingreso, tras una caída, tras cambios de medicación y ante cambios del estado clínico** (`es_downton_info_reevaluate`).
- **No está diseñado** para población pediátrica.

## Cómo se puntúa

Instrucción de la app: *selecciona una opción por apartado* (`es_downton_select_one_per_section`); en medicamentos y déficit sensorial pueden marcarse **varias** opciones (`es_downton_select_all_options`).

### 1. Caídas previas (`es_downton_item_previous_falls`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 0 | No | `es_downton_option_no` |
| 1 | Sí | `es_downton_option_yes` |

### 2. Medicamentos (`es_downton_item_medications`) — marcar todos los que tome (1 punto cada uno)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| +1 | Tranquilizantes / sedantes | `es_downton_med_tranquilizers` |
| +1 | Diuréticos | `es_downton_med_diuretics` |
| +1 | Antihipertensivos | `es_downton_med_antihypertensives` |
| +1 | Antiparkinsonianos | `es_downton_med_antiparkinsonian` |
| +1 | Antidepresivos | `es_downton_med_antidepressants` |
| +1 | Otros medicamentos | `es_downton_med_others` |

### 3. Déficit sensorial (`es_downton_item_sensory_deficit`) — marcar todos los presentes (1 punto cada uno)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| +1 | Déficit visual | `es_downton_sens_visual` |
| +1 | Déficit auditivo | `es_downton_sens_auditory` |
| +1 | Déficit en extremidades | `es_downton_sens_limbs` |

### 4. Estado mental (`es_downton_item_mental_state`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 0 | Orientado | `es_downton_option_oriented` |
| 1 | Confuso | `es_downton_option_confused` |

### 5. Deambulación (`es_downton_item_gait`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 0 | Normal | `es_downton_option_normal` |
| 1 | Segura con ayuda | `es_downton_option_safe_with_help` |
| 1 | Insegura | `es_downton_option_unsafe` |

### Total

| Concepto | Valor |
|---|---|
| Mínimo | 0 |
| Máximo teórico | 12 (caídas previas 1 + hasta 6 fármacos + hasta 3 déficits + estado mental 1 + deambulación 1) |
| Registro en la app | `TOTAL DOWNTON` — `%1$d / 11` (`es_downton_total_label`, `es_downton_total_value`) |

> La app rotula el total como «/ 11» y en su panel informativo indica «Puntuación total: 0 – 6» (`es_downton_info_total_score`); ambas cifras proceden de versiones clásicas con apartados excluyentes, mientras que la pantalla suma los 5 apartados y admite varios fármacos y déficits a la vez. Lo relevante para la interpretación es el **punto de corte en 3**.

## Cómo explorar cada ítem (técnica)

1. **Caídas previas.** Preguntar al paciente y a la familia por **caídas en los últimos meses**, sus circunstancias y consecuencias; revisar la historia clínica.
2. **Medicamentos.** Revisar la **lista completa de fármacos** (incluidos los de venta libre) y marcar los grupos con efecto sobre el riesgo de caídas: sedantes, diuréticos, antihipertensivos, antiparkinsonianos, antidepresivos y otros.
3. **Déficit sensorial.** Valorar la **visión** (gafas, cataratas, agudeza), la **audición** (audífono, hipoacusia) y el **déficit en extremidades** (amputación, neuropatía, paresia).
4. **Estado mental.** Valorar la **orientación** y la presencia de **confusión** (delirium, demencia); registrar si es un cambio agudo.
5. **Deambulación.** **Observar la marcha** (si es posible, con el paciente levantándose y caminando unos metros) y clasificarla: normal, segura con ayuda o insegura. Valorar el uso de bastón, andador o silla.

**Errores frecuentes:** no revisar la medicación completa; valorar la deambulación sin observar al paciente; no tener en cuenta el déficit visual o auditivo corregido; y no reevaluar tras un cambio de fármacos o tras una caída.

## Puntuación total e interpretación

La pantalla de resultados de la app aplica **un único punto de corte en 3**:

| Puntuación | Resultado en la app | Actuación de enfermería |
|---|---|---|
| **0-2** | `SIN RIESGO` (`es_downton_no_risk`) | No requiere medidas específicas. Reevaluar periódicamente (`es_downton_no_risk_recommendation`) |
| **≥ 3** | `RIESGO ALTO` (`es_downton_high_risk`) | Medidas preventivas estrictas: cama en posición baja, barandillas, acompañamiento en la deambulación, timbre accesible, revisar medicación (`es_downton_high_risk_recommendation`) |

El panel informativo de la app detalla además los tramos `es_downton_info_no_risk_range` (0-2 → sin riesgo), `es_downton_info_moderate_range` (3-4 → riesgo moderado) y `es_downton_info_high_range` (≥ 5 → riesgo alto); el resultado de la pantalla principal agrupa 3-4 y ≥ 5 como **RIESGO ALTO**.

Un resultado **≥ 3** obliga a aplicar el **protocolo de prevención de caídas** de la unidad. La enfermera debe **revisar la medicación** del apartado 2 y comentar con el equipo médico la posibilidad de ajustarla, ya que es un factor modificable. Las medidas deben **registrarse** y explicarse al paciente y a la familia.

## Validez

El índice de Downton fue descrito por **Downton JH (1993)** y validado en el ámbito de la **rehabilitación y de los pacientes ancianos**; el estudio de **Nyberg y Gustafson (Stroke 1996)** lo validó en pacientes en **rehabilitación tras ictus**, mostrando su utilidad para predecir las caídas. Es una escala **sencilla, rápida y muy utilizada** en el entorno hospitalario.

Su principal limitación psicométrica es la **especificidad limitada** (clasifica como riesgo a pacientes que no caerán), derivada de la suma no ponderada de fármacos y déficits. No se incluyen cifras concretas de sensibilidad, especificidad o AUC porque varían según la población y el punto de corte; para el detalle debe consultarse la publicación original y las validaciones posteriores.

## Limitaciones y errores frecuentes

- Es una escala **clásica y sencilla**, pero con **menor capacidad predictiva** que escalas más completas como la **Morse Fall Scale** (`morse.md`).
- La suma de varios fármacos o déficits puede **inflar la puntuación** y clasificar como alto riesgo a pacientes con bajo riesgo real (la escala no pondera la importancia de cada factor).
- No recoge factores del entorno (obstáculos, iluminación) ni el uso de dispositivos (sueros, sondas, drenajes) que también favorecen las caídas.
- La **deambulación** debe observarse, no inferirse.
- Los textos del panel de la app (**«/ 11»** y **«0-6»**) no coinciden con la suma real de la pantalla; interpretar con el **corte en 3**.
- Debe complementarse con la **valoración clínica y del entorno** y con la educación del paciente y la familia.

## Ejemplo práctico resuelto

**Caso.** Varón de 80 años ingresado por descompensación de insuficiencia cardiaca. Refiere una caída en casa el mes pasado. Toma furosemida, enalapril y lorazepam. Tiene cataratas no operadas (déficit visual) y camina con andador, con marcha insegura. Está orientado.

| Apartado | Valor | Puntos |
|---|---|---|
| Caídas previas | Sí | 1 |
| Medicamentos | Furosemida + enalapril + lorazepam | 3 |
| Déficit sensorial | Visual | 1 |
| Estado mental | Orientado | 0 |
| Deambulación | Insegura | 1 |
| **Total** | | **6** |

**Downton = 6 → ≥ 3 → RIESGO ALTO.**

**Actuación de enfermería:** aplicar el protocolo de prevención (cama en posición baja, barandillas, timbre y objetos al alcance, calzado antideslizante, iluminación adecuada, acompañamiento en la deambulación), **revisar la medicación** con el equipo médico (sedante y diurético), asegurar las gafas, señalizar el riesgo y educar al paciente y a la familia. Registrar las medidas y reevaluar tras cualquier cambio.

## Relación con otras escalas

- **Morse Fall Scale:** escala de riesgo de caídas más completa y con ítems ponderados.
- **Barthel:** la dependencia funcional aumenta el riesgo de caídas.
- **CFS:** la fragilidad se asocia a mayor riesgo de caídas.
- **CAM-ICU / RASS:** el delirium y la sedación incrementan el riesgo.
- **Braden/EMINA:** comparten factores de riesgo (inmovilidad, deterioro mental).

## Puntos clave

- Valora el **riesgo de caídas** con **5 apartados**; medicamentos y déficit sensorial son **listas de comprobación**.
- **Corte en 3**: **≥ 3 = riesgo alto** y obliga a medidas preventivas.
- Reevaluar **al ingreso, tras caída, cambio de medicación o cambio clínico**.
- La **revisión de la medicación** es un factor modificable clave.
- No pondera la importancia de cada factor: puede **sobreestimar** el riesgo.
- No recoge factores del **entorno** ni los dispositivos.
- Observar la **deambulación** en lugar de inferirla.
- Complementar con la valoración clínica y del entorno.

---

## Evidencia y referencias

- **Downton JH.** *Falls in the elderly*. London: Edward Arnold; 1993.
- **Oliver D, et al.** Risk factors and risk assessment tools for falls in hospital in-patients: a systematic review. *Age Ageing* 2004.
- **NICE.** Falls in older people: assessment after a fall and preventing further falls. 2013 (actualización).

> La escala tiene una precisión moderada; no sustituye la valoración multifactorial ni las medidas ambientales. Reevaluar tras cada caída y al cambiar de unidad.

---

## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **Escala de Downton** | Riesgo de caídas |
| **Morse Fall Scale** | Alternativa de cribado |
| **Prevención de caídas** | Medidas y entorno |
| **Cuidados de enfermería** | Registro y reevaluación |
