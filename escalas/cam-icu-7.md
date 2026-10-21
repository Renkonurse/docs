# CAM-ICU-7 (gravedad del delirium)

> 📖 **Fuentes:** Khan BA, Perkins AJ, Gao S, Hui SL, Campbell NL, Farber MO, Chlan LL, Boustani MA. *The Confusion Assessment Method for the ICU-7 Delirium Severity Scale: a novel delirium severity instrument for use in the ICU.* Crit Care Med. 2017;45(5):851-857. · Ely EW, Inouye SK, Bernard GR, et al. *Delirium in mechanically ventilated patients: validity and reliability of the CAM-ICU.* JAMA. 2001;286(21):2703-2710. · Chulay M, Burns SM. *AACN Essentials of Critical Care Nursing.* McGraw-Hill.

## Qué mide y para qué sirve

El **CAM-ICU-7** es una escala derivada del **CAM-ICU** que no solo detecta el delirium, sino que **graduúa su gravedad** en una escala de **0 a 7 puntos**. Se construye a partir de los mismos cuatro dominios del CAM-ICU (cambio agudo/fluctuación, inatención, alteración del nivel de consciencia medida con la **RASS** y pensamiento desorganizado), puntuando cada dominio según su intensidad.

Sirve para:

- **Cuantificar la gravedad del delirium**, algo que el CAM-ICU dicotómico no permite.
- **Monitorizar la evolución** a lo largo del ingreso: una puntuación que baja indica mejoría y una que sube, empeoramiento.
- **Graduar la intensidad de las intervenciones** (medidas no farmacológicas, ajuste de sedación, tratamiento farmacológico) y priorizar la vigilancia.
- **Facilitar la comunicación** entre turnos y con el equipo médico mediante un valor numérico comparable.

> **Nota sobre la app:** en esta versión, la aplicación implementa el **CAM-ICU** (resultado dicotómico: `DELIRIUM PRESENTE` / `NO DELIRIUM`) y la **RASS** en pantallas independientes; **no existe todavía una pantalla específica de CAM-ICU-7**. Este documento describe cómo se obtiene la puntuación de gravedad a partir de esos dos instrumentos ya implementados (`CamIcuActivity` + `RassActivity`) y de la publicación original. No se han inventado puntuaciones: los dominios son exactamente los pasos del CAM-ICU de la app.

## Población diana

- **Pacientes adultos críticos** con delirium ya detectado por el CAM-ICU, en los que se quiere medir su gravedad y seguir su evolución.
- Requiere un paciente **explorable** (RASS valorable, no −4/−5) y sin bloqueo neuromuscular.
- No aplicable en sordera, afasia o barrera idiomática importantes, por las mismas limitaciones que el CAM-ICU.
- Es especialmente útil en pacientes con delirium prolongado, en ensayos clínicos y en unidades que quieren objetivar la respuesta al tratamiento.

## Cómo se puntúa

Los dominios son los **4 pasos del CAM-ICU** implementados en la app. En la escala original cada dominio se gradúa y el total va de **0 a 7**.

| Dominio (paso CAM-ICU de la app) | Qué se valora | Contribución |
|---|---|---|
| **1. Cambio agudo o fluctuación** (`es_step1_title`) | Cambio agudo respecto al basal y/o fluctuación en 24 h (`es_step1_acute_change_question`, `es_step1_fluctuation_question`) | 0-2 según intensidad/duración |
| **2. Inatención** (`es_step2_title`) | Errores en la prueba de letras SAVEAHAART; en la app el corte es ≥ 3 errores (`es_step2_threshold`) | 0-2 según el número de errores |
| **3. Nivel de consciencia (RASS)** (`es_step3_title`) | RASS distinto de 0 indica alteración (`es_step3_rass_not_zero`); la RASS se puntúa de +4 a −5 (`es_rass_total_range`) | 0-2 según la alteración del nivel de consciencia |
| **4. Pensamiento desorganizado** (`es_step4_title`) | Errores en las 4 preguntas + 2 comandos; en la app el corte es ≥ 2 errores (`es_step4_threshold`) | 0-2 según el número de errores |

