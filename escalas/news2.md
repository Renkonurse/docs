---
layout: default
title: "NEWS2 (National Early Warning Score 2)"
---
# NEWS2 (National Early Warning Score 2)

> 📖 **Fuentes:** Royal College of Physicians. *National Early Warning Score (NEWS) 2: standardising the assessment of acute-illness severity in the NHS.* London: RCP; 2017. · SEEIUC: https://www.seeiuc.org

## Qué mide y para qué sirve

El **NEWS2** es una escala de **alerta precoz de deterioro clínico** (`es_desc_news2`) que combina **7 parámetros fisiológicos** en una puntuación única. Valora la **frecuencia respiratoria, la SpO₂ (con dos escalas), el oxígeno suplementario, la temperatura, la tensión arterial sistólica, la frecuencia cardiaca y el nivel de consciencia (ACVPU)** (`es_news2_dialog_description`). A mayor puntuación, mayor riesgo de deterioro, y la frecuencia de monitorización se ajusta al nivel de riesgo (`es_dialog_note`).

Sirve para:

- **Detectar precozmente el deterioro** clínico antes de que sea evidente.
- **Estandarizar la frecuencia de monitorización** y el escalado de la respuesta.
- **Definir a quién avisar** (enfermera responsable, equipo médico, equipo de críticos) y con qué urgencia.
- **Documentar y comunicar** la gravedad fisiológica de forma objetiva.
- **Priorizar** la carga de trabajo y la vigilancia en la unidad.

## Población diana

- **Pacientes adultos hospitalizados**, tanto en urgencias como en planta de hospitalización y en unidades de críticos.
- Es aplicable a la mayoría de los pacientes, con **precauciones** en pacientes con enfermedades que alteran de forma crónica los parámetros (EPOC con hipercapnia, insuficiencia renal, arritmias).
- **No está validado** en **pacientes pediátricos** (existe una versión específica, PEWS) ni en **embarazadas** (existe la versión obstétrica, MEOWS).
- En pacientes con **deterioro crónico** (insuficiencia cardiaca avanzada, oxigenoterapia domiciliaria) hay que interpretar la tendencia más que el valor absoluto.

## Cómo se puntúa

Cada parámetro puntúa de **0 a 3**. La app introduce los valores actuales (`es_introduce_current_values`) y calcula automáticamente el total. **Puntuación total: 0 – 20** (`es_news2_dialog_total_score`).

### Frecuencia respiratoria (rpm)

| Valor | ≤ 8 | 9-11 | 12-20 | 21-24 | ≥ 25 |
|---|---|---|---|---|---|
| Puntos | 3 | 1 | 0 | 2 | 3 |

### SpO₂ · Escala 1 (por defecto)

| Valor | ≤ 91 % | 92-93 % | 94-95 % | ≥ 96 % |
|---|---|---|---|---|
| Puntos | 3 | 2 | 1 | 0 |

### SpO₂ · Escala 2 (insuficiencia respiratoria hipercápnica, diana 88-92 %)

Se activa con `es_hipercapnia_scale2` («Insuficiencia respiratoria hipercápnica (escala SpO₂ 2: 88–92 %)»). La app aplica:

| SpO₂ | En aire | Con O₂ suplementario |
|---|---|---|
| ≥ 93 % | 0 | 3 |
| 88-92 % | 0 | 0 |
| 86-87 % | 1 | 1 |
| 84-85 % | 2 | 2 |
| ≤ 83 % | 3 | 3 |

### O₂ suplementario (`es_supplementary_o2`)

| Situación | Aire | Con O₂ suplementario |
|---|---|---|
| Puntos | 0 | **2** |

### Temperatura (`es_temperature`)

| Valor | ≤ 35,0 | 35,1-36,0 | 36,1-38,0 | 38,1-39,0 | > 39,0 |
|---|---|---|---|---|---|
| Puntos | 3 | 1 | 0 | 1 | 2 |

### Tensión arterial sistólica (mmHg)

| Valor | ≤ 90 | 91-100 | 101-110 | 111-219 | ≥ 220 |
|---|---|---|---|---|---|
| Puntos | 3 | 2 | 1 | 0 | 3 |

### Frecuencia cardiaca (lpm)

| Valor | ≤ 40 | 41-50 | 51-90 | 91-110 | 111-130 | ≥ 131 |
|---|---|---|---|---|---|---|
| Puntos | 3 | 1 | 0 | 1 | 2 | 3 |

