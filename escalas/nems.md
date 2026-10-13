# NEMS (Nine Equivalents of Nursing Manpower Use Score)

> 📖 **Fuentes:** Miranda DR, Moreno R, Iapichino G. *Nine equivalents of nursing manpower use score (NEMS).* Intensive Care Med. 1997;23(7):760-765. · Chulay M, Burns SM. *AACN Essentials of Critical Care Nursing.* McGraw-Hill.

## Qué mide y para qué sirve

El **NEMS** cuantifica la **carga de trabajo de enfermería en UCI** durante las **últimas 24 horas** a partir de **9 ítems** (`es_nems_description`). Cada ítem se marca como presente o ausente (**Sí / No**) y tiene un **peso fijo** según el consumo de recursos que implica. El total puede alcanzar **66 puntos** (la app indica el rango como «0 – 63+», `es_total_score_range`).

Sirve para:

- **Estimar las necesidades de personal** de enfermería por turno y por unidad (`es_nems_purpose`).
- **Comparar la carga de trabajo** entre unidades, turnos y periodos.
- **Justificar recursos** ante la dirección y en la planificación de plantillas.
- **Ajustar la asignación de pacientes** a cada profesional según su complejidad.
- **Investigar** en gestión de cuidados y en resultados de enfermería.

**No es una escala de gravedad clínica del paciente**; mide consumo de recursos y carga de trabajo.

## Población diana

- **Pacientes ingresados en UCI** durante al menos 24 horas.
- Se aplica **por paciente y por día** (últimas 24 h), no por turno aislado.
- Es útil en **unidades de críticos de cualquier tipo** (médica, quirúrgica, cardiológica, neuro), aunque su comparación entre unidades requiere criterios homogéneos.
- **No se aplica** a plantas de hospitalización convencional ni a urgencias.

## Cómo se puntúa

Instrucción de la app (`es_select_option_last_24h`): *marca la opción correspondiente a las últimas 24 h*. Cada ítem vale **0** si no está presente y su **peso fijo** si lo está.

| # | Ítem (app) | Peso si Sí | Cadena de la opción |
|---|---|---|---|
| 1 | **Monitorización** — monitorización básica (constantes horarias) | **+9** | `es_nems_monitoring` |
| 2 | **Medicación intravenosa** (bolo o perfusión) | **+6** | `es_nems_iv_medication` |
| 3 | **Ventilación mecánica** | **+12** | `es_nems_mechanical_ventilation` |
| 4 | **Soporte ventilatorio suplementario** (O₂, nebulización) | **+3** | `es_nems_supplementary_ventilatory` |
| 5 | **Un fármaco vasoactivo** | **+7** | `es_nems_single_vasoactive` |
| 6 | **Múltiples fármacos vasoactivos** | **+12** | `es_nems_multiple_vasoactive` |
| 7 | **Técnicas de diálisis** | **+6** | `es_nems_dialysis` |
| 8 | **Intervenciones específicas en UCI** (intubación, cardioversión…) | **+5** | `es_nems_interventions_icu` |
| 9 | **Intervenciones específicas fuera de UCI** (cirugía, pruebas…) | **+6** | `es_nems_interventions_outside_icu` |

Todos los ítems se responden con **«Sí»** (`es_downton_option_yes`) o **«No»** (`es_downton_option_no`).

### Total

| Concepto | Valor |
|---|---|
| Mínimo | 0 |
| Máximo | 66 (9 + 6 + 12 + 3 + 7 + 12 + 6 + 5 + 6) |
| Registro en la app | `TOTAL NEMS (24 h)` (`es_total_nems_24h`) · `es_total_score_range` («0 – 63+») |

## Cómo explorar cada ítem (técnica)

El NEMS **no se explora en el paciente**: se construye revisando **lo realizado en las últimas 24 horas** en el registro de enfermería y la hoja de cuidados.

1. **Monitorización.** Marcar si el paciente ha precisado **monitorización básica con constantes horarias** (no basta la monitorización intermitente habitual de planta).
2. **Medicación intravenosa.** Marcar si ha recibido **medicación IV en bolo o perfusión** (antibióticos, analgésicos, etc.).
3. **Ventilación mecánica.** Marcar si ha estado en **ventilación mecánica** (invasiva o no invasiva según el criterio de la unidad); es el ítem de mayor peso junto con los vasoactivos múltiples.
4. **Soporte ventilatorio suplementario.** Marcar si ha precisado **oxigenoterapia o nebulizaciones**.
5. **Un fármaco vasoactivo.** Marcar si ha recibido **un solo** vasoactivo en perfusión.
6. **Múltiples fármacos vasoactivos.** Marcar si ha recibido **dos o más** vasoactivos.
7. **Técnicas de diálisis.** Marcar si ha precisado **diálisis** o técnicas continuas de depuración.
8. **Intervenciones específicas en UCI.** Marcar si se han realizado procedimientos como **intubación, cardioversión, colocación de catéteres centrales o drenajes**.
9. **Intervenciones específicas fuera de UCI.** Marcar si el paciente ha salido de la unidad para **cirugía o pruebas** con acompañamiento de enfermería.

