---
layout: default
title: "HACOR score (Heart rate, Acidosis, Consciousness, Oxygenation, Respiratory rate)"
---
# HACOR score (Heart rate, Acidosis, Consciousness, Oxygenation, Respiratory rate)

> 📖 **Fuentes:** Duan J, Wang S, Liu P, et al. *Assessment of heart rate, acidosis, consciousness, oxygenation, and respiratory rate to predict noninvasive ventilation failure in hypoxemic patients.* Intensive Care Med. 2017;43(2):192-199. · Chulay M, Burns SM. *AACN Essentials of Critical Care Nursing.* McGraw-Hill. · Lynn-McHale Wiegand DJ, ed. *AACN Procedure Manual for Critical Care.* 7th ed. Elsevier. · SEEIUC: https://www.seeiuc.org

El **HACOR** es una escala **predictiva** diseñada para estimar, en las **primeras horas de ventilación mecánica no invasiva (VMNI)**, la probabilidad de **fracaso** de la técnica y, por tanto, la necesidad de **intubación**. Se calcula con cinco variables que la enfermera ya registra en la valoración: **frecuencia cardíaca (H), pH (A), nivel de conciencia (C), oxigenación PaO₂/FiO₂ (O) y frecuencia respiratoria (R)**.

Responde a una pregunta muy concreta de la UCI: *«este paciente en VMNI por insuficiencia respiratoria hipoxémica, ¿está mejorando o se va a intubar?»*.

---

## 1. Población diana y contexto

- **Adultos con insuficiencia respiratoria aguda hipoxémica** tratados con **VMNI** (habitualmente CPAP o BiPAP con interfaz oronasal).
- Se aplica **después de 1-2 horas** de VMNI (y puede repetirse a las 12, 24 y 48 h).
- Es especialmente útil cuando la decisión de intubar es difícil: el HACOR **objetiva la tendencia** y ayuda a no retrasar la intubación.
- **No está diseñado** para la VMNI de la agudización de la EPOC hipercápnica como indicación principal (aunque puede orientar), ni para la ventilación invasiva.

> En la app, el campo **PaO₂/FiO₂** puede tomarse del último registro de la valoración integral o calcularse con la PaO₂ y la FiO₂ del paciente.

---

## 2. Cómo se puntúa

Se suman cinco componentes. La app implementa exactamente estos cortes:

### ❤️ Frecuencia cardíaca (FC)

| FC (lpm) | Puntos |
|---|---|
| ≤ 120 | 0 |
| > 120 | 1 |

### 🩸 pH arterial (acidosis)

| pH | Puntos |
|---|---|
| ≥ 7,35 | 0 |
| 7,30-7,34 | 1 |
| 7,25-7,29 | 2 |
| < 7,25 | 3 |

### 🧠 Nivel de conciencia (Glasgow)

| GCS | Puntos |
|---|---|
| 15 | 0 |
| 13-14 | 1 |
| 11-12 | 2 |
| ≤ 10 | 3 |

### 🫁 Oxigenación (PaO₂/FiO₂)

| PaO₂/FiO₂ | Puntos |
|---|---|
| ≥ 201 | 0 |
| 176-200 | 1 |
| 151-175 | 2 |
| 126-150 | 3 |
| 101-125 | 4 |
| ≤ 100 | 5 |

### 💨 Frecuencia respiratoria (FR)

| FR (rpm) | Puntos |
|---|---|
| ≤ 30 | 0 |
| 31-35 | 1 |
| 36-40 | 2 |
| 41-45 | 3 |
| > 45 | 4 |

**Total: 0 a 25 puntos.**

---

## 3. Interpretación

| Total | Interpretación | Actuación |
|---|---|---|
| **0-4** | Riesgo bajo de fracaso de la VMNI | Mantener VMNI, reevaluar a las 1-2 h y después según evolución |
| **≥ 5** | **Alto riesgo de fracaso** | Avisar al médico, optimizar interfaz y parámetros, valorar **intubación** y preparar el material de vía aérea |
| **≥ 10** | Riesgo muy elevado (fracaso precoz) | Intubación probablemente inminente; no demorar el aviso |

La app muestra además el **desglose por componentes**, imprescindible para saber **qué** está fallando (p. ej. empeora la oxigenación pero mejora el pH) y para recalcular el score en la siguiente valoración.

**Ejemplo.** Paciente con FC 118, pH 7,31, GCS 14, PaO₂/FiO₂ 145 y FR 34:
`0 (FC) + 1 (pH) + 1 (GCS) + 3 (PAFI) + 1 (FR) = 6 puntos` → **alto riesgo de fracaso**: avisar y valorar intubación.

---

## 4. Actuación de enfermería

