# Escala de Maddox (flebitis del catéter venoso periférico)

> 📖 **Fuentes:** Maddox RR, Rush DR, Rapp RP, Foster TS, Mazella V, McKean HE. *Double-blind study to investigate methods to prevent cephalothin-induced phlebitis.* Am J Hosp Pharm. 1977;34(1):29-34. · Lynn-McHale Wiegand DJ, ed. *AACN Procedure Manual for Critical Care.* 7th ed. Elsevier.

## Qué mide y para qué sirve

La **escala de Maddox** es una herramienta de **valoración visual** para **detectar y clasificar la flebitis** en el punto de inserción del **catéter venoso periférico** (`es_maddox_dialog_description`). Gradúa los signos locales de **0 a 5+** y, para cada grado, indica el **significado clínico** y la **actuación recomendada**. Una puntuación **≥ 2+ indica retirada del catéter** (`es_dialog_recommendation`).

Sirve para:

- **Detectar precozmente la flebitis** y evitar su progresión a tromboflebitis.
- **Estandarizar la valoración** del punto de inserción entre profesionales.
- **Indicar la retirada del catéter** en el momento adecuado.
- **Documentar y registrar** la incidencia de flebitis.
- **Evaluar la calidad del cuidado** de los accesos venosos periféricos.

## Población diana

- **Pacientes adultos y pediátricos con catéter venoso periférico** (vía periférica, catéter corto, midline según protocolo).
- Es aplicable **en cada turno** y siempre que se administren **fármacos irritantes**.
- También en pacientes con **accesos venosos de larga duración** (si el protocolo lo contempla) y en unidades de hospitalización, urgencias y críticos.
- **No se aplica** a catéteres venosos centrales ni a otros dispositivos (para ellos existen otras escalas).

## Cómo se puntúa

Instrucción de la app: *selecciona el grado observado en el punto de punción* (`es_select_observed_grade`). El resultado se muestra como `GRADO MADDOX` (`es_grade_maddox_label`) y con la actuación correspondiente (`es_action_label`).

| Grado | Título (app) | Signos (app) | Significado | Actuación |
|---|---|---|---|---|
| **0** | Sin signos (`es_grade_0_title`) | Sin dolor, eritema, hinchazón ni cordón palpable en la zona de punción (`es_grade_0_signs`) | No signos de flebitis (`es_grade_0_meaning`) | Observar el punto de inserción (`es_observe_insertion_site`) |
| **1+** | Posible signo (`es_grade_1_title`) | Zona de punción dolorosa o sensible al toque, sin eritema ni hinchazón (`es_grade_1_signs`) | Posible signo de flebitis (`es_grade_1_meaning`) | Observar el punto de inserción (`es_observe_insertion_site`) |
| **2+** | Inicio de flebitis (`es_grade_2_title`) | Dolor continuo en la zona de punción, sin eritema ni cordón palpable (`es_grade_2_signs`) | Inicio de flebitis (`es_grade_2_title`) | **Retirar el catéter** (`es_remove_catheter`) |
| **3+** | Etapa media (`es_grade_3_title`) | Dolor + eritema + hinchazón + endurecimiento o cordón venoso palpable **< 8 cm** por encima del punto de punción (`es_grade_3_signs`) | Etapa media de flebitis (`es_grade_3_meaning`) | Retirar el catéter y valorar tratamiento (`es_remove_catheter_assess_treatment`) |
| **4+** | Flebitis avanzada (`es_grade_4_title`) | Dolor + eritema + hinchazón + cordón venoso palpable **> 8 cm** por encima del punto de punción y/o purulencia (`es_grade_4_signs`) | Estado avanzado de flebitis (`es_grade_4_meaning`) | Retirar el catéter y valorar tratamiento (`es_remove_catheter_assess_treatment`) |
| **5+** | Tromboflebitis (`es_grade_5_title`) | Trombosis venosa franca con todos los signos anteriores y dificultad o detención de la perfusión (`es_grade_5_signs`) | Tromboflebitis (`es_grade_5_title`) | Retirar el catéter e iniciar tratamiento (`es_remove_catheter_start_treatment`) |