**Errores frecuentes:** marcar lo **prescrito** en lugar de lo **realizado**; no revisar las 24 h completas (solo el turno actual); duplicar ítems (marcar a la vez un vasoactivo y múltiples vasoactivos); y aplicar criterios distintos entre profesionales sin consenso previo.

## Puntuación total e interpretación

| Puntuación | Carga de trabajo | Cadena en la app | Actuación de enfermería |
|---|---|---|---|
| **< 20** | Carga baja | `es_load_low` · `es_range_low` | Asignación habitual; reevaluar la evolución |
| **20-29** | Carga moderada | `es_load_moderate` · `es_range_moderate` | Vigilar la relación enfermera/paciente; ajustar si procede |
| **30-39** | Carga alta | `es_load_high` · `es_range_high` | Revisar la asignación de cargas y priorizar cuidados; comunicar a la supervisión |
| **≥ 40** | Carga muy alta | `es_load_very_high` · `es_range_very_high` | Reforzar el personal si es posible; revisar la seguridad del paciente y la ratio enfermera/paciente |

## Validez

El NEMS fue desarrollado por **Miranda et al. (Intensive Care Med 1997)** como una **simplificación del TISS** (Therapeutic Intervention Scoring System), con el objetivo de medir la **carga de trabajo de enfermería** con un número reducido de ítems y de forma comparable entre unidades. Se validó en **unidades de cuidados intensivos europeas** (en el marco del proyecto EURICUS) y mostró una **buena correlación con el TISS-28** y con otras medidas de carga asistencial.

Su utilidad principal es **de gestión**, no clínica: no predice la mortalidad ni la gravedad del paciente, y su comparación entre unidades exige criterios homogéneos de registro. No se incluyen cifras concretas de sensibilidad, especificidad o AUC porque no es una escala diagnóstica ni pronóstica.

## Limitaciones y errores frecuentes

- **No mide la gravedad ni el pronóstico** del paciente; para eso deben usarse escalas como SOFA (`sofa.md`), NEWS2 (`news2.md`) o APACHE II.
- Es sensible a la **variabilidad en el registro**: un mismo paciente puede obtener puntuaciones distintas según lo que se documente.
- Está pensado para **periodos de 24 h**; no debe usarse para valoraciones puntuales de un turno aislado sin ajustar la interpretación.
- Su uso requiere **consenso de equipo** sobre qué se considera cada ítem (p. ej., qué cuenta como «monitorización básica» o como «intervención específica»).
- No recoge **tiempos reales** de cuidados ni la complejidad relacional o emocional (familia, cuidados al final de la vida).
- Puede **infraestimar** la carga de pacientes con necesidades de comunicación, movilización o cuidados paliativos intensivos.

## Ejemplo práctico resuelto

**Caso.** Varón de 70 años en UCI, en las últimas 24 h: monitorización con constantes horarias, antibioterapia IV en perfusión, ventilación mecánica invasiva, oxigenoterapia adicional, **dos** fármacos vasoactivos, sin diálisis, con intubación programada y un traslado a radiología.

| Ítem | Puntos |
|---|---|
| Monitorización (constantes horarias) | 9 |
| Medicación intravenosa | 6 |
| Ventilación mecánica | 12 |
| Soporte ventilatorio suplementario | 3 |
| Múltiples fármacos vasoactivos | 12 |
| Intervenciones específicas en UCI (intubación) | 5 |
| Intervenciones específicas fuera de UCI (radiología) | 6 |
| **Total** | **53** |

**Carga muy alta (≥ 40).**

**Actuación de enfermería:** registrar el NEMS con el detalle de los ítems marcados, revisar con la supervisión la asignación de cargas y la ratio enfermera/paciente, priorizar los cuidados de mayor complejidad (ventilación, vasoactivos, movilización), y usar el dato para justificar refuerzo de personal en el turno.

## Relación con otras escalas

- **SOFA:** valora la disfunción orgánica y la gravedad clínica; complementa al NEMS.
- **NEWS2:** alerta precoz de deterioro; mide gravedad fisiológica, no carga de trabajo.
- **TISS-28:** escala original de la que deriva el NEMS.
- **MRC Sum Score y Barthel:** valoran la función y la dependencia, que influyen en la carga de cuidados.
- **CPOT/ESCID, CAM-ICU y RASS:** generan intervenciones que incrementan la carga de enfermería.

## Puntos clave

- Mide la **carga de trabajo de enfermería en UCI** de las **últimas 24 h**.
- **9 ítems** con pesos fijos; total de **0 a 66**.
- **< 20** baja; **20-29** moderada; **30-39** alta; **≥ 40** muy alta.
- Refleja **lo realizado**, no lo prescrito.
- **No mide gravedad ni pronóstico**: es una herramienta de gestión.
- Su fiabilidad depende del **registro y del consenso del equipo**.
- Sirve para **estimar plantillas** y comparar unidades o periodos.
- Debe completarse con escalas clínicas (SOFA, NEWS2).
