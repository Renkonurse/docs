# Escala RASS (Richmond Agitation-Sedation Scale)

> 📖 **Fuentes:** Sessler CN, Gosnell MS, Grap MJ, et al. *The Richmond Agitation-Sedation Scale: validity and reliability in adult intensive care unit patients.* Am J Respir Crit Care Med. 2002;166(10):1338-1344. · Devlin JW, Skrobik Y, Gélinas C, et al. *PADIS Clinical Practice Guidelines.* Crit Care Med. 2018;46(9):e825-e873. · Chulay M, Burns SM. *AACN Essentials of Critical Care Nursing.* McGraw-Hill.

## Qué mide y para qué sirve

La **RASS (Richmond Agitation-Sedation Scale)** valora de forma simultánea el **nivel de agitación y el nivel de sedación** del paciente crítico. Es una escala **observacional y verbal** de **10 niveles**, que va de **+4 (combatividad)** a **−5 (no despertable)**, con el **0 (alerta y calmado)** como punto neutro.

Sirve para:

- **Fijar y alcanzar el objetivo de sedación** prescrito, comparando la puntuación real con la diana.
- **Ajustar la sedoanalgesia** de forma protocolizada (sedación ligera frente a profunda).
- **Valorar el nivel de consciencia antes de aplicar el CAM-ICU**: el paso 3 del CAM-ICU utiliza directamente la RASS, y una RASS distinta de 0 se considera alteración del nivel de consciencia.
- **Detectar agitación** y prevenir eventos adversos (autoextubación, retirada de catéteres, caídas, lucha con el ventilador).
- **Comunicar** el estado de sedación entre turnos junto con las dosis de fármacos administradas.

En la app se presenta como una lista de 10 opciones con su etiqueta y su descripción completa (`es_rass_label_*` y `es_rass_desc_*`), más el resultado `PUNTUACIÓN RASS` (`es_rass_score_label`) y el rango `es_rass_total_range` (+4 a −5).

## Población diana

- **Pacientes adultos críticos** con sedoanalgesia, ventilación mecánica o riesgo de agitación: UCI médica, quirúrgica, cardiológica, neurológica y de trauma.
- Pacientes **no sedados** en los que se quiere objetivar el nivel de alerta y la presencia de agitación o somnolencia.
- Es la escala de referencia para el **protocolo de sedación mínima** y para la valoración del delirium.
- **No es interpretable** en el paciente con **bloqueo neuromuscular** ni en el paciente con sordera o barrera idiomática importante para los niveles que dependen de la respuesta verbal.

## Cómo se puntúa

Se selecciona **una única opción**, de +4 a −5, con la descripción clínica tal como aparece en la app.

| Puntos | Nivel | Descripción (cadena de la app) |
|---|---|---|
| **+4** | Combatividad | Violento, peligro para el personal (`es_rass_desc_4_combative`) |
| **+3** | Muy agitado | Retira tubos, catéteres o drenajes; agresivo (`es_rass_desc_3_very_agitated`) |
| **+2** | Agitado | Movimientos frecuentes sin propósito, lucha con el respirador (`es_rass_desc_2_agitated`) |
| **+1** | Inquieto | Ansioso pero sin movimientos agresivos ni vigorosos (`es_rass_desc_1_restless`) |
| **0** | Alerta y calmado | Estado normal, colaborador (`es_rass_desc_0_alert_calm`) |
| **−1** | Somnoliento | No está plenamente alerta, pero se mantiene despierto > 10 s (`es_rass_desc_minus1_drowsy`) |
| **−2** | Sedación ligera | Se despierta brevemente (< 10 s) al contacto visual o voz (`es_rass_desc_minus2_light_sedation`) |
| **−3** | Sedación moderada | Movimiento o apertura ocular a la voz, sin contacto visual (`es_rass_desc_minus3_moderate_sedation`) |
| **−4** | Sedación profunda | Sin respuesta a la voz, movimientos o apertura ocular al estímulo físico (`es_rass_desc_minus4_deep_sedation`) |
| **−5** | No despertable | Sin respuesta a la voz ni al estímulo físico (`es_rass_desc_minus5_unresponsive`) |

