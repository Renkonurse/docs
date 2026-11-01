---
layout: default
title: "Morse Fall Scale (Morse · riesgo de caídas)"
---
# Morse Fall Scale (Morse · riesgo de caídas)

> 📖 **Fuentes:** Morse JM, Morse RM, Tylko SJ. *Development of a scale to identify the fall-prone patient.* Can J Aging. 1989;8(4):366-377. · MSD Manual Professional: https://www.msdmanuals.com/professional

## Qué mide y para qué sirve

La **Morse Fall Scale** es el **estándar mundial** para valorar el **riesgo de caídas** del paciente hospitalizado (`es_desc_morse`). Consta de **6 ítems ponderados** según su peso predictivo; el total va de **0 a 125** (`es_morse_info_summary`, `es_morse_total_value`). Los **puntos de corte son 25 y 45**.

Sirve para:

- **Estratificar el riesgo de caídas** al ingreso y durante la hospitalización.
- **Indicar medidas preventivas** proporcionadas al nivel de riesgo.
- **Identificar los factores modificables** (ayuda para deambular, medicación, dispositivos).
- **Documentar y comunicar** el riesgo entre turnos.
- **Evaluar el efecto** de las intervenciones preventivas.

## Población diana

- **Pacientes adultos hospitalizados**, tanto en planta como en urgencias, rehabilitación y unidades de críticos (cuando el paciente puede deambular o levantarse).
- Es aplicable al **ingreso** y en las **reevaluaciones periódicas** y tras una caída.
- Está validada en múltiples poblaciones y entornos, y es una de las escalas más utilizadas internacionalmente.
- **No está diseñada** para población pediátrica (existen escalas específicas).

## Cómo se puntúa

Se elige **una opción por ítem** y se suman los puntos.

### 1. Caídas previas (últimos 3 meses) (`es_morse_item_previous_falls`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 0 | No | `es_downton_option_no` |
| 25 | Sí | `es_downton_option_yes` |

### 2. Diagnóstico secundario (`es_morse_item_secondary_diagnosis`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 0 | No | `es_downton_option_no` |
| 15 | Sí | `es_downton_option_yes` |

### 3. Ayuda para deambular (`es_morse_item_ambulatory_aid`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 0 | Ninguna / reposo / enfermería | `es_morse_option_none_rest_nursing` |
| 15 | Muletas / bastón / andador | `es_morse_option_crutches_cane_walker` |
| 30 | Se apoya en muebles | `es_morse_option_furniture_support` |

### 4. Vía intravenosa / heparina (`es_morse_item_iv_heparin`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 0 | No | `es_downton_option_no` |
| 20 | Sí | `es_downton_option_yes` |

### 5. Marcha (`es_morse_item_gait`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 0 | Normal / reposo / inmóvil | `es_morse_option_normal_rest_immobile` |
| 10 | Débil | `es_morse_option_weak` |
| 20 | Alterada / encorvada | `es_morse_option_altered_stooped` |

### 6. Estado mental (`es_morse_item_mental_state`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 0 | Orientado / consciente de sus limitaciones | `es_morse_option_oriented_aware_limitations` |
| 15 | Sobreestima sus capacidades / olvida limitaciones | `es_morse_option_overestimates_limitations` |

### Total

| Concepto | Valor |
|---|---|
| Mínimo | 0 |
| Máximo | 125 (25 + 15 + 30 + 20 + 20 + 15) |
| Registro en la app | `TOTAL MORSE` — `%1$d / 125` (`es_morse_total_label`, `es_morse_total_value`) |

## Cómo explorar cada ítem (técnica)

1. **Caídas previas.** Preguntar al paciente y a la familia por caídas en los **últimos 3 meses**, incluidas las no atendidas; revisar la historia clínica. Es el ítem de mayor peso (25 puntos).
2. **Diagnóstico secundario.** Comprobar si el paciente tiene **más de un diagnóstico** médico activo (la comorbilidad se asocia a más caídas).
3. **Ayuda para deambular.** Observar y preguntar qué ayuda utiliza: ninguna o reposo, bastón/andador/muletas, o se apoya en los muebles. El apoyo en muebles es el de mayor riesgo.
4. **Vía intravenosa / heparina.** Comprobar si el paciente tiene **vía venosa o tratamiento con heparina**, factores que aumentan el riesgo.
5. **Marcha.** **Observar al paciente caminar** unos metros: normal, débil (pasos cortos, insegura pero sin apoyo) o alterada/encorvada. No inferirla sin verla.
6. **Estado mental.** Valorar si el paciente es **consciente de sus limitaciones** o las **sobreestima/olvida** (deterioro cognitivo, delirium, negación).

**Errores frecuentes:** no observar la marcha; no preguntar por caídas previas recientes; no revisar la presencia de vía venosa o heparina; y valorar el estado mental sin considerar el delirium.

## Puntuación total e interpretación

| Puntuación | Riesgo | Etiqueta de la app | Actuación de enfermería |
|---|---|---|---|
| **0-24** | Riesgo bajo — cuidados estándar | `es_morse_low_risk_standard_care` (`es_morse_info_low_range`) | Cuidados estándar: orientación, timbre y objetos al alcance, reevaluación periódica |
| **25-44** | Riesgo moderado — precauciones | `es_morse_moderate_risk_precautions` (`es_morse_info_moderate_range`) | **Precauciones**: barandillas, calzado antideslizante, iluminación, ayuda en la deambulación, revisión de la medicación y educación |
| **≥ 45** | Riesgo alto — protocolo de caídas | `es_morse_high_risk_falls_protocol` (`es_morse_info_high_range`) | **Protocolo de caídas**: cama en posición baja, barandillas, acompañamiento, dispositivos de ayuda, vigilancia frecuente, señalización del riesgo y comunicación al equipo |

