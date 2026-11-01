---
layout: default
title: "Escala de Cubbin \u0026 Jackson (riesgo de UPP en el paciente crítico)"
---
# Escala de Cubbin & Jackson (riesgo de UPP en el paciente crítico)

> 📖 **Fuentes:** Cubbin B, Jackson C. *Trial of a pressure area risk calculator for intensive therapy patients.* Intensive Care Nurs. 1991;7(1):40-44. · Chulay M, Burns SM. *AACN Essentials of Critical Care Nursing.* McGraw-Hill.

## Qué mide y para qué sirve

La **escala de Cubbin & Jackson** es una escala de **riesgo de úlceras por presión específica del paciente crítico (UCI)** (`es_cj_subtitle`, `es_cj_info_description`). Valora **10 ítems** —edad, peso, estado de la piel, estado mental, movilidad, hemodinámica, respiración, nutrición, incontinencia e higiene/movilización en cama—, cada uno con **4 niveles que puntúan de 1 a 4**. El total va de **10 a 40** (`es_cj_total_value` = `%1$d / 40`). La escala está construida de forma que **a mayor puntuación, menor riesgo** (los valores 4 corresponden a la situación de menor riesgo y los valores 1 a la de mayor riesgo).

Sirve para:

- **Identificar el riesgo de UPP en el paciente crítico**, incluyendo factores propios de la UCI.
- **Graduar ese riesgo** e indicar la intensidad de las medidas preventivas.
- **Orientar la intervención** en cada ítem alterado.
- **Documentar y comunicar** el riesgo entre turnos.
- **Evaluar la evolución** del riesgo durante el ingreso en UCI.

## Población diana

- **Pacientes adultos críticos** ingresados en UCI, especialmente los que presentan inestabilidad hemodinámica, ventilación mecánica o inmovilidad.
- Es aplicable al **ingreso** y en las **reevaluaciones periódicas** (habitualmente cada 24-48 h).
- **No es una escala pediátrica**: está diseñada para el **adulto crítico**.
- En pacientes de planta puede usarse **Braden** o **EMINA**; la Cubbin & Jackson aporta factores específicos de UCI.

## Cómo se puntúa

Se elige **una opción por ítem** (el valor más bajo = peor situación). La app muestra los 10 ítems con sus opciones (`itemsCJ`).

| # | Ítem (app) | Puntos 4 | Puntos 3 | Puntos 2 | Puntos 1 |
|---|---|---|---|---|---|
| 1 | **Edad** (`es_cj_item_1_age`) | < 40 años (`es_cj_age_4`) | 40-55 años (`es_cj_age_3`) | 56-70 años (`es_cj_age_2`) | > 70 años (`es_cj_age_1`) |
| 2 | **Peso** (`es_cj_item_2_weight`) | Peso normal (`es_cj_weight_4`) | Obeso (`es_cj_weight_3`) | Caquéctico (`es_cj_weight_2`) | Cualquier peso + edema (`es_cj_weight_1`) |
| 3 | **Estado de la piel** (`es_cj_item_3_skin`) | Piel intacta (`es_cj_skin_4`) | Enrojecimiento / eritema (`es_cj_skin_3`) | Excoriación / rozadura (`es_cj_skin_2`) | Necrosis / exudado (`es_cj_skin_1`) |
| 4 | **Estado mental** (`es_cj_item_4_mental`) | Alerta (`es_cj_mental_4`) | Apático / confuso (`es_cj_mental_3`) | Semicomatoso (`es_cj_mental_2`) | Comatoso (`es_cj_mental_1`) |
| 5 | **Movilidad** (`es_cj_item_5_mobility`) | Movilidad completa (`es_cj_mobility_4`) | Limitación leve (`es_cj_mobility_3`) | Muy limitada (silla) (`es_cj_mobility_2`) | Inmóvil (cama) (`es_cj_mobility_1`) |
| 6 | **Hemodinámica** (`es_cj_item_6_hemodynamics`) | Estable sin soporte inotrópico (`es_cj_hemo_4`) | Estable con reposición de volumen (`es_cj_hemo_3`) | Inestable con soporte inotrópico (`es_cj_hemo_2`) | Crítico con soporte inotrópico (`es_cj_hemo_1`) |
| 7 | **Respiración** (`es_cj_item_7_respiration`) | Respiración espontánea (`es_cj_resp_4`) | Ventilación intermitente (destete) (`es_cj_resp_3`) | Ventilación mecánica continua (`es_cj_resp_2`) | VM + PEEP alta / dificultad (`es_cj_resp_1`) |
| 8 | **Nutrición** (`es_cj_item_8_nutrition`) | Dieta completa (`es_cj_nutrition_4`) | Dieta parcial / suplementos (`es_cj_nutrition_3`) | Nutrición enteral/parenteral insuficiente (`es_cj_nutrition_2`) | Ayuno (`es_cj_nutrition_1`) |
| 9 | **Incontinencia** (`es_cj_item_9_incontinence`) | Continente / sonda (`es_cj_incont_4`) | Incontinencia urinaria ocasional (`es_cj_incont_3`) | Incontinencia urinaria total (`es_cj_incont_2`) | Incontinencia urinaria y fecal (`es_cj_incont_1`) |
| 10 | **Higiene / movilización en cama** (`es_cj_item_10_hygiene`) | Se moviliza solo (`es_cj_bed_4`) | Requiere ayuda parcial (`es_cj_bed_3`) | Requiere mucha ayuda (`es_cj_bed_2`) | Dependiente total (`es_cj_bed_1`) |

