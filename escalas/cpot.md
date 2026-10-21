# CPOT · Critical-Care Pain Observation Tool

> 📖 **Fuentes:** Gélinas C, Fillion L, Puntillo KA, Viens C, Fortier M. *Validation of the Critical-Care Pain Observation Tool in adult patients.* Am J Respir Crit Care Med. 2006;174(3):282-288. · Devlin JW, Skrobik Y, Gélinas C, et al. *PADIS Clinical Practice Guidelines.* Crit Care Med. 2018;46(9):e825-e873. · Lynn-McHale Wiegand DJ, ed. *AACN Procedure Manual for Critical Care.* 7th ed. Elsevier.

## Qué mide y para qué sirve

La **CPOT (Critical-Care Pain Observation Tool)** es una escala **observacional** de dolor para pacientes críticos que **no pueden comunicarse** (sedados, intubados o con alteración de la consciencia). Valora **4 indicadores** —expresión facial, movimientos corporales, tensión muscular y cumplimiento con el ventilador—, cada uno de **0 a 2 puntos**, con un total de **0 a 8**. Punto de corte: **> 2 = dolor** (`es_cpot_intro_hint`).

Sirve para:

- **Detectar el dolor** en el paciente crítico no comunicativo.
- **Guiar la analgesia**: indicar rescates, titular perfusiones y evaluar la respuesta.
- **Valorar el dolor durante los procedimientos** (aspiración de secreciones, curas, movilización, retirada de drenajes).
- **Diferenciar el dolor** de otras causas de agitación o de lucha con el respirador.
- **Registrar y comunicar** el dolor de forma objetiva entre turnos.

Es una de las escalas **recomendadas por las guías PADIS 2018** para el paciente crítico que no puede autoinformar el dolor, junto con la BPS (`es_cpot_info_source`).

## Población diana

- **Pacientes adultos críticos** que no pueden comunicar el dolor: sedados, intubados, con delirium, con deterioro cognitivo avanzado o con alteración de la consciencia.
- Especialmente indicada en **pacientes en ventilación mecánica** (el indicador 4 valora la interacción con el respirador).
- **No es válida** en el paciente con **bloqueo neuromuscular** (los indicadores musculares no son valorables).
- En el paciente que **puede comunicarse**, la escala de elección es la **EVA**.

## Cómo se puntúa

Se valora **en reposo y, si es posible, durante la movilización** (`es_cpot_intro_hint`). Se elige **una opción por indicador** y se suman los cuatro.

### 1. Expresión facial (`es_cpot_facial_expression`)

| Puntos | Descripción | Cadena en la app |
|---|---|---|
| 0 | Relajada, neutra | `es_cpot_face_relaxed_neutral` |
| 1 | Tensa (ceño fruncido, cejas bajas) | `es_cpot_face_tense` |
| 2 | Mueca de dolor (párpados cerrados, mueca) | `es_cpot_face_grimace` |

### 2. Movimientos corporales (`es_cpot_body_movements`)

| Puntos | Descripción | Cadena en la app |
|---|---|---|
| 0 | Sin movimientos o postura normal | `es_cpot_body_no_movements` |
| 1 | Protección (movimiento lento, cauteloso) | `es_cpot_body_protection` |
| 2 | Inquietud / agitación | `es_cpot_body_restlessness` |

### 3. Tensión muscular (`es_cpot_muscle_tension`)

| Puntos | Descripción | Cadena en la app |
|---|---|---|
| 0 | Sin resistencia a la movilización pasiva | `es_cpot_muscle_no_resistance` |
| 1 | Resistencia a la movilización pasiva | `es_cpot_muscle_resistance` |
| 2 | Resistencia fuerte / rigidez | `es_cpot_muscle_strong_resistance` |

### 4. Cumplimiento con el ventilador (`es_cpot_ventilator_compliance`)

