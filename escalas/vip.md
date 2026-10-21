# VIP · Visual Infusion Phlebitis Score (flebitis por infusión)

> 📖 **Fuentes:** Jackson A. *Visual Infusion Phlebitis Score (VIP).* NHS; 1998. · Lynn-McHale Wiegand DJ, ed. *AACN Procedure Manual for Critical Care.* 7th ed. Elsevier.

## Qué mide y para qué sirve

El **índice VIP** (*Visual Infusion Phlebitis*) valora de **0 a 5** el estado del **punto de inserción del catéter venoso periférico** y orienta la **actuación de enfermería** en cada grado (`es_vip_dialog_description`). Es una escala **observacional y visual** que permite **detectar y graduar la flebitis** y decidir el momento de retirada del catéter.

> **Importante:** en la app, «VIP» corresponde a **Visual Infusion Phlebitis** (flebitis por infusión) y **no** a «ventilator-induced pneumonia».

Sirve para:

- **Detectar precozmente la flebitis** y evitar su progresión.
- **Estandarizar la valoración** del punto de inserción.
- **Indicar la retirada del catéter** de forma protocolizada.
- **Documentar la incidencia** de flebitis y evaluar la calidad del cuidado.
- **Formar y comunicar** al equipo sobre el estado de los accesos.

Instrucción de la app (`es_vip_description`): *valora el punto de inserción del catéter venoso periférico. Cada grado indica los signos que hay que buscar y la actuación recomendada.* El resultado se muestra como `GRADO VIP` (`es_vip_grade_label`) y los signos como `Signos: %1$s` (`es_vip_signs_label`).

## Población diana

- **Pacientes con catéter venoso periférico** (vía periférica corta, midline según protocolo), tanto adultos como pediátricos.
- Es aplicable **en cada turno** y siempre que se administren **fármacos irritantes**.
- Se utiliza en hospitalización, urgencias, quirófano y unidades de críticos.
- **No se aplica** a catéteres venosos centrales ni a otros dispositivos.

## Cómo se puntúa

Se selecciona **un único grado (0-5)** según los signos observados.

| Grado | Título (app) | Signos (app) | Actuación (app) |
|---|---|---|---|
| **0** | Sitio sano (`es_vip_grade_0_title`) | Sin signos de flebitis (`es_vip_grade_0_signs`) | No requiere actuación. Mantener la vigilancia en cada turno (`es_vip_grade_0_action`) |
| **1** | Posibles primeros signos (`es_vip_grade_1_title`) | Dolor leve en el punto de inserción o enrojecimiento leve (`es_vip_grade_1_signs`) | Investigar la causa y aumentar la vigilancia. Valorar si procede retirar el catéter (`es_vip_grade_1_action`) |
| **2** | Flebitis precoz (`es_vip_grade_2_title`) | Dos de estos signos: dolor en el punto, eritema o edema (`es_vip_grade_2_signs`) | **RETIRAR el catéter y recanalizar en otra zona** (`es_vip_grade_2_action`) |
| **3** | Flebitis media (`es_vip_grade_3_title`) | Dolor a lo largo del trayecto de la vía, eritema e induración (`es_vip_grade_3_signs`) | Retirar el catéter y considerar tratamiento (`es_vip_grade_3_action`) |
| **4** | Flebitis avanzada o tromboflebitis precoz (`es_vip_grade_4_title`) | Signos del grado 3 más cordón venoso palpable, con signos extensos (`es_vip_grade_4_signs`) | Retirar el catéter y tratar (`es_vip_grade_4_action`) |
| **5** | Tromboflebitis avanzada (`es_vip_grade_5_title`) | Signos del grado 4 más fiebre, con signos extensos (`es_vip_grade_5_signs`) | Retirada del catéter y tratamiento urgentes (`es_vip_grade_5_action`) |

Resumen del diálogo de la app (`es_vip_dialog_range_0` … `es_vip_dialog_range_5`):