### Total

| Concepto | Valor |
|---|---|
| Mínimo | 10 |
| Máximo | 40 |
| Registro en la app | `TOTAL C&J` (`es_cj_total_label`) — `%1$d / 40` (`es_cj_total_value`) |

## Cómo explorar cada ítem (técnica)

1. **Edad.** Registrar la edad real del paciente.
2. **Peso.** Valorar el estado ponderal (normal, obesidad, caquexia o pérdida > 20 %) y la presencia de **edema**, que agrava el riesgo.
3. **Estado de la piel.** **Inspeccionar** la piel (especialmente prominencias óseas) y clasificar: intacta, eritema, excoriación o necrosis/exudado.
4. **Estado mental.** Valorar el nivel de consciencia y la colaboración: alerta, apático/confuso, semicomatoso o comatoso.
5. **Movilidad.** Valorar la capacidad de movimiento: completa, limitación leve, muy limitada (silla) o inmóvil (cama).
6. **Hemodinámica.** Valorar la estabilidad y la necesidad de **soporte inotrópico o reposición de volumen**; la inestabilidad con vasoactivos empeora la perfusión cutánea.
7. **Respiración.** Valorar el soporte respiratorio: espontánea, ventilación intermitente (destete), ventilación mecánica continua o VM con PEEP alta/dificultad.
8. **Nutrición.** Valorar la ingesta y el soporte nutricional: dieta completa, parcial/suplementos, nutrición enteral/parenteral insuficiente o ayuno.
9. **Incontinencia.** Registrar la continencia urinaria y fecal (o el manejo de sonda).
10. **Higiene / movilización en cama.** Valorar la dependencia para movilizarse y para la higiene: se moviliza solo, requiere ayuda parcial, mucha ayuda o dependencia total.

**Errores frecuentes:** invertir la orientación de la escala (recordar que **4 = menor riesgo**); no inspeccionar la piel; no considerar la inestabilidad hemodinámica; y valorar solo el turno actual sin considerar las 24 h.

## Puntuación total e interpretación

La app aplica un **corte en 25 puntos** (`clasificacionCubbinJackson`: `total >= 25` → riesgo bajo; `< 25` → riesgo alto):

| Puntuación | Resultado en la app | Actuación de enfermería |
|---|---|---|
| **≥ 25** | `Riesgo bajo` (`es_braden_riesgo_bajo`) | Cuidados habituales de la piel, cambios posturales programados y reevaluación |
| **< 25 (≤ 24)** | `Riesgo muy alto — UPP probable` (`es_cj_risk_very_high`) | **Medidas preventivas intensivas**: cambios posturales frecuentes (cada 2 h o según tolerancia), superficies de apoyo, cuidado de la piel y de la humedad, control de la incontinencia, soporte nutricional y movilización precoz |

Un total **< 25** identifica al paciente crítico con **riesgo muy alto de UPP**. Los ítems de **hemodinámica** (vasopresores) y **respiración** (VM con PEEP) reflejan factores de riesgo propios de la UCI que otras escalas no recogen, y que se asocian a **UPP por dispositivos y a menor tolerancia a la movilización**. Debe registrarse al ingreso en UCI y **reevaluarse periódicamente** y ante cambios clínicos.

> **Nota sobre la app:** los paneles informativos conservan textos de una **versión anterior de la escala (10 ítems de 1-3 puntos, total 10-30, con tramos 10-12/13-15/16-20/≥ 21)**; la puntuación que aplica realmente la pantalla es la de la tabla anterior (1-4 puntos, total 10-40, corte en 25).

## Validez