1. **Registrar la hora de inicio de la VMNI** y el momento exacto del cálculo: el HACOR se interpreta en el contexto temporal.
2. **Calcular a las 1-2 horas** y repetir de forma seriada (12, 24 y 48 h) o antes si el paciente empeora.
3. **Comprobar la calidad de la medida**: fugas de la interfaz, SpO₂ fiable, FiO₂ real, gasometría arterial (no venosa).
4. **Vigilar el trabajo respiratorio y el patrón**: uso de musculatura accesoria, tiraje, respiración paradójica, sudoración, agitación.
5. **Optimizar la VMNI** antes de concluir un fracaso: interfaz adecuada, protección cutánea, parámetros y humidificación revisados.
6. **Anticipar la intubación**: material de vía aérea, aspiración, fármacos, carro de parada y ayuda disponible.
7. **Documentar y comunicar** el total, el desglose y la evolución (mejoría o empeoramiento) al equipo médico.
8. **Enviar el resultado a Monitorización** si la app lo permite, para que quede en la valoración del paciente.

---

## 5. Errores frecuentes

- **Calcular con datos de distinta hora** (FC de la mañana con gasometría de la tarde): pierde todo el valor predictivo.
- **Usar SpO₂ en lugar de PaO₂** para el componente de oxigenación: el índice PaO₂/FiO₂ exige gasometría.
- **No registrar la FiO₂ real** (o confundir 0,5 con 50 %): el PAFI se altera por completo.
- **No anotar la hora de inicio de la VMNI** y comparar scores de fases distintas.
- **Medir el Glasgow con el paciente sedado** o bajo los efectos de la analgesia: el componente C se falsea.
- **Media de varias gasometrías** en lugar de la más próxima al momento de la valoración.
- **Interpretar un valor aislado**: la tendencia (subida del score) es el signo de alarma.
- **Retrasar el aviso** pensando que «aún hay margen» cuando el score ya es ≥ 5-10.

---

## 6. Limitaciones

- Es una escala **predictiva**, no un diagnóstico: no sustituye la valoración clínica ni la decisión del intensivista.
- Desarrollada y validada en **insuficiencia respiratoria hipoxémica**; su rendimiento en otras poblaciones (EPOC hipercápnica, postoperatorio, inmunodeprimidos) puede diferir.
- Los cortes son los del instrumento original; modificarlos invalida la escala.
- Un **score bajo no garantiza el éxito** ni un score alto obliga a intubar: hay que integrar la causa, la reversibilidad y el techo terapéutico.

---

## 7. Relación con el resto de la app

- **ROX index:** valora el fracaso de la **cánula nasal de alto flujo** (CNAF); HACOR valora la **VMNI**.
- **Índice de Tobin (RSBI):** criterio de destete de la ventilación invasiva.
- **Glasgow, RASS y CAM-ICU:** componentes neurológicos y de sedación que influyen en el score.
- **PAFI (PaO₂/FiO₂):** base del componente de oxigenación.
- **Gasometría:** fuente del pH y de la PaO₂.
- **Vía aérea artificial:** preparación de la intubación y cuidados del tubo orotraqueal.

---

## Puntos clave

- El **HACOR** predice el **fracaso de la VMNI** en la insuficiencia respiratoria hipoxémica.
- Se calcula con **FC, pH, Glasgow, PaO₂/FiO₂ y FR** (5 componentes, total **0-25**).
- **≥ 5 puntos** → alto riesgo de fracaso: avisar y valorar intubación; **≥ 10** → fracaso precoz.
- Se mide a las **1-2 horas** del inicio y de forma **seriada**; la tendencia es lo importante.
- Todos los datos deben ser **simultáneos y de la misma valoración**.
- Un score alto **no retrasa** el aviso: anticipar la vía aérea es parte del cuidado.
- Es una ayuda a la decisión, **no una orden de intubación**.

> ⚠️ Documento de apoyo: **no sustituye** el juicio clínico ni los protocolos del centro.

---

## Evidencia y referencias

- **Duan J, et al.** Assessment of heart rate, acidosis, consciousness, oxygenation, and respiratory rate to predict noninvasive ventilation failure in hypoxemic patients. *Intensive Care Med* 2017;43:192-199.
- **Rochwerg B, et al.** Official ERS/ATS clinical practice guidelines: noninvasive ventilation for acute respiratory failure. *Eur Respir J* 2017.

> Predice fracaso de VMNI en insuficiencia respiratoria hipoxémica; no sustituye la valoración clínica ni la decisión de intubar. Reevaluar a las 1-2 horas y tras cambios.

---

## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **HACOR** | Predicción de fracaso de VMNI |
| **VMNI** | Indicaciones y ajuste |
| **Gasometría** | pH y PaO₂/FiO₂ |
| **Alto flujo** | Alternativa de soporte |