- 0 → Sitio sano. Mantener la vigilancia
- 1 → Posibles primeros signos. Investigar y vigilar
- 2 → Flebitis precoz. Retirar el catéter
- 3 → Flebitis media. Retirar y considerar tratamiento
- 4 → Flebitis avanzada. Retirar y tratar
- 5 → Tromboflebitis avanzada. Retirada y tratamiento urgentes

## Cómo explorar cada ítem (técnica)

1. **Inspección.** Con buena iluminación y guantes, **inspeccionar el punto de inserción y el trayecto venoso**: enrojecimiento, edema, induración, cordón visible o supuración.
2. **Palpación.** **Palpar suavemente** la zona y el trayecto para detectar **calor, edema, induración o cordón venoso palpable**.
3. **Dolor.** **Preguntar al paciente** por el dolor en el punto de inserción y a lo largo del trayecto (los grados 1-3 se definen en parte por el dolor).
4. **Perfusión y permeabilidad.** Comprobar la velocidad de infusión y si hay dificultad o detención del flujo.
5. **Apósito y fijación.** Valorar el estado del apósito, la fijación y la presencia de humedad o fugas.
6. **Signos sistémicos.** En el grado 5 comprobar la **temperatura** y el estado general (fiebre).
7. **Registro.** Documentar el grado, la fecha y la hora, y las medidas aplicadas.

**Errores frecuentes:** no palpar el trayecto venoso; no preguntar por el dolor; retirar el catéter solo con signos avanzados; no registrar el grado; y no reevaluar tras la retirada o el cambio de catéter.

## Puntuación total e interpretación

**A partir de 2 puntos se considera flebitis: es el umbral de retirada del catéter** (`es_vip_threshold_note`). Se recomienda **evaluar el punto de inserción en cada turno** y siempre que se administren fármacos irritantes (`es_vip_dialog_recommendation`).

| Grado | Interpretación | Actuación de enfermería |
|---|---|---|
| **0** | Sitio sano | Mantener la vigilancia en cada turno |
| **1** | Posibles primeros signos | **Investigar la causa** (fármaco irritante, flujo, fijación, movilización) y **aumentar la vigilancia**; valorar la retirada |
| **2** | **Flebitis precoz** | **Retirar el catéter** y recanalizar en otra zona |
| **3** | Flebitis media | Retirar el catéter y **considerar tratamiento** |
| **4** | Flebitis avanzada / tromboflebitis precoz | Retirar el catéter y **tratar**; comunicar al equipo médico |
| **5** | Tromboflebitis avanzada | **Retirada y tratamiento urgentes**; valorar cultivo si hay supuración y comunicar |

La gradación seriada permite **comparar la evolución** y evaluar la calidad del cuidado de los accesos; debe registrarse cada valoración en la historia de enfermería.

## Validez

El **Visual Infusion Phlebitis Score** fue descrito por **Jackson A (1998)** en el ámbito del **NHS** y es una de las escalas de valoración de flebitis **más utilizadas en el Reino Unido y en otros países**, incorporada a numerosos protocolos de cuidado de accesos venosos periféricos. Su fortaleza es la **sencillez y la claridad de la actuación asociada a cada grado**.

Su **validación psicométrica formal es limitada**: se trata de una escala clínica consensuada, con variabilidad interobservador en los grados intermedios. No se incluyen cifras concretas de sensibilidad, especificidad o AUC porque no están establecidas de forma robusta; para el detalle debe consultarse la publicación original y la literatura sobre escalas de flebitis.

## Limitaciones y errores frecuentes