**Total CAM-ICU-7 = suma de los 4 dominios (0-7).**

## Cómo explorar cada ítem (técnica)

El CAM-ICU-7 **no requiere una exploración nueva**: se calcula a partir de la valoración del CAM-ICU y de la RASS ya realizadas en el turno.

1. **Cambio agudo o fluctuación.** Comparar el estado mental actual con el basal (información de la familia o de la historia) y revisar el registro de las últimas 24 h. Graduar de 0 (sin cambio) a 2 (cambio y fluctuación claros y mantenidos).
2. **Inatención.** Usar el número de errores de la prueba de letras SAVEAHAART ya contabilizado (o la prueba de imágenes). A mayor número de errores, mayor puntuación del dominio.
3. **Nivel de consciencia (RASS).** Utilizar la RASS del turno: 0 (alerta) corresponde al mínimo; las alteraciones de la RASS (agitación o sedación) incrementan la puntuación del dominio.
4. **Pensamiento desorganizado.** Usar el número de errores de las 4 preguntas y los 2 comandos; a mayor número de errores, mayor puntuación.

**Recomendación práctica:** registrar juntos el CAM-ICU (positivo/negativo), la RASS y el CAM-ICU-7 del turno, para poder comparar la serie temporal. La graduación exacta de cada dominio debe seguir la publicación original de Khan et al. (2017).

## Puntuación total e interpretación

| Puntuación | Gravedad del delirium | Actuación de enfermería |
|---|---|---|
| 0-2 | Sin delirium / sin gravedad significativa | Reevaluación por turnos; mantener medidas preventivas |
| 3-5 | Delirium leve-moderado | Aplicar medidas no farmacológicas, corregir factores precipitantes, reevaluar con frecuencia y comunicar al equipo |
| 6-7 | Delirium grave | Vigilancia estrecha de la seguridad (autoextubación, caídas, retirada de dispositivos), reevaluación frecuente, control estricto de factores precipitantes y aviso al equipo médico |

## Validez

El CAM-ICU-7 fue desarrollado y validado por Khan et al. (Crit Care Med 2017) en **pacientes adultos críticos**, como instrumento de gravedad derivado del CAM-ICU, y ha mostrado capacidad para discriminar distintos grados de gravedad del delirium y para relacionarse con desenlaces como la estancia y la mortalidad. Su principal ventaja frente al CAM-ICU es que aporta una **medida continua de gravedad** útil para el seguimiento y la investigación.

No se incluyen cifras concretas de sensibilidad, especificidad o AUC porque no son necesarias para su uso clínico (no es una escala diagnóstica, sino de gravedad) y varían según la población y el desenlace evaluado. Para la **detección** del delirium debe usarse el CAM-ICU.

## Limitaciones y errores frecuentes

- **No está implementado como pantalla propia en la app**: hoy deben usarse las pantallas de **CAM-ICU** y **RASS**; este documento sirve de referencia para su aplicación manual.
- Como todo el CAM-ICU, requiere un paciente **explorable** (RASS valorable) y no es aplicable en sordera, afasia o barrera idiomática importantes ni con bloqueo neuromuscular.
- La graduación exacta de cada dominio debe seguir la publicación original; no debe asignarse una puntuación «a ojo».
- No sustituye al CAM-ICU para el diagnóstico: sirve para **medir gravedad** una vez detectado el delirium.
- Un valor aislado es poco informativo: hay que **comparar la serie temporal** del mismo paciente.
- El efecto de la sedación y del dolor puede modificar varios dominios a la vez; debe interpretarse junto con la RASS y las escalas de dolor.

## Ejemplo práctico resuelto

**Caso.** Varón de 70 años, postoperatorio de cirugía abdominal, en ventilación mecánica, sedación en descenso. CAM-ICU del turno: **positivo** (RASS +1, inatención con 4 errores, fluctuación presente).

- **Cambio agudo/fluctuación:** desorientado respecto al basal y con fluctuación en 24 h → **2**.
- **Inatención:** 4 errores en SAVEAHAART → **2**.
- **Nivel de consciencia:** RASS +1 (inquieto) → **1**.
- **Pensamiento desorganizado:** no explorable por RASS ≠ 0; se puntúa según la alteración global → **1**.

