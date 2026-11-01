---
layout: default
title: "Escala de Murray (LIS · Lung Injury Score)"
---
# Escala de Murray (LIS · Lung Injury Score)

> 📖 **Fuentes:** Murray JF, Matthay MA, Luce JM, Flick MR. *An expanded definition of the adult respiratory distress syndrome.* Am Rev Respir Dis. 1988;138(3):720-723. · Marino PL. *The ICU Book.* 4th ed. Wolters Kluwer.

## Qué mide y para qué sirve

La **escala de Murray (Lung Injury Score, LIS)** cuantifica la **gravedad de la lesión pulmonar aguda / SDRA**. Valora **4 componentes** —infiltrados radiológicos, oxigenación (PaO₂/FiO₂), PEEP y compliance estática—, cada uno de **0 a 4 puntos**. La **puntuación final es la suma dividida entre 4** (`LIS = suma / 4`), de modo que el resultado va de **0 a 4** con decimales.

Sirve para:

- **Cuantificar la gravedad** de la lesión pulmonar al ingreso y en su evolución.
- **Objetivar la respuesta** a las medidas de soporte (PEEP, pronación, ventilación protectora).
- **Estratificar el pronóstico** y comparar pacientes y poblaciones.
- **Documentar la evolución** del SDRA de forma estandarizada.
- **Apoyar la comunicación** entre turnos y con el equipo médico.

## Población diana

- **Pacientes adultos con insuficiencia respiratoria hipoxémica y sospecha de SDRA**, habitualmente en **ventilación mecánica invasiva**.
- Requiere **gasometría arterial**, **radiografía de tórax** y **parámetros ventilatorios** (PEEP y compliance estática).
- **No es aplicable** de forma completa en el paciente no intubado (CNAF, ventilación no invasiva), donde algunos componentes no pueden medirse.
- No sustituye a los **criterios de Berlín** para la definición y clasificación del SDRA.

## Cómo se puntúa

Se completa cada uno de los 4 componentes. La app calcula automáticamente la PaO₂/FiO₂ y los puntos de PEEP y compliance a partir de los valores introducidos.

### 1. Infiltrados en la radiografía de tórax (`es_infiltrados_rx_torax`)

| Puntos | Hallazgo | Cadena en la app |
|---|---|---|
| 0 | Sin infiltrados | `es_infiltrados_sin` |
| 1 | 1 cuadrante | `es_infiltrados_1_cuadrante` |
| 2 | 2 cuadrantes | `es_infiltrados_2_cuadrantes` |
| 3 | 3 cuadrantes | `es_infiltrados_3_cuadrantes` |
| 4 | 4 cuadrantes | `es_infiltrados_4_cuadrantes` |

### 2. Oxigenación · PaO₂/FiO₂ (mmHg)

La app calcula el cociente a partir de la PaO₂ (`es_pao2_label`, mmHg) y la FiO₂ (`es_fio2_label`, %) y muestra el resultado como `PaO₂/FiO₂ = %1$d mmHg` (`es_pafi_resultado`).

| Puntos | PaO₂/FiO₂ |
|---|---|
| 0 | ≥ 300 |
| 1 | 225 - 299 |
| 2 | 175 - 224 |
| 3 | 100 - 174 |
| 4 | < 100 |

### 3. PEEP (cmH₂O) (`es_peep_label`)

| Puntos | PEEP |
|---|---|
| 0 | ≤ 5 |
| 1 | 6 - 8 |
| 2 | 9 - 11 |
| 3 | 12 - 14 |
| 4 | ≥ 15 |

### 4. Compliance estática (mL/cmH₂O) (`es_compliance_estatica_label`)

| Puntos | Compliance |
|---|---|
| 0 | ≥ 80 |
| 1 | 60 - 79 |
| 2 | 40 - 59 |
| 3 | 20 - 39 |
| 4 | ≤ 19 |

### Total