Resumen del diálogo de la app (`es_dialog_range_0` … `es_dialog_range_5`):

- 0 → Sin signos de flebitis
- 1+ → Posible signo. Observar
- 2+ → Inicio de flebitis. Retirar catéter
- 3+ → Etapa media. Retirar y valorar
- 4+ → Avanzada. Retirar y valorar
- 5+ → Tromboflebitis. Retirar e iniciar tratamiento

## Cómo explorar cada ítem (técnica)

1. **Inspección.** Con buena iluminación y guantes, **inspeccionar el punto de inserción** y el trayecto venoso: enrojecimiento, hinchazón, supuración, palidez o cordón visible.
2. **Palpación.** **Palpar suavemente** la zona y el trayecto venoso buscando **calor, induración, cordón palpable** y valorar la **extensión** del cordón respecto al punto de punción (< 8 cm o > 8 cm).
3. **Dolor.** **Preguntar al paciente** por el dolor o la sensibilidad en la zona (el grado 1+ y 2+ se definen por el dolor).
4. **Perfusión.** Comprobar la **velocidad de infusión** y la **permeabilidad** del catéter: la dificultad o detención de la perfusión es característica del grado 5+.
5. **Apósito y fijación.** Valorar el estado del apósito, la fijación y la presencia de fugas o humedad, aunque no formen parte del grado.
6. **Registro.** Documentar **fecha, hora y grado** en el registro de enfermería (`es_document_note`).

**Errores frecuentes:** no palpar el trayecto venoso; no preguntar por el dolor; no medir la extensión del cordón; retirar el catéter solo cuando hay signos avanzados; y no registrar el grado en cada turno.

## Puntuación total e interpretación

| Grado | Significado | Actuación de enfermería |
|---|---|---|
| **0** | Sin signos | Mantener la vigilancia en cada turno; no requiere actuación |
| **1+** | Posible signo | **Investigar la causa** (fármaco, flujo, fijación) y **aumentar la vigilancia**; valorar la retirada |
| **≥ 2+** | **Flebitis establecida** | **Retirar el catéter**, recanalizar en otra zona si es preciso, aplicar cuidados locales y **valorar tratamiento**; comunicar en 4+ y 5+ |
| **4+ / 5+** | Flebitis avanzada / tromboflebitis | Retirada inmediata, tratamiento, valorar **cultivo** si hay supuración y **comunicar al equipo médico** |

Se recomienda **evaluar el punto de inserción al menos una vez por turno** y **siempre que se administren fármacos irritantes** (`es_dialog_recommendation`). Debe **documentarse en el registro de enfermería** con **fecha, hora y grado de flebitis** (`es_document_note`), lo que permite calcular la incidencia y comparar la práctica.

## Validez

La escala de Maddox fue introducida por **Maddox et al. (Am J Hosp Pharm 1977)**, en el contexto de un ensayo sobre la prevención de la flebitis inducida por cefalotina, y se ha utilizado ampliamente en la práctica y en la investigación sobre **complicaciones de los accesos venosos periféricos**. Es una escala **descriptiva y visual**, sencilla de aplicar por enfermería.

Su **validación psicométrica formal es limitada** en comparación con otras escalas: se trata de una gradación clínica consensuada, con **variabilidad interobservador** en los grados intermedios. No se incluyen cifras concretas de sensibilidad, especificidad o AUC porque no están establecidas de forma robusta; para el detalle debe consultarse la publicación original y la literatura sobre escalas de flebitis.

## Limitaciones y errores frecuentes

- Es una escala **visual y subjetiva**: la valoración de los grados intermedios (1+ a 3+) puede variar entre profesionales.
- El grado 2+ se define **solo por dolor continuo**, sin eritema ni cordón: exige **preguntar activamente** al paciente por el dolor en la zona.
- No recoge de forma explícita la **extensión del eritema** ni el diámetro del cordón venoso más allá del punto de corte de 8 cm.
- No distingue entre causas **mecánicas, químicas o infecciosas** de la flebitis.
- Debe complementarse con las medidas de **prevención**: elección del catéter y de la vena, higiene de manos, antisepsia de la piel, fijación adecuada y retirada precoz.
- La **documentación** es imprescindible, pero a menudo incompleta, lo que infradestima la incidencia.
- Escala relacionada: **VIP** (`vip.md`), para el mismo problema con una gradación alternativa.

