---
layout: default
title: "Clasificación de Killip (infarto agudo de miocardio)"
---
# Clasificación de Killip (infarto agudo de miocardio)

> 📖 **Fuentes:** Killip T, Kimball JT. *Treatment of myocardial infarction in a coronary care unit: a two year experience with 250 patients.* Am J Cardiol. 1967;20(4):457-464. · SEEIUC: https://www.seeiuc.org

## Qué mide y para qué sirve

La **clasificación de Killip** estratifica la **gravedad del infarto agudo de miocardio (IAM)** según los **signos de insuficiencia cardiaca** presentes en la exploración. Es una escala **categórica de 4 clases (I-IV)** —no un sumatorio de puntos— y es un **predictor independiente de mortalidad intrahospitalaria** (`es_killip_dialog_note`).

Sirve para:

- **Estratificar la gravedad** del IAM desde el ingreso.
- **Orientar la intensidad del tratamiento** y el nivel de vigilancia (planta, unidad coronaria, UCI).
- **Estimar el pronóstico** intrahospitalario.
- **Guiar el manejo de la insuficiencia cardiaca** asociada (fluidos, diuréticos, vasodilatadores, soporte respiratorio).
- **Estandarizar la comunicación** del estado hemodinámico del paciente con SCA.

## Población diana

- **Pacientes con infarto agudo de miocardio** (con o sin elevación del ST) en las **primeras horas** de evolución.
- Pacientes ingresados en **unidad coronaria o UCI** con sospecha de IAM y signos de insuficiencia cardiaca.
- Es aplicable a la mayoría de los adultos con IAM.
- **No es directamente extrapolable** a otras formas de insuficiencia cardiaca (crónica descompensada, miocardiopatías) ni a otros síndromes coronarios sin infarto.

## Cómo se puntúa

Se elige **una sola clase** según los criterios clínicos. La app usa las etiquetas `CLASE KILLIP` (`es_killip_class_label`) y `es_killip_dialog_subtitle`.

| Clase | Título (app) | Criterios clínicos (app) | Mortalidad aproximada (app) |
|---|---|---|---|
| **I** | Sin insuficiencia cardíaca (`es_killip_class1_title`) | No crepitantes, no S3, no ingurgitación yugular. Perfusión periférica conservada (`es_killip_class1_criteria`) | ≈ 6 % (`es_killip_class1_mortality`) |
| **II** | Insuficiencia cardíaca leve (`es_killip_class2_title`) | Crepitantes en bases pulmonares, S3, ingurgitación yugular. Sin edema agudo (`es_killip_class2_criteria`) | ≈ 17 % (`es_killip_class2_mortality`) |
| **III** | Edema agudo de pulmón (`es_killip_class3_title`) | Crepitantes en más de la mitad de los campos pulmonares. Ortopnea, disnea intensa (`es_killip_class3_criteria`) | ≈ 38 % (`es_killip_class3_mortality`) |
| **IV** | Shock cardiogénico (`es_killip_class4_title`) | TAS < 90 mmHg, oliguria, piel fría y sudorosa, alteración del estado mental (`es_killip_class4_criteria`) | ≈ 81 % (`es_killip_class4_mortality`) |

Resumen del diálogo de la app (`es_killip_dialog_class1` … `es_killip_dialog_class4`):

- Clase I → Sin IC
- Clase II → IC leve (crepitantes bases, S3, IY)
- Clase III → Edema agudo de pulmón
- Clase IV → Shock cardiogénico

## Cómo explorar cada ítem (técnica)

La clase Killip se determina con **exploración clínica**, no con ítems puntuables:

1. **Auscultación pulmonar.** Buscar **crepitantes**: ausentes (I), en bases (II), en más de la mitad de los campos (III). Valorar también la presencia de ortopnea y disnea.
2. **Auscultación cardiaca.** Buscar el **tercer ruido (S3)**, signo de sobrecarga de volumen.
3. **Inspección yugular.** Valorar la **ingurgitación yugular** (a 45°), indicador de presión venosa elevada.
4. **Perfusión periférica.** Comprobar **piel fría y sudorosa, livideces, relleno capilar enlentecido** y pulsos periféricos.
5. **Tensión arterial.** Medir la **TAS**: < 90 mmHg en la clase IV.
6. **Diuresis.** Vigilar la **oliguria** (< 0,5 mL/kg/h) como signo de hipoperfusión renal.
7. **Estado mental.** Valorar la **alteración del estado mental** (confusión, agitación, somnolencia) por hipoperfusión cerebral.

**Errores frecuentes:** clasificar sin auscultar los campos pulmonares completos; no buscar la ingurgitación yugular; atribuir la hipotensión a otras causas sin valorar el gasto cardiaco; y no reevaluar la clase cuando cambia el estado clínico.

## Interpretación y actuación de enfermería

| Clase | Gravedad | Implicación y actuación de enfermería |
|---|---|---|
| I | Sin IC | Buen pronóstico; tratamiento estándar del IAM y vigilancia; monitorización ECG continua y control de constantes |
| II | IC leve | Vigilancia estrecha, control de fluidos, balance hídrico y diuresis; administrar tratamiento de la IC según protocolo; avisar si empeora |
| III | Edema agudo de pulmón | Situación grave; soporte respiratorio (oxigenoterapia, VNI según indicación), diuréticos y vasodilatadores según protocolo; posición semisentada y vigilancia estrecha |
| IV | Shock cardiogénico | Máxima gravedad; soporte hemodinámico (vasopresores/inotrópicos), valorar revascularización urgente y soporte circulatorio; monitorización invasiva; **aviso inmediato al equipo** |