| Concepto | Valor |
|---|---|
| Suma de los 4 componentes | 0 – 16 (`es_puntos_total`) |
| **Puntuación LIS** | **suma / 4** → 0 – 4 (`es_lis_murray_suma`) |
| Requisito | Deben completarse **los 4 campos** (`es_completa_todos_los_campos`) |

## Cómo explorar cada ítem (técnica)

1. **Infiltrados radiológicos.** Revisar la **radiografía de tórax** (o TC) y contar los **cuadrantes** afectados por infiltrados alveolares no explicados por derrame, atelectasia o cardiomegalia. La valoración es visual y sistemática (cuadrantes superior/inferior y derecho/izquierdo).
2. **PaO₂/FiO₂.** Obtener una **gasometría arterial** con la **FiO₂** administrada en ese momento; calcular el cociente dividiendo la PaO₂ (mmHg) entre la FiO₂ en fracción. Registrar ambos valores juntos.
3. **PEEP.** Anotar la **PEEP total** programada en el ventilador (cmH₂O) en el momento de la medición.
4. **Compliance estática.** Medirla en **ventilación controlada**, con el paciente **sin esfuerzo espontáneo** (o con sedación/relajación adecuadas) y sin auto-PEEP significativa, mediante una pausa inspiratoria: **compliance = volumen tidal / (presión meseta − PEEP)**.
5. **Calcular el LIS** = suma de los 4 componentes / 4 y registrar el valor con los datos utilizados.

**Errores frecuentes:** calcular la PaO₂/FiO₂ con una FiO₂ distinta a la del momento de la gasometría; medir la compliance con esfuerzo espontáneo o con fugas; no contar bien los cuadrantes; y no registrar juntos los datos que alimentan la puntuación.

## Puntuación total e interpretación

| LIS (suma/4) | Lectura | Cadena en la app | Actuación de enfermería |
|---|---|---|---|
| 0 | Sin lesión pulmonar | `es_sin_lesion_pulmonar` | Ventilación protectora según indicación; vigilancia habitual |
| 0,1 – 2,5 | Lesión leve-moderada | `es_lesion_pulmonar_leve` | Mantener ventilación protectora, vigilar oxigenación y evolución |
| > 2,5 | Lesión grave | `es_lesion_pulmonar_grave` | Ventilación protectora, control de la causa y vigilancia estrecha; valorar con el equipo pronación y otras medidas |

La app solo calcula el LIS cuando los **cuatro componentes** son válidos (`es_murray_interpretacion`). Si falta uno, no imputa cero ni estima el valor ausente: un LIS incompleto no es un LIS bajo.

Un LIS **> 2,5** corresponde a lesión pulmonar grave en la descripción original. Orienta a revisar la ventilación protectora, el control de la causa y la vigilancia, pero no convierte por sí solo la pronación o el bloqueo neuromuscular en indicaciones automáticas: son decisiones clínicas. La tendencia del LIS es útil para valorar la respuesta al tratamiento.

## Validez

La escala de Murray fue descrita por **Murray et al. (Am Rev Respir Dis 1988)** como una **definición ampliada del SDRA** que combinaba criterios clínicos, radiológicos y fisiológicos. Fue una de las primeras herramientas en cuantificar la gravedad de la lesión pulmonar y se utilizó durante años en investigación y en la práctica clínica; se ha relacionado con la mortalidad y con la duración de la ventilación mecánica.

Con la publicación de la **definición de Berlín (2012)** y de las guías posteriores, la clasificación del SDRA se basa en el grado de hipoxemia (PaO₂/FiO₂ con PEEP ≥ 5) y en los infiltrados bilaterales; el LIS sigue siendo útil como **medida cuantitativa de gravedad** y para el seguimiento. No se incluyen cifras concretas de sensibilidad, especificidad o AUC porque la escala no es una prueba diagnóstica, sino un índice de gravedad.

## Limitaciones y errores frecuentes