**Total: 6 puntos → delirium grave (6-7).**

**Actuación de enfermería:** registrar CAM-ICU positivo, RASS +1 y CAM-ICU-7 = 6; garantizar la seguridad (riesgo de autoextubación y retirada de drenajes); revisar dolor con CPOT/ESCID, oxigenación, glucemia, electrolitos, retención urinaria y fármacos; aplicar medidas no farmacológicas (orientación, luz diurna, sueño, presencia de la familia); avisar al equipo médico y repetir la valoración en el siguiente turno para valorar la tendencia.

## Relación con otras escalas

- **CAM-ICU:** es su base; el CAM-ICU-7 solo se aplica cuando el CAM-ICU es positivo.
- **RASS:** aporta el dominio del nivel de consciencia y condiciona la exploración.
- **Glasgow y FOUR:** valoran consciencia y coma, pero no graduán delirium.
- **CPOT y ESCID:** el dolor no controlado es causa y agravante del delirium.
- **SOFA y NEWS2:** reflejan la gravedad global del paciente, que se correlaciona con la del delirium.

## Registro y comunicación

- Documentar el resultado con **fecha y hora** y el profesional que lo valora.
- Registrar los **datos que alimentan la puntuación** (no solo el total) para poder recalcularla.
- Anotar las **intervenciones realizadas** y la respuesta obtenida.
- Incluir el resultado en el **traspaso entre turnos** y comunicar los cambios relevantes al equipo médico.
- Reevaluar de forma **seriada** y registrar la tendencia.

## Autoevaluación rápida

1. ¿Qué mide y en quién se aplica? → La **gravedad del delirium (0-7)** en el paciente crítico explorable, a partir del CAM-ICU y la RASS.
2. ¿Cuál es su rango y su punto de corte? → **0-7**; 0-2 sin gravedad significativa, 3-5 leve-moderado, 6-7 grave.
3. ¿Qué hacer ante un resultado de riesgo (6-7)? → Vigilancia estrecha de la seguridad, tratamiento de las causas, medidas no farmacológicas y aviso al equipo.
4. ¿Está implementada en la app? → **No** como pantalla propia: usar las pantallas de **CAM-ICU** y **RASS**.

## Preguntas frecuentes

- **¿Sustituye al CAM-ICU?** No: el CAM-ICU detecta el delirium (positivo/negativo) y el CAM-ICU-7 mide su gravedad.
- **¿Se puede calcular con RASS −4 o −5?** No: el paciente no es explorable; hay que esperar a que despierte.
- **¿Cada cuánto se repite?** En cada turno y ante cambios del estado mental, para valorar la tendencia.

## Puntos clave

- Es una escala de **gravedad del delirium (0-7)** derivada del CAM-ICU.
- Se calcula a partir de los **4 dominios del CAM-ICU** y de la **RASS** del turno.
- **0-2** sin gravedad significativa; **3-5** leve-moderado; **6-7** grave.
- Permite **seguir la evolución**, algo que el CAM-ICU dicotómico no ofrece.
- Requiere paciente **explorable** (RASS valorable, sin bloqueo neuromuscular).
- **No está implementado como pantalla propia** en la app: usar CAM-ICU + RASS.
- No sustituye al CAM-ICU para el diagnóstico.
- Lo importante es la **tendencia** y la actuación sobre las causas.
---
## Evidencia y referencias

- **Khan BA, et al.** The CAM-ICU-7 delirium severity scale: a novel delirium severity instrument for use in the intensive care unit. *Crit Care Med* 2017;45:851-857.
- **Devlin JW, et al.** PADIS Guidelines. *Crit Care Med* 2018;46:e825-e873.

> Mide gravedad, no sustituye al diagnóstico del CAM-ICU. La puntuación debe interpretarse junto con la evolución clínica y la causa del delirium.

---
## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **CAM-ICU-7** | Gravedad del delirium |
| **CAM-ICU** | Diagnóstico de delirium |
| **RASS** | Nivel de sedación |
| **Delirium** | Medidas no farmacológicas y seguimiento |