| Puntos | Descripción | Cadena en la app |
|---|---|---|
| 0 | Tolera el ventilador / voz normal (no VM) | `es_cpot_vent_tolerates` |
| 1 | Tose pero tolera / suspiros, gemidos | `es_cpot_vent_coughs_tolerates` |
| 2 | Lucha con el ventilador / quejidos, llanto | `es_cpot_vent_fighting` |

### Total

| Concepto | Valor |
|---|---|
| Mínimo | 0 (0+0+0+0) |
| Máximo | 8 (2 en cada uno de los 4 indicadores) |
| Registro en la app | `TOTAL CPOT` (`es_cpot_total_label`) |
| Punto de corte | **> 2 = dolor** (`es_cpot_intro_hint`) |

## Cómo explorar cada ítem (técnica)

1. **Preparación.** Observar al paciente al menos **1 minuto** en reposo, sin manipulación y con la habitación en calma. Registrar primero la puntuación **en reposo** y después la obtenida **durante la movilización o el procedimiento**.
2. **Expresión facial.** Observar frente, cejas y boca: relajada (0), tensa con ceño fruncido (1), mueca de dolor con párpados cerrados (2).
3. **Movimientos corporales.** Observar la postura y los movimientos: normales o ausentes (0), movimientos lentos y cautelosos de protección (1), inquietud o agitación (2).
4. **Tensión muscular.** Realizar una **movilización pasiva suave** de un brazo (flexión/extensión del codo) y valorar la resistencia: ninguna (0), resistencia (1), resistencia fuerte o rigidez (2). No forzar si hay fracturas, trombosis o dolor evidente.
5. **Cumplimiento con el ventilador.** En el paciente **intubado**, observar la interacción con el respirador y las curvas: tolera (0), tose pero tolera, o presenta suspiros/gemidos (1), lucha con el ventilador o presenta quejidos/llanto (2). En el paciente **no intubado**, valorar la voz (normal frente a quejidos o llanto).

**Errores frecuentes:** valorar solo en reposo y no durante el procedimiento; no realizar la movilización pasiva del brazo y puntuar el tono muscular «a ojo»; atribuir la lucha con el ventilador solo al dolor sin descartar asincronía, secreciones, hipoxemia o auto-PEEP; no reevaluar tras la analgesia; y no formar al equipo, lo que aumenta la variabilidad.

## Puntuación total e interpretación

| Puntuación | Significado | Cadena en la app | Actuación de enfermería |
|---|---|---|---|
| 0 | Sin dolor | `es_cpot_no_pain` (`es_cpot_info_range_0`) | Mantener analgesia pautada si procede; reevaluar por turnos |
| 1-2 | Dolor leve | `es_cpot_mild_pain` (`es_cpot_info_range_1_2`) | Medidas no farmacológicas y analgesia pautada; reevaluar |
| 3-4 | Dolor moderado | `es_cpot_moderate_pain` (`es_cpot_info_range_3_4`) | **Rescate analgésico** según protocolo; reevaluar; comunicar si se repite |
| 5-8 | Dolor intenso — considerar analgesia | `es_cpot_severe_pain` (`es_cpot_info_range_5_8`) | **Actuación inmediata**: analgesia, aviso al equipo médico y reevaluación estrecha |

Una puntuación **> 2** indica dolor: administrar analgesia según protocolo, avisar al equipo médico si es intenso y **reevaluar tras la intervención**. La puntuación seriada permite **titular la analgesia** y comprobar su eficacia; debe registrarse junto con la intervención y la respuesta.

## Validez

La CPOT fue desarrollada y validada por Gélinas et al. (Am J Respir Crit Care Med 2006) en **pacientes adultos de UCI**, tanto **intubados como no intubados**, que no podían autoinformar el dolor. Los estudios de validación muestran **buena fiabilidad interobservador**, **consistencia interna adecuada** y **sensibilidad al cambio** tras la analgesia, con una buena capacidad para discriminar la presencia de dolor.