La app recuerda que **la clase se determina en las primeras horas del IAM y puede evolucionar** (`es_killip_result_note`): un paciente puede pasar de clase I a clase III en pocas horas, por lo que debe reevaluarse. La monitorización incluye constantes, diuresis horaria, saturación, ECG y vigilancia de signos de shock; la clase Killip forma parte de la **información de traspaso** entre turnos.

## Validez

La clasificación de Killip fue descrita por **Killip y Kimball (Am J Cardiol 1967)** en una serie de **250 pacientes ingresados en una unidad coronaria** por infarto agudo de miocardio, y demostró una **clara relación entre la clase clínica y la mortalidad intrahospitalaria**. Desde entonces se ha validado en múltiples cohortes y registros de SCA, y sigue siendo un **predictor independiente de mortalidad** ampliamente utilizado.

Las cifras de mortalidad aproximada por clase que muestra la app proceden de esta escala y de series clásicas; deben interpretarse como orientativas, ya que la mortalidad actual ha descendido con la reperfusión y el tratamiento moderno. No se incluyen cifras de sensibilidad o especificidad porque no es una prueba diagnóstica, sino una clasificación clínica de gravedad.

## Limitaciones y errores frecuentes

- Es una clasificación **clínica**, con **variabilidad entre observadores** (sobre todo entre clase I y II).
- No recoge la **fracción de eyección** ni otros parámetros ecocardiográficos, que aportan información pronóstica adicional.
- Se aplica al **IAM**; en otros contextos (insuficiencia cardiaca crónica, otros síndromes) la clasificación no es directamente extrapolable.
- La clase puede **cambiar rápidamente**, por lo que una clasificación aislada al ingreso puede quedar obsoleta.
- No sustituye a otras escalas de riesgo del SCA como el **TIMI** (`timi.md`).
- En pacientes con **enfermedad pulmonar crónica** los crepitantes pueden estar presentes sin insuficiencia cardiaca, lo que sobreestima la clase.

## Ejemplo práctico resuelto

**Caso.** Varón de 68 años con dolor torácico de 2 horas; ECG con elevación del ST anterior. A la exploración: crepitantes en ambas bases, ingurgitación yugular, S3 audible, TAS 105 mmHg, diuresis conservada, consciente y orientado.

**Clasificación: Killip II (insuficiencia cardiaca leve, sin edema agudo).**

**Actuación de enfermería:** monitorización ECG continua, constantes y diuresis horaria, control de la oxigenación, posición semisentada, administración del tratamiento antiisquémico y de la insuficiencia cardiaca según protocolo, vigilancia de signos de empeoramiento (aumento de crepitantes, desaturación, hipotensión, oliguria) y preparación para la revascularización urgente. Registrar la clase y reevaluarla tras la reperfusión.

## Relación con otras escalas

- **TIMI:** estratifica el riesgo isquémico y hemorrágico en el SCA; complementa a Killip.
- **SOFA:** valora la disfunción orgánica, incluida la cardiovascular.
- **NEWS2:** alerta precoz de deterioro global.
- **Glasgow:** la alteración del estado mental en Killip IV puede cuantificarse con el Glasgow.
- **NEMS:** la clase III-IV incrementa la carga de cuidados de enfermería.

## Registro y comunicación

- Documentar el resultado con **fecha y hora** y el profesional que lo valora.
- Registrar los **datos que alimentan la puntuación** (no solo el total) para poder recalcularla.
- Anotar las **intervenciones realizadas** y la respuesta obtenida.
- Incluir el resultado en el **traspaso entre turnos** y comunicar los cambios relevantes al equipo médico.
- Reevaluar de forma **seriada** y registrar la tendencia.

## Autoevaluación rápida

1. ¿Qué mide y en quién se aplica? → La **gravedad del IAM** según los signos de insuficiencia cardiaca, en las primeras horas.
2. ¿Cuál es su rango y su punto de corte? → **4 clases (I-IV)**; la gravedad y la mortalidad aumentan de I a IV.
3. ¿Qué hacer ante un resultado de riesgo (III-IV)? → **Activación inmediata** del equipo, soporte respiratorio/hemodinámico y reevaluación continua.

## Puntos clave

- Estratifica la **gravedad del IAM** en **4 clases** según los signos de insuficiencia cardiaca.
- **I** sin IC; **II** IC leve; **III** edema agudo de pulmón; **IV** shock cardiogénico.
- La mortalidad **aumenta progresivamente** con la clase (orientativa).
- Se determina **al ingreso** y **puede evolucionar**: reevaluar.
- La exploración incluye **auscultación, ingurgitación yugular, TAS, diuresis y estado mental**.
- **Clase III-IV**: activación inmediata del equipo y de los recursos de críticos.
- Tiene **variabilidad interobservador** (sobre todo I-II).
- Complementa al **TIMI** y a las escalas de gravedad general.

---

## Evidencia y referencias

- **Killip T, Kimball JT.** Treatment of myocardial infarction in a coronary care unit: a two year experience with 250 patients. *Am J Cardiol* 1967;20:457-464.
- **Ibanez B, et al.** 2017 ESC Guidelines for the management of acute myocardial infarction in patients presenting with ST-segment elevation. *Eur Heart J* 2018;39:119-177.
- **Authors/Task Force Members.** ESC Guidelines on acute coronary syndromes.

> La clasificación es bedside y tiene variabilidad interobservador; complementa al TIMI y a la valoración hemodinámica. No sustituye la estratificación moderna del SCA.

---

## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **Killip** | Gravedad del SCA |
| **TIMI** | Riesgo isquémico |
| **Shock cardiogénico** | Reconocimiento y soporte |
| **Hemodinámica** | Presión, gasto y perfusión |