### Nivel de consciencia · ACVPU (`es_consciousness_acvpu`)

| Opción | Alerta (`es_acvpu_alert`) | Alterado (`es_acvpu_altered`) |
|---|---|---|
| Puntos | 0 | **3** |

> **ACVPU** = Alerta, Confusión, Voz, Dolor, No responde. Cualquier alteración (nueva confusión, responde a la voz o al dolor, o no responde) puntúa 3.

## Cómo explorar cada ítem (técnica)

1. **Frecuencia respiratoria.** Contar durante **1 minuto completo**, con el paciente en reposo; es el parámetro más sensible al deterioro y el primero que suele alterarse.
2. **SpO₂.** Medir con pulsioximetría en un dedo con buena perfusión, sin esmalte ni frialdad, y con el sensor bien colocado; comprobar que la curva de pletismografía es adecuada. **Elegir la escala correcta**: escala 1 por defecto; escala 2 solo en pacientes con **insuficiencia respiratoria hipercápnica** con diana 88-92 %.
3. **O₂ suplementario.** Registrar si el paciente recibe **oxígeno suplementario** (gafas, mascarilla, CNAF, ventilación no invasiva), independientemente del flujo: puntúa 2.
4. **Temperatura.** Medir preferiblemente por vía **timpánica o central**; registrar el valor real y no redondear.
5. **Tensión arterial sistólica.** Medir con manguito del tamaño adecuado, brazo a la altura del corazón y paciente en reposo; confirmar valores extremos antes de puntuar.
6. **Frecuencia cardiaca.** Obtenerla del monitor o por palpación durante 1 minuto; en arritmias, confirmar la frecuencia real.
7. **Nivel de consciencia (ACVPU).** Valorar si está **Alerta** o si hay cualquier alteración (nueva **C**onfusión, responde a la **V**oz, responde al **D**olor, **U**nresponsive). Una nueva confusión puntúa 3 aunque el paciente esté orientado después.

**Errores frecuentes:** usar la **escala 2** en pacientes que no son hipercápnicos; no puntuar el **oxígeno suplementario**; valorar la consciencia con el Glasgow en lugar del ACVPU; medir la FR en periodos cortos; y no registrar la hora de la medición.

## Puntuación total e interpretación

| Total | Riesgo | Etiqueta de la app | Monitorización / actuación |
|---|---|---|---|
| 0 | Rutina | `es_interpretation_routine` (`es_info_range_routine`) | Monitorización cada 12 h (`es_monitoring_every_12h`) |
| 1-4 | Riesgo bajo | `es_interpretation_low_risk` (`es_info_range_low_risk`) | Monitorización cada 4-6 h; la enfermera valora (`es_monitoring_every_4_6h`) |
| 5-6 | Riesgo medio | `es_interpretation_medium_risk` (`es_info_range_medium_risk`) | Monitorización cada 1 h; avisar a la enfermera responsable y al equipo médico (`es_monitoring_every_1h`) |
| ≥ 7 | Riesgo alto | `es_info_range_high_risk` | Monitorización continua; avisar al equipo de críticos de forma urgente (`es_monitoring_continuous`) |

**Regla especial** (`es_info_single_parameter`, `es_critical_parameter_warning`): **un solo parámetro con puntuación 3** fuerza al menos **riesgo medio** y muestra el aviso «⚠ Hay al menos un parámetro con puntuación 3».

El valor debe registrarse de forma **seriada** (cada 4-12 h según el riesgo): lo importante es la **tendencia ascendente**, que obliga a actuar antes de que el paciente se deteriore.

## Validez

El NEWS2 fue publicado por el **Royal College of Physicians (Londres, 2017)** como actualización del NEWS original, con el objetivo de **estandarizar la valoración de la gravedad de la enfermedad aguda** en el NHS. Está **ampliamente validado en pacientes adultos hospitalizados** y se ha asociado de forma consistente con el **riesgo de deterioro, el ingreso en UCI, la parada cardiaca y la mortalidad**; un NEWS2 elevado o en ascenso se relaciona con peor evolución.

Su principal fortaleza es que se calcula con **constantes de monitorización rutinaria** y no requiere exploraciones adicionales. Su principal limitación es la **sensibilidad variable** según la población y la existencia de pacientes que se deterioran con puntuaciones bajas (ancianos, inmunodeprimidos). No se incluyen cifras concretas de sensibilidad, especificidad o AUC porque varían según la población, el desenlace y el punto de corte; para el detalle debe consultarse la publicación del RCP y las validaciones posteriores.