La enfermera debe registrarlo **al ingreso, en cada turno/cambio de estado y tras una caída**, y anotar las medidas aplicadas. Los ítems de **ayuda para deambular** y **marcha** orientan la movilización segura; el de **vía intravenosa/heparina** recuerda el riesgo añadido de los dispositivos.

## Validez

La Morse Fall Scale fue desarrollada por **Morse, Morse y Tylko (Can J Aging 1989)** para identificar al paciente con propensión a las caídas y es una de las escalas **más utilizadas y validadas internacionalmente**. La literatura muestra de forma consistente una **sensibilidad alta** (identifica bien a los pacientes que caerán) con una **especificidad limitada** (clasifica como riesgo a algunos pacientes que no caerán), por lo que su principal valor es el **elevado valor predictivo negativo**.

Se ha validado en poblaciones médicas, quirúrgicas y de rehabilitación, y en distintas traducciones. No se incluyen cifras concretas de sensibilidad, especificidad o AUC porque varían según la población, el punto de corte y la definición de caída; para el detalle debe consultarse la publicación original y las revisiones.

## Limitaciones y errores frecuentes

- La escala **no incorpora factores ambientales** ni el uso de otros dispositivos (sondas, drenajes, oxígeno) que también aumentan el riesgo.
- El ítem de **estado mental** depende de la valoración subjetiva del paciente (sobreestima/olvida sus limitaciones).
- Puede comportarse de forma distinta en **pacientes con deterioro cognitivo** o en unidades con protocolos de sujeción.
- La **marcha** debe observarse; si el paciente no puede caminar, aplicar el criterio de «normal/reposo/inmóvil».
- Es una escala de **cribado**: no sustituye al juicio clínico ni a la valoración del entorno.
- Puede complementarse con la **escala de Downton** (`downton.md`) si el protocolo de la unidad lo requiere.
- Un valor aislado es menos informativo que la **tendencia** y que la reevaluación tras cambios.

## Ejemplo práctico resuelto

**Caso.** Mujer de 76 años ingresada por neumonía. Refiere una caída en casa hace un mes. Tiene diagnóstico secundario (insuficiencia renal crónica), camina con bastón, tiene una vía venosa periférica, presenta marcha débil y está desorientada en el tiempo, sobreestimando su capacidad para levantarse sola.

| Ítem | Valor | Puntos |
|---|---|---|
| Caídas previas | Sí | 25 |
| Diagnóstico secundario | Sí | 15 |
| Ayuda para deambular | Bastón | 15 |
| Vía intravenosa / heparina | Sí | 20 |
| Marcha | Débil | 10 |
| Estado mental | Sobreestima sus capacidades | 15 |
| **Total** | | **100** |

**Morse = 100 → riesgo alto (≥ 45).**

**Actuación de enfermería:** activar el **protocolo de caídas**: cama en posición baja y frenada, barandillas, timbre y objetos personales al alcance, calzado antideslizante, acompañamiento en la deambulación, vigilancia frecuente, señalización del riesgo en la habitación y educación del paciente y la familia. Revisar la medicación sedante y la necesidad de la vía venosa, y **reevaluar en cada turno y tras cualquier cambio**.

## Relación con otras escalas

- **Downton:** escala alternativa de riesgo de caídas, más sencilla y con listas de comprobación.
- **Barthel:** la dependencia funcional se asocia a más caídas.
- **CFS:** la fragilidad incrementa el riesgo.
- **CAM-ICU y RASS:** el delirium y la sedación aumentan el riesgo de caídas.
- **Braden/EMINA:** comparten factores de riesgo (inmovilidad, deterioro mental).

## Puntos clave

- Valora el **riesgo de caídas** con **6 ítems ponderados**; total **0-125**.
- **0-24** bajo; **25-44** moderado; **≥ 45** alto.
- El ítem de **caídas previas** es el de mayor peso (25 puntos).
- **Observar la marcha** y revisar la ayuda para deambular y la vía venosa.
- **≥ 45** → activar el protocolo de caídas.
- **Sensibilidad alta y especificidad limitada**: útil para descartar riesgo.
- No recoge factores ambientales ni otros dispositivos.
- Reevaluar al ingreso, por turnos y tras una caída.

---

## Evidencia y referencias

- **Morse JM.** *Preventing Patient Falls*. Thousand Oaks: Sage; 1997.
- **Morse JM, et al.** A prospective study of fall risk factors. *Can J Nurs Res* 1989.
- **Oliver D, et al.** Risk factors and risk assessment tools for falls in hospital in-patients: a systematic review. *Age Ageing* 2004.

> La escala identifica riesgo, no predice lesiones. Debe complementarse con una valoración multifactorial y medidas ambientales; reevaluar tras cada caída.

---

## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **Morse Fall Scale** | Riesgo de caídas |
| **Downton** | Alternativa de cribado |
| **Prevención de caídas** | Medidas y entorno |
| **Cuidados de enfermería** | Registro y reevaluación |
