# CFS · Clinical Frailty Scale (Escala de fragilidad clínica)

> 📖 **Fuentes:** Rockwood K, Song X, MacKnight C, et al. *A global clinical measure of fitness and frailty in elderly people.* CMAJ. 2005;173(5):489-495. · MSD Manual Professional: https://www.msdmanuals.com/professional

## Qué mide y para qué sirve

La **Clinical Frailty Scale (CFS)** es una escala clínica **ordinal de 1 a 9** que describe el **estado funcional basal** del paciente, es decir, su grado de fragilidad **en las 2 semanas previas a la enfermedad aguda** (`f2_cfs_instruccion`, `f2_cfs_subtitulo`). No mide la gravedad de la enfermedad actual, sino la **reserva funcional** con la que el paciente llega a la UCI.

Se basa en la **descripción clínica global** (movilidad, actividades instrumentales y básicas de la vida diaria, síntomas, comorbilidad y cognición), no en un sumatorio de ítems. **La puntuación es directamente el nivel elegido (1-9).**

Sirve para:

- **Estimar la reserva funcional** y el pronóstico del paciente crítico.
- **Contextualizar las decisiones** de intensidad terapéutica y de ingreso en UCI, junto con el equipo y la familia.
- **Planificar el alta** y los recursos necesarios (rehabilitación, ayuda domiciliaria, residencia).
- **Comparar poblaciones** y ajustar por fragilidad en investigación.

## Población diana

- **Pacientes adultos mayores** (habitualmente ≥ 65 años) ingresados en UCI, urgencias o planta.
- Pacientes con **enfermedad crónica avanzada** en los que interesa conocer la reserva funcional previa.
- Es útil en cualquier paciente en el que se planteen decisiones de intensidad terapéutica.
- En **pacientes sin informador fiable** (sin familia, sin historia clínica) la estimación pierde precisión.

## Cómo se puntúa

Se selecciona **un único nivel (1-9)** entre los que muestra la app (`nivelesCfs`):

| Nivel | Descripción completa (cadena de la app) |
|---|---|
| **1** | 💪 1 · **Muy en forma**: activo, enérgico y motivado; hace ejercicio regularmente (`f2_cfs_nivel_1`) |
| **2** | 🏃 2 · **En forma**: hace ejercicio ocasional o es activo de forma estacional (`f2_cfs_nivel_2`) |
| **3** | 🚶 3 · **Se maneja bien**: problemas médicos controlados, activo pero sin ejercicio vigoroso (`f2_cfs_nivel_3`) |
| **4** | ⚠️ 4 · **Vulnerable**: no depende de otros, pero los síntomas limitan las actividades (`f2_cfs_nivel_4`) |
| **5** | 🧓 5 · **Ligeramente frágil**: dependencia limitada para actividades instrumentales avanzadas (`f2_cfs_nivel_5`) |
| **6** | 🦯 6 · **Moderadamente frágil**: necesita ayuda para actividades instrumentales y para salir (`f2_cfs_nivel_6`) |
| **7** | 🦽 7 · **Gravemente frágil**: dependiente para las actividades básicas de la vida diaria (`f2_cfs_nivel_7`) |
| **8** | 🛏️ 8 · **Muy gravemente frágil**: totalmente dependiente, se acerca al final de la vida (`f2_cfs_nivel_8`) |
| **9** | 🕊️ 9 · **Enfermo terminal**: esperanza de vida inferior a 6 meses (`f2_cfs_nivel_9`) |

Rango válido: **1 a 9** (`CfsLogica.MINIMO` = 1, `CfsLogica.MAXIMO` = 9).

## Cómo explorar cada ítem (técnica)

La CFS **no se explora ítem a ítem en el paciente agudo**: se reconstruye el estado funcional de las **2 semanas previas** a la enfermedad actual.

1. **Fuentes de información.** Preguntar a la **familia o cuidador principal**, revisar la **historia clínica** (informes de atención primaria, altas previas, valoraciones sociales) y, si el paciente está orientado, completar con su propia versión.
2. **Áreas que hay que reconstruir:**
   - **Movilidad:** si sale de casa, si camina solo, si usa bastón/andador/silla de ruedas.
   - **Actividades instrumentales (AIVD):** compras, cocina, teléfono, medicación, manejo del dinero, uso del transporte.
   - **Actividades básicas (ABVD):** baño, vestido, alimentación, continencia, uso del retrete, transferencias.
   - **Síntomas y comorbilidad:** disnea, angina, dolor, fatiga que limitan la actividad.
   - **Cognición:** quejas de memoria, desorientación, diagnóstico de demencia.
3. **Graduación.** 1-3 = no frágil (desde muy en forma hasta «se maneja bien»); 4 = vulnerable (síntomas limitan); 5-6 = fragilidad leve-moderada (dependencia instrumental); 7-8 = fragilidad grave (dependencia para ABVD); 9 = enfermedad terminal.

**Errores frecuentes:** valorar el estado **actual** (enfermedad aguda, sedación, delirium) en lugar del basal; dejarse influir por la impresión de gravedad de la UCI; no preguntar a la familia; y confundir fragilidad con comorbilidad (un paciente con muchas enfermedades pero funcionalmente independiente puede tener CFS bajo).

## Puntuación total e interpretación

La app agrupa el nivel en bandas de significado clínico (`CfsLogica.banda`) y muestra la interpretación correspondiente:

| Nivel CFS | Banda | Interpretación (cadena de la app) | Actuación de enfermería |
|---|---|---|---|
| 1-3 | No frágil | No frágil (CFS 1–3) (`f2_cfs_interpretacion_1`) | Cuidados habituales; movilización precoz y prevención estándar |
| 4 | Vulnerable | Vulnerable (CFS 4) (`f2_cfs_interpretacion_2`) | Vigilar la pérdida funcional; movilización y soporte nutricional |
| 5-6 | Fragilidad leve-moderada | Fragilidad leve-moderada (CFS 5–6) (`f2_cfs_interpretacion_3`) | Plan de cuidados con prevención de caídas y UPP, rehabilitación y coordinación al alta |
| 7-8 | Fragilidad grave | Fragilidad grave (CFS 7–8) (`f2_cfs_interpretacion_4`) | Cuidados de dependencia, prevención de complicaciones, valorar objetivos terapéuticos con el equipo |
| 9 | Enfermo terminal | Enfermo terminal (CFS 9) (`f2_cfs_interpretacion_5`) | Cuidados paliativos y confort; revisar la adecuación del esfuerzo terapéutico |

El resultado se muestra como `CFS %1$d` (`f2_cfs_resultado`) junto con la banda.

## Validez

La CFS fue desarrollada y validada por Rockwood et al. (CMAJ 2005) en la cohorte del **Canadian Study of Health and Aging (CSHA)**, una amplia población de personas mayores, y desde entonces se ha validado en múltiples entornos, incluidos **urgencias, hospitalización y UCI**. Se ha relacionado de forma consistente con la **mortalidad, el deterioro funcional y el uso de recursos**; en el paciente crítico, una CFS elevada se asocia a peor pronóstico funcional y vital.

No se incluyen cifras concretas de sensibilidad, especificidad o AUC porque varían según la población, el punto de corte y el desenlace evaluado. La CFS es una escala **clínica y semisubjetiva**, con buena correlación con otras medidas de fragilidad.

## Limitaciones y errores frecuentes

- Requiere información fiable sobre el **estado funcional previo** (cuidador, familia, historia clínica); en pacientes sin informador la estimación es menos fiable.
- Es una escala **clínica y subjetiva**: dos valoradores pueden diferir en los niveles intermedios (especialmente 3-5).
- **No debe valorarse en el momento agudo** sin referirse a las 2 semanas previas.
- No sustituye a otras escalas geriátricas (**Barthel** para actividades básicas, escalas de deterioro cognitivo) sino que las complementa.
- No recoge directamente la **comorbilidad** (para ello, el índice de **Charlson**) ni la gravedad aguda (**SOFA**, **NEWS2**).
- En la app, la CFS se registra como nivel único, sin suma de puntos.

## Ejemplo práctico resuelto

**Caso.** Mujer de 84 años, ingresada por neumonía grave. La hija refiere que vivía sola, salía a la compra con un bastón, se cocinaba y se administraba la medicación, aunque desde hacía unos meses necesitaba ayuda para las tareas más pesadas y para salir de casa. No tenía demencia conocida y se vestía y aseaba sola.

- Dependencia **instrumental** (compra pesada, salir) pero **independiente para ABVD** → **CFS 6 (moderadamente frágil)**.

**Actuación de enfermería:** registrar CFS 6 en el ingreso, orientar el plan de cuidados hacia la prevención de caídas y UPP, movilización precoz, valoración nutricional y del riesgo de delirium, y coordinar con trabajo social la ayuda domiciliaria al alta. En las decisiones de intensidad terapéutica, la fragilidad moderada (CFS 6) aporta información pronóstica relevante que debe compartirse con el equipo y la familia.

## Relación con otras escalas

- **Barthel:** mide la independencia en las actividades básicas; complementa a la CFS (que valora además las instrumentales y la cognición).
- **Charlson:** cuantifica la comorbilidad; una CFS alta puede coexistir con un Charlson bajo y viceversa.
- **MRC Sum Score:** valora la debilidad adquirida en UCI, que agrava la fragilidad previa.
- **NUTRIC/mNUTRIC:** el riesgo nutricional se relaciona con la fragilidad y el pronóstico.
- **rSOFA/News2:** reflejan la gravedad aguda, no el estado basal.

## Registro y comunicación

- Documentar el resultado con **fecha y hora** y el profesional que lo valora.
- Registrar los **datos que alimentan la puntuación** (no solo el total) para poder recalcularla.
- Anotar las **intervenciones realizadas** y la respuesta obtenida.
- Incluir el resultado en el **traspaso entre turnos** y comunicar los cambios relevantes al equipo médico.
- Reevaluar de forma **seriada** y registrar la tendencia.

## Autoevaluación rápida

1. ¿Qué mide y en quién se aplica? → La **fragilidad basal (1-9)** en las 2 semanas previas a la enfermedad aguda.
2. ¿Cuál es su rango y su punto de corte? → **1-3** no frágil; **4** vulnerable; **5-6** fragilidad leve-moderada; **7-8** grave; **9** terminal.
3. ¿Qué hacer ante un resultado de riesgo (≥ 7)? → Plan de cuidados de dependencia, prevención de complicaciones y revisión de los objetivos terapéuticos con el equipo.

## Puntos clave

- Mide **fragilidad basal** (2 semanas previas) en una escala de **1 a 9**.
- **1-3** no frágil; **4** vulnerable; **5-6** fragilidad leve-moderada; **7-8** grave; **9** terminal.
- Es **clínica y global**: movilidad, AIVD, ABVD, síntomas y cognición.
- **No se valora en el momento agudo**: hay que reconstruir el estado previo.
- Requiere información de la **familia o la historia clínica**.
- Se asocia a **mortalidad y peor recuperación funcional** en el paciente crítico.
- Ayuda en las **decisiones compartidas** de intensidad terapéutica y en la planificación del alta.
- En la app se registra como **nivel único**, sin suma de puntos.