Está **recomendada por las guías PADIS 2018** (junto con la BPS) y es una de las escalas observacionales de dolor más utilizadas internacionalmente. No se incluyen cifras concretas de sensibilidad, especificidad o AUC porque varían según la población, el punto de corte y el procedimiento evaluado; para el detalle debe consultarse la publicación original.

## Limitaciones y errores frecuentes

- Requiere **movilización pasiva** para valorar la tensión muscular; en el paciente con **bloqueo neuromuscular** los indicadores musculares no son valorables.
- Puede confundirse con **delirium, ansiedad o disnea**; hay que integrar el resultado con la valoración global.
- Es una escala **observacional**, con variabilidad entre valoradores; conviene formación y consenso de equipo.
- No usar en pacientes que pueden comunicarse verbalmente: en ellos emplear **EVA**; una alternativa observacional es **ESCID**.
- La **analgesia previa** puede enmascarar los indicadores; valorar antes del rescate cuando sea posible.
- El indicador de **cumplimiento con el ventilador** exige descartar causas no dolorosas de lucha (asincronía, secreciones, hipoxemia, auto-PEEP).

## Ejemplo práctico resuelto

**Caso.** Mujer de 66 años, en ventilación mecánica por neumonía, con sedación ligera. Se valora **antes** de la aspiración de secreciones.

- **Expresión facial:** ceño fruncido → **1**.
- **Movimientos corporales:** postura normal, sin movimientos → **0**.
- **Tensión muscular:** resistencia a la movilización pasiva → **1**.
- **Cumplimiento con el ventilador:** tolera el respirador → **0**.

**Total: 2 puntos → dolor leve (1-2), sin superar el punto de corte (> 2).**

**Actuación de enfermería:** realizar la aspiración con técnica suave y preoxigenación, **reevaluar la CPOT inmediatamente después del procedimiento** (es frecuente que suba) y, si supera 2 puntos, administrar el rescate analgésico prescrito y volver a valorar a los 30 minutos. Registrar ambos valores (antes y después) y la intervención.

## Relación con otras escalas

- **EVA:** escala autoinformada; se usa cuando el paciente puede comunicarse.
- **ESCID:** escala observacional alternativa, validada en español.
- **BPS:** otra escala observacional recomendada por PADIS.
- **RASS:** la agitación puede deberse al dolor; valorar el dolor antes de aumentar la sedación.
- **CAM-ICU:** el dolor no controlado es factor precipitante de delirium.
- **VAS (asincronía):** la lucha con el ventilador puede ser dolor, asincronía o ambas.

## Puntos clave

- Valora el **dolor observacional** en el paciente crítico no comunicativo.
- **4 indicadores** de **0 a 2** puntos; total **0-8**.
- **Punto de corte > 2 = dolor**.
- Valorar **en reposo y durante los procedimientos**.
- La **movilización pasiva** es imprescindible para el tono muscular.
- **Reevaluar tras la analgesia** y registrar la intervención.
- Recomendada por **PADIS 2018** junto con la BPS.
- No es valorable con **bloqueo neuromuscular**.
---
## Evidencia y referencias

- **Gélinas C, et al.** Validation of the Critical-Care Pain Observation Tool in adult patients. *Am J Crit Care* 2006;15:420-427.
- **Gélinas C, et al.** Pain assessment in the critically ill adult: recent evidence and new trends. *Intensive Crit Care Nurs* 2016.
- **Devlin JW, et al.** PADIS Guidelines. *Crit Care Med* 2018.

> Es observacional y requiere respuesta motora; no es válida en pacientes con bloqueo neuromuscular. Debe valorarse en reposo y durante procedimientos.

---
## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **CPOT** | Dolor en paciente no comunicativo |
| **ESCID** | Alternativa validada en español |
| **EVA** | Dolor en paciente comunicativo |
| **Sedoanalgesia** | Analgesia y rescates |