La escala de Cubbin & Jackson fue desarrollada por **Cubbin y Jackson (Intensive Care Nurs 1991)** específicamente para **pacientes de cuidados intensivos**, con el objetivo de disponer de una calculadora de riesgo de UPP adaptada a las particularidades del paciente crítico (inestabilidad hemodinámica, ventilación mecánica, inmovilidad). Los estudios de validación la compararon con otras escalas y mostraron su utilidad en la población de UCI.

Es una de las escalas de riesgo de UPP **específicas de críticos** más citadas. No se incluyen cifras concretas de sensibilidad, especificidad o AUC porque varían según la población y el punto de corte; para el detalle debe consultarse la publicación original.

## Limitaciones y errores frecuentes

- No es una escala **pediátrica**: está diseñada para el **adulto crítico**.
- **Atención a la orientación de la puntuación**: en esta implementación el valor **4 es el de menor riesgo** y el **1 el de mayor riesgo**, de modo que el total alto indica menor riesgo (corte en 25).
- Los paneles informativos de la app conservan textos de una **versión anterior (1-3 puntos, total 10-30)**, lo que puede confundir; la puntuación válida es la de la pantalla.
- **No sustituye a la inspección de la piel** ni a la valoración clínica individual.
- La valoración hemodinámica y respiratoria puede variar rápidamente; la puntuación es una fotografía del momento.
- La **subjetividad** de algunos ítems (peso, estado mental) puede generar variabilidad entre valoradores.

## Ejemplo práctico resuelto

**Caso.** Varón de 74 años en UCI, en ventilación mecánica con PEEP 12, inestable con noradrenalina a dosis bajas, caquéctico, con edema, somnoliento, inmóvil en cama, con nutrición enteral insuficiente, incontinencia urinaria total y dependencia total para la higiene. Piel con eritema en el sacro.

| Ítem | Valor | Puntos |
|---|---|---|
| Edad | > 70 años | 1 |
| Peso | Caquéctico + edema → cualquier peso + edema | 1 |
| Estado de la piel | Eritema | 3 |
| Estado mental | Semicomatoso | 2 |
| Movilidad | Inmóvil | 1 |
| Hemodinámica | Inestable con inotrópicos | 2 |
| Respiración | VM + PEEP alta | 1 |
| Nutrición | Nutrición enteral insuficiente | 2 |
| Incontinencia | Urinaria total | 2 |
| Higiene/movilización | Dependiente total | 1 |
| **Total** | | **16** |

**Cubbin & Jackson = 16 → < 25 → riesgo muy alto, UPP probable.**

**Actuación de enfermería:** instaurar **medidas preventivas intensivas**: cambios posturales cada 2 h (o según tolerancia hemodinámica), superficie de apoyo adecuada, protección del sacro y de los talones, control estricto de la humedad y de la incontinencia, optimización del soporte nutricional con el equipo, inspección de la piel en cada movilización y **reevaluación cada 24 h**. Registrar la puntuación, las medidas y las lesiones.

## Relación con otras escalas

- **Braden:** escala de riesgo de UPP de uso internacional, menos específica de UCI.
- **EMINA:** escala española validada también en pacientes críticos.
- **Barthel:** la dependencia funcional se relaciona con el riesgo de UPP.
- **SOFA:** la disfunción orgánica y la inestabilidad se asocian a mayor riesgo cutáneo.
- **RASS:** el nivel de sedación condiciona la movilidad y la colaboración.

## Puntos clave

- Escala de riesgo de UPP **específica del paciente crítico**.
- **10 ítems** con **4 niveles (1-4)**; total **10-40**.
- **A mayor puntuación, menor riesgo**; corte en **25**.
- **< 25** → riesgo muy alto e indicación de **prevención intensiva**.
- Incluye factores propios de UCI: **hemodinámica y respiración**.
- Reevaluar periódicamente y ante cambios clínicos.
- **No sustituye a la inspección de la piel**.
- Atención a la orientación de la escala (4 = menor riesgo) y a los textos antiguos del panel.

---

## Evidencia y referencias

- **Cubbin B, Jackson C.** Trial of a pressure area risk calculator for intensive therapy patients. *Intensive Care Nurs* 1991;7:40-44.
- **Pancorbo-Hidalgo PL, et al.** Risk assessment scales for pressure ulcer prevention: a systematic review. *J Adv Nurs* 2006.
- **NPIAP/EPUAP/PPPIA.** Prevention and Treatment of Pressure Ulcers/Injuries: Clinical Practice Guideline. 2019.

> Es específica del paciente crítico, pero su validación externa es limitada. En planta pueden usarse Braden o EMINA.

---

## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **Cubbin & Jackson** | Riesgo de UPP en UCI |
| **Braden / EMINA** | Alternativas en otros contextos |
| **Prevención de UPP** | Medidas y superficies |
| **Cuidados de la piel** | Inspección y registro |