## Cómo explorar cada ítem (técnica)

La app recuerda la secuencia estándar de exploración (`es_how_to_assess`). La valoración se realiza **en tres escalones**, deteniéndose en cuanto se obtiene respuesta:

1. **Observar al paciente sin estimular** (`es_rass_step1_observe`). Si está calmado y colaborador → **0**; si presenta agitación, graduarla entre **+1 y +4** según la descripción de cada nivel.
2. Si no responde, **llamar por su nombre y pedir que abra los ojos** (`es_rass_step2_call_name`). Si se mantiene despierto más de 10 segundos → **−1**; si se despierta brevemente (< 10 s) con contacto visual → **−2**; si solo hay movimiento o apertura ocular sin contacto visual → **−3**.
3. Si no responde, **estimular físicamente** (sacudir el hombro, presión esternal) (`es_rass_step3_physical`). Si hay respuesta al estímulo físico → **−4**; si no hay ninguna respuesta → **−5**.

**Recomendaciones de técnica:** valorar al paciente **antes** de administrar analgesia o sedación de rescate, para no enmascarar el estado real; hacerlo con el paciente en reposo y sin manipulación reciente; usar siempre los mismos estímulos; y **registrar la puntuación junto con la dosis de sedantes y analgesia del turno** (`es_rass_record_with_doses`).

**Errores frecuentes:** estimular físicamente de entrada en lugar de empezar por la observación; no diferenciar −1 de −2 (el criterio es el tiempo de atención: > 10 s o < 10 s); puntuar −3 cuando hay contacto visual; confundir la agitación por dolor, hipoxia, retención urinaria o delirium con una agitación que requiere más sedación.

## Puntuación total e interpretación

| Rango | Grupo | Etiqueta de la app | Actuación de enfermería |
|---|---|---|---|
| +1 a +4 | Agitación | `es_agitation` | Buscar causa (dolor, hipoxia, retención, delirium, fármacos); garantizar seguridad; ajustar sedoanalgesia según protocolo; avisar si +3/+4 |
| 0 | Alerta y calmado | `es_alert_and_calm` | Objetivo en muchos pacientes; mantener y reevaluar por turnos |
| −1 a −2 | Sedación ligera | `es_light_sedation` | Objetivo habitual; mantener sedación mínima y favorecer la interacción |
| −3 | Sedación moderada | `es_moderate_sedation` | Revisar objetivo prescrito; valorar reducir si no hay indicación |
| −4 | Sedación profunda | `es_deep_sedation` | Verificar indicación (SDRA grave, hipertensión intracraneal, relajación); no aplicable el CAM-ICU |
| −5 | No despertable | `es_not_arousable` | Reevaluar necesidad de sedación y descartar causas orgánicas; registrar y comunicar |

**Objetivo habitual en UCI:** entre **−1 y −3** según la sedación objetivo (`es_rass_icu_target`). En la mayoría de los pacientes se busca una **sedación ligera** (RASS 0 a −2); los niveles −4/−5 se reservan para indicaciones concretas (SDRA grave, hipertensión intracraneal, relajación muscular, etc.).

## Validez

La RASS fue desarrollada y validada por Sessler et al. (Am J Respir Crit Care Med 2002) en **pacientes adultos ingresados en UCI médica, quirúrgica, cardiológica y neurológica**. El estudio mostró una **excelente fiabilidad interobservador** y una buena correlación con otras escalas de sedación y con el nivel de consciencia, tanto en pacientes sedados como no sedados.

Está **recomendada por las guías PADIS (2018)** como herramienta de referencia para valorar y monitorizar la sedación y para aplicar el CAM-ICU, y es una de las escalas más utilizadas en los protocolos de sedación mínima. No se incluyen cifras exactas de sensibilidad o especificidad porque la RASS no es una escala diagnóstica, sino de graduación del estado de sedación.

## Limitaciones y errores frecuentes