## Ejemplo práctico resuelto

**Caso.** Varón de 60 años con vía venosa periférica en el antebrazo para antibioterapia. En la valoración del turno la enfermera observa eritema y edema en el punto de punción, el paciente refiere dolor continuo y se palpa un cordón venoso indurado de unos 5 cm por encima del punto de punción, sin supuración ni fiebre.

**Clasificación: grado 3+ (etapa media de flebitis)** — dolor + eritema + hinchazón + cordón palpable < 8 cm.

**Actuación de enfermería:** **retirar el catéter**, aplicar los cuidados locales indicados (compresas frías o calor local según protocolo, antisepsia), recanalizar en otra zona si es preciso, **valorar el tratamiento** con el equipo médico, **documentar fecha, hora y grado**, y registrar el evento para el seguimiento de la incidencia de flebitis. Si en las horas siguientes apareciera fiebre o supuración, comunicarlo de inmediato y valorar cultivo.

## Relación con otras escalas

- **VIP (Visual Infusion Phlebitis):** gradación alternativa de la flebitis, con umbral de retirada en 2.
- **A-DIVA:** predice la dificultad de canalización antes de intentar el acceso.
- **Braden/EMINA:** comparten el objetivo de prevenir complicaciones cutáneas.
- **NEMS:** los cuidados de los accesos incrementan la carga de enfermería.
- **NEWS2:** la flebitis con repercusión sistémica (fiebre) puede elevar la puntuación de alerta.

## Registro y comunicación

- Documentar el resultado con **fecha y hora** y el profesional que lo valora.
- Registrar los **datos que alimentan la puntuación** (no solo el total) para poder recalcularla.
- Anotar las **intervenciones realizadas** y la respuesta obtenida.
- Incluir el resultado en el **traspaso entre turnos** y comunicar los cambios relevantes al equipo médico.
- Reevaluar de forma **seriada** y registrar la tendencia.

## Autoevaluación rápida

1. ¿Qué mide y en quién se aplica? → La **flebitis del catéter venoso periférico** (grados 0 a 5+).
2. ¿Cuál es su rango y su punto de corte? → **0 a 5+**; **≥ 2+** indica retirada del catéter.
3. ¿Qué hacer ante un resultado de riesgo (≥ 2+)? → **Retirar el catéter**, aplicar cuidados locales, valorar tratamiento y documentar fecha, hora y grado.

## Puntos clave

- Gradúa la **flebitis del catéter venoso periférico** de **0 a 5+**.
- **≥ 2+** es el **umbral de retirada** del catéter.
- El grado 2+ se define por **dolor continuo** sin eritema ni cordón.
- El cordón palpable **< 8 cm** separa el 3+ del 4+.
- El 5+ (tromboflebitis) puede acompañarse de **fiebre** y requiere tratamiento urgente.
- Valorar **en cada turno** y tras fármacos irritantes.
- **Palpar** el trayecto venoso, no solo inspeccionar.
- **Documentar fecha, hora y grado** en cada valoración.
---
## Evidencia y referencias

- **Maddox RR, et al.** Double-blind study to investigate methods to prevent cephalothin-induced phlebitis. *Am J Hosp Pharm* 1977;34:29-34.
- **Lynn-McHale Wiegand DJ, ed.** *AACN Procedure Manual for Critical Care*. 7th ed. Elsevier.
- **INS.** Infusion Therapy Standards of Practice (9.ª ed. 2024).

> Es una escala visual y subjetiva; estandariza la valoración, pero no sustituye la inspección del punto de inserción ni la retirada ante signos de flebitis.

---
## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **Escala de Maddox** | Flebitis del catéter periférico |
| **VIP score** | Alternativa visual |
| **Accesos vasculares** | Cuidados y retirada |
| **Flebitis** | Prevención y registro |