- Es una escala **visual y subjetiva**; conviene consensuar en el equipo los criterios de cada grado.
- El grado 2 exige **dos signos** entre dolor, eritema y edema: hay que **explorar y palpar** el punto de inserción, no solo mirarlo.
- No recoge la **extensión exacta** del eritema ni la longitud del cordón venoso (a diferencia de la escala de **Maddox**, que usa el corte de 8 cm).
- No distingue entre causas **mecánicas, químicas o infecciosas**.
- Debe complementarse con las **medidas de prevención**: higiene de manos, antisepsia de la piel, fijación adecuada, elección de la vena y del catéter y retirada precoz.
- La **documentación** incompleta infradestima la incidencia de flebitis.
- Escala relacionada: **Maddox** (`maddox.md`), para el mismo problema con otra gradación.

## Ejemplo práctico resuelto

**Caso.** Mujer de 55 años con vía venosa periférica en el dorso de la mano para perfusión de un antibiótico irritante. En la valoración del turno presenta **dolor en el punto de inserción y edema**, sin eritema ni cordón palpable.

**Clasificación: grado 2 (flebitis precoz)** — dos signos (dolor + edema).

**Actuación de enfermería:** **retirar el catéter** y recanalizar en otra zona (preferiblemente una vena de mayor calibre y en otro punto), aplicar los cuidados locales según protocolo, **documentar el grado, la fecha y la hora**, registrar el fármaco administrado y valorar con el equipo médico si precisa tratamiento. Revaluar el nuevo acceso en cada turno y considerar medidas preventivas (dilución del fármaco, velocidad de infusión, fijación adecuada).

## Relación con otras escalas

- **Maddox:** gradación alternativa de la flebitis.
- **A-DIVA:** predice la dificultad de canalización antes del acceso.
- **Braden/EMINA:** prevención de complicaciones cutáneas.
- **NEMS:** los cuidados de los accesos incrementan la carga de enfermería.
- **NEWS2:** la flebitis con fiebre puede elevar la puntuación de alerta.

## Registro y comunicación

- Documentar el resultado con **fecha y hora** y el profesional que lo valora.
- Registrar los **datos que alimentan la puntuación** (no solo el total) para poder recalcularla.
- Anotar las **intervenciones realizadas** y la respuesta obtenida.
- Incluir el resultado en el **traspaso entre turnos** y comunicar los cambios relevantes al equipo médico.
- Reevaluar de forma **seriada** y registrar la tendencia.

## Autoevaluación rápida

1. ¿Qué mide y en quién se aplica? → La **flebitis del catéter venoso periférico** (grados 0 a 5).
2. ¿Cuál es su rango y su punto de corte? → **0-5**; **≥ 2** indica flebitis y retirada del catéter.
3. ¿Qué hacer ante un resultado de riesgo (≥ 2)? → **Retirar el catéter**, recanalizar, tratar y documentar el grado con fecha y hora.

## Puntos clave

- Valora la **flebitis del catéter venoso periférico** de **0 a 5**.
- **≥ 2 puntos = flebitis** y **umbral de retirada** del catéter.
- El grado 2 requiere **dos signos** (dolor, eritema o edema).
- El grado 5 (tromboflebitis con fiebre) exige **actuación urgente**.
- Valorar **en cada turno** y tras fármacos irritantes.
- **Inspeccionar y palpar** el punto de inserción y el trayecto.
- **Documentar** el grado en cada valoración.
- Complementar con medidas de **prevención** y retirada precoz.
---
## Evidencia y referencias

- **Jackson A.** Visual Infusion Phlebitis Score (VIP). NHS; 1998.
- **Gallant P, Schultz AA.** Evaluation of a visual infusion phlebitis scale for determining appropriate discontinuation of peripheral intravenous catheters. *J Infus Nurs* 2006;29:338-345.
- **INS.** Infusion Therapy Standards of Practice (9.ª ed. 2024).

> La escala es visual; un VIP ≥ 2 indica retirada del catéter según el protocolo. Debe registrarse en cada turno y siempre ante dolor, eritema o induración.

---
## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **VIP score** | Flebitis por infusión |
| **Maddox** | Alternativa visual |
| **Accesos vasculares** | Cuidados y retirada |
| **Flebitis** | Prevención y registro |