- En **bloqueo neuromuscular** la escala no es interpretable.
- Debe valorarse **antes** de administrar analgesia/sedación de rescate, para no enmascarar el estado real.
- En pacientes con **afasia, barrera idiomática o sordera**, la interpretación de los niveles positivos puede verse dificultada.
- La **sedación profunda (RASS −4/−5)** impide aplicar el CAM-ICU; hay que reevaluar cuando el paciente despierte.
- La agitación **no siempre es indicación de más sedación**: hay que descartar dolor, hipoxia, hipercapnia, retención urinaria, delirium, abstinencia y mal ajuste del ventilador.
- La valoración debe repetirse **cada turno** y siempre que cambie la perfusión de sedantes o analgesia; registrar la puntuación junto con las dosis es imprescindible para interpretarla.
- Un único valor es poco informativo si no se conoce el **objetivo prescrito** y la tendencia.

## Ejemplo práctico resuelto

**Caso.** Varón de 63 años, SDRA moderado en ventilación mecánica, con perfusión de propofol y remifentanilo. El objetivo prescrito es RASS −1 a −2.

- A la **observación** no está agitado, pero permanece con los ojos cerrados.
- Al **llamarle por su nombre** abre los ojos y mantiene contacto visual durante unos 4-5 segundos, para volver a cerrarlos.
- Puntuación: **RASS −2 (sedación ligera)**.

**Actuación de enfermería:** registrar RASS −2 junto con las dosis de propofol y remifentanilo del turno, comprobar que está dentro del objetivo prescrito (sí, −1 a −2), mantener la sedación mínima eficaz, valorar el dolor con una escala observacional (CPOT/ESCID) y, como el paciente está en RASS −2 y despierta brevemente, **aplicar el CAM-ICU** en cuanto sea posible. Vigilar la tolerancia al ventilador y comunicar cualquier cambio mantenido fuera del objetivo.

## Relación con otras escalas

- **CAM-ICU:** el paso 3 utiliza la RASS; RASS ≠ 0 indica alteración del nivel de consciencia.
- **Glasgow y FOUR:** miden consciencia y coma; la RASS es más adecuada para graduar la sedación.
- **CPOT y ESCID:** valoran el dolor de forma observacional; deben aplicarse antes de atribuir la agitación a la sedación.
- **PADIS:** recomienda protocolos de sedación ligera guiados por RASS, junto con la valoración del dolor y del delirium.
- **News2 / SOFA:** la alteración del estado mental también forma parte de estas escalas de gravedad.

## Registro y comunicación

- Documentar el resultado con **fecha y hora** y el profesional que lo valora.
- Registrar los **datos que alimentan la puntuación** (no solo el total) para poder recalcularla.
- Anotar las **intervenciones realizadas** y la respuesta obtenida.
- Incluir el resultado en el **traspaso entre turnos** y comunicar los cambios relevantes al equipo médico.
- Reevaluar de forma **seriada** y registrar la tendencia.

## Autoevaluación rápida

1. ¿Qué mide y en quién se aplica? → El **nivel de agitación y sedación** del paciente crítico, de **+4 a −5**.
2. ¿Cuál es su rango y su punto de corte? → Objetivo habitual en UCI **entre −1 y −3** (sedación ligera).
3. ¿Qué hacer ante un resultado de riesgo? → Buscar causa de la agitación antes de sedar más; con RASS −4/−5 no se puede aplicar el CAM-ICU.

## Puntos clave

- Gradúa **agitación y sedación** en 10 niveles, de **+4 a −5**, con el **0** como neutro.
- Se explora en **tres escalones**: observar → voz → estímulo físico.
- **Objetivo habitual: RASS −1 a −3**, con sedación ligera siempre que sea posible.
- **RASS ≠ 0** es criterio de alteración de consciencia en el **CAM-ICU**.
- **RASS −4/−5** impide aplicar el CAM-ICU.
- Valorar **antes** del rescate de sedoanalgesia y registrar con las dosis del turno.
- La agitación obliga a **buscar causa** antes de aumentar la sedación.
- No es interpretable con **bloqueo neuromuscular**.