## Limitaciones y errores frecuentes

- La **Escala 2 de SpO₂** solo debe usarse en pacientes con **insuficiencia respiratoria hipercápnica** (EPOC, obesidad-hipoventilación…) con diana de 88-92 %; en el resto se usa la Escala 1.
- En pacientes con **arritmias** o tratamientos que alteran la frecuencia cardiaca, el parámetro puede no reflejar el deterioro real.
- El nivel de consciencia debe valorarse como **ACVPU**, no como Glasgow; una **nueva confusión** puntúa 3 aunque el paciente esté orientado después.
- La **fiebre o la hipotermia** pueden tener causas no infecciosas; el NEWS2 no identifica la causa del deterioro.
- **No sustituye** a la valoración clínica completa ni a escalas específicas de gravedad como **SOFA** (`sofa.md`) o **qSOFA** (`qsofa.md`).
- No está validado en **pediatría** ni en **embarazo**.
- Un valor aislado es menos informativo que la **tendencia**; hay que registrar la hora y las intervenciones.

## Ejemplo práctico resuelto

**Caso.** Mujer de 74 años ingresada en planta por infección respiratoria. Constantes: FR 24 rpm, SpO₂ 92 % con gafas nasales a 2 L/min, temperatura 38,4 °C, TAS 105 mmHg, FC 112 lpm, paciente alerta.

| Parámetro | Valor | Puntos |
|---|---|---|
| FR | 24 | 2 |
| SpO₂ (escala 1) | 92 % | 2 |
| O₂ suplementario | Sí | 2 |
| Temperatura | 38,4 °C | 1 |
| TAS | 105 mmHg | 1 |
| FC | 112 lpm | 2 |
| Consciencia (ACVPU) | Alerta | 0 |
| **Total** | | **10** |

**NEWS2 = 10 → riesgo alto (≥ 7).**

**Actuación de enfermería:** iniciar **monitorización continua**, avisar de forma **urgente** al equipo médico y al equipo de críticos, comprobar la vía aérea y la oxigenación, obtener gasometría y cultivos según protocolo, revisar la medicación y las medidas de soporte, y **repetir el NEWS2** tras cada intervención. Registrar el total, la hora y las acciones realizadas.

## Relación con otras escalas

- **qSOFA:** puntuación pronóstica en sospecha de infección; no sustituye el sistema de cribado/respuesta ni debe usarse de forma aislada.
- **SOFA:** cuantifica la disfunción orgánica; se usa cuando el paciente requiere valoración de gravedad.
- **Glasgow y FOUR:** valoran la consciencia con más detalle cuando hay deterioro neurológico.
- **RASS y CAM-ICU:** valoran sedación y delirium en el paciente crítico.
- **NEMS:** mide la carga de trabajo de enfermería, no la gravedad.

## Puntos clave

- Escala de **alerta precoz** con **7 parámetros**; total **0-20**.
- **0** rutina; **1-4** bajo; **5-6** medio; **≥ 7** alto.
- **Un parámetro con 3** ya implica al menos riesgo medio.
- Usar la **escala 1 de SpO₂** por defecto y la **escala 2** solo en hipercapnia.
- El **oxígeno suplementario puntúa 2**; la **consciencia alterada (ACVPU) puntúa 3**.
- La **tendencia ascendente** es la señal de alarma más útil.
- Determina la **frecuencia de monitorización y a quién avisar**.
- No sustituye al **juicio clínico** ni a las escalas de gravedad específicas.

---

## Evidencia y referencias

- **Royal College of Physicians.** National Early Warning Score (NEWS) 2: standardising the assessment of acute-illness severity in the NHS. 2017.
- **Smith GB, et al.** The ability of the National Early Warning Score (NEWS) to discriminate patients at risk of early cardiac arrest, unanticipated intensive care unit admission, and death. *Resuscitation* 2013.
- **NICE.** Acutely ill adults in hospital: recognising and responding to deterioration. 2007 (actualización).

> Es una herramienta de alerta y respuesta, no un diagnóstico. Un NEWS2 alto exige valoración clínica urgente y escalado; no sustituye la impresión del equipo.

---

## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **NEWS2** | Deterioro y escalado |
| **qSOFA** | Cribado de sepsis |
| **Alertas clínicas** | Respuesta y aviso |
| **Constantes vitales** | Registro y tendencia |