- Los infiltrados se valoran de forma **subjetiva** en la radiografía, lo que introduce variabilidad entre observadores.
- La **compliance estática** requiere que el paciente esté en ventilación mecánica controlada y sin esfuerzo espontáneo para ser fiable.
- No sustituye a los **criterios de Berlín** para la clasificación del SDRA ni a la valoración clínica global.
- En el paciente **no intubado** (CNAF, ventilación no invasiva) algunos componentes pueden no ser medibles y el índice no debe completarse por inferencia.
- La **PEEP y la compliance** pueden cambiar rápidamente; la puntuación es una fotografía del momento.
- La PaO₂/FiO₂ puede verse alterada por la altitud, la FiO₂ administrada y el tiempo de evolución.
- No incorpora otros factores pronósticos (edad, comorbilidad, sepsis de origen).
- Un LIS calculado con un componente estimado o imputado **no es comparable** con otro obtenido con los cuatro medidos.

## Ejemplo práctico resuelto

**Caso.** Mujer de 55 años con neumonía grave y SDRA, en ventilación mecánica.

- **Infiltrados:** 3 cuadrantes → **3**.
- **PaO₂/FiO₂:** PaO₂ 80 mmHg con FiO₂ 0,60 → 133 → **3** (100-174).
- **PEEP:** 12 cmH₂O → **3**.
- **Compliance estática:** 30 mL/cmH₂O → **3**.

**Suma = 12; LIS = 12 / 4 = 3,0** → lesión pulmonar grave (> 2,5).

**Actuación de enfermería:** registrar el LIS y los datos empleados (gasometría, FiO₂, PEEP, compliance, Rx), mantener la ventilación protectora según indicación y protocolo, vigilar la oxigenación y la hemodinámica, comentar con el equipo la pronación y la sedación/relajación si procede, y repetir la valoración para seguir la evolución.

## Relación con otras escalas

- **ROX:** valora la respuesta a la cánula nasal de alto flujo antes de la intubación.
- **Índice de Tobin (RSBI):** valora el destete cuando el paciente mejora.
- **VAS (asincronía):** relevante en la ventilación mecánica del SDRA.
- **SOFA:** incluye el componente respiratorio (PaO₂/FiO₂) y valora la disfunción orgánica global.
- **NEWS2:** alerta precoz de deterioro, previa al desarrollo del SDRA.

## Puntos clave

- Cuantifica la **gravedad del SDRA** con **4 componentes** de 0 a 4.
- **LIS = suma / 4**, con resultado de **0 a 4**.
- **0** sin lesión; **0,1-2,5** lesión leve-moderada; **> 2,5** lesión grave.
- Solo se calcula con los **cuatro componentes** válidos; no se imputan ausencias.
- Requiere **gasometría, radiografía, PEEP y compliance estática** del mismo momento.
- La **compliance** debe medirse en ventilación controlada sin esfuerzo espontáneo.
- Los infiltrados se valoran por **cuadrantes** y con variabilidad interobservador.
- Es una medida de **gravedad y seguimiento**, no un criterio diagnóstico aislado.
- Repetir cada 24 h para valorar la **respuesta al tratamiento**.

---

## Evidencia y referencias

- **Murray JF, et al.** An expanded definition of the adult respiratory distress syndrome. *Am Rev Respir Dis* 1988;138:720-723.
- **ARDS Definition Task Force.** Acute respiratory distress syndrome: the Berlin Definition. *JAMA* 2012;307:2526-2533.
- **Fan E, et al.** ATS/ESICM/SCCM Clinical Practice Guideline: Mechanical Ventilation in Adult Patients with ARDS. *Am J Respir Crit Care Med* 2017.

> El LIS de Murray es histórico; la definición vigente es la de Berlín (PaO₂/FiO₂ ≤ 300 con PEEP ≥ 5). No usar el LIS aislado para definir SDRA.

---

## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **Escala de Murray** | Gravedad radiológica y de oxigenación |
| **SDRA** | Definición de Berlín y manejo |
| **PaFi** | Oxigenación |
| **Ventilación protectora** | Volumen y presión |
