# TIMI Risk Score (síndrome coronario agudo sin elevación del ST · UA/NSTEMI)

> 📖 **Fuentes:** Antman EM, Cohen M, Bernink PJLM, et al. *The TIMI risk score for unstable angina/non-ST elevation MI: a method for prognostication and therapeutic decision making.* JAMA. 2000;284(7):835-842. · SEEIUC: https://www.seeiuc.org

## Qué mide y para qué sirve

El **TIMI Risk Score** estratifica el **riesgo de eventos cardiovasculares** en pacientes con **síndrome coronario agudo sin elevación del ST (angina inestable / IAMSEST)**. Se compone de **7 criterios** que puntúan **1 punto cada uno**, con un total de **0 a 7**. A mayor puntuación, mayor riesgo de eventos a 14 días y **mayor beneficio de una estrategia invasiva precoz** y de tratamiento antitrombótico intensivo (`es_beneficio_estrategia`).

Sirve para:

- **Estratificar el riesgo** de muerte, infarto o revascularización urgente a corto plazo (14 días).
- **Decidir la estrategia de tratamiento**: invasiva precoz (< 24 h) frente a conservadora.
- **Ajustar la intensidad del tratamiento antitrombótico**.
- **Decidir el nivel de vigilancia** y el destino del paciente (unidad coronaria, UCI).
- **Estandarizar la comunicación** del riesgo entre profesionales.

## Población diana

- **Pacientes adultos con síndrome coronario agudo sin elevación del ST** (angina inestable o IAMSEST).
- Se calcula con los datos de las **primeras horas del ingreso**.
- **No es aplicable al STEMI**, que tiene su propio TIMI Risk Score con criterios distintos (`es_nota_stemi`).
- No está diseñado para el **dolor torácico no coronario** ni para el SCA de otras causas.

## Cómo se puntúa

Instrucción de la app (`es_marca_criterios`): *marca los criterios presentes (1 punto cada uno)*. El resultado se muestra como `PUNTUACIÓN TIMI` `%1$d / 7` (`es_puntuacion_timi`, `es_puntuacion_timi_valor`).

| # | Criterio (1 punto cada uno) | Detalle en la app |
|---|---|---|
| 1 | **Edad ≥ 65 años** (`es_criterio_edad_65`) | `es_punto_1` (1 punto) |
| 2 | **≥ 3 factores de riesgo coronario** (`es_criterio_factores_riesgo`) | HTA, DM, dislipemia, tabaquismo, historia familiar (`es_detalle_factores_riesgo`) |
| 3 | **Coronariopatía conocida** (`es_criterio_coronariopatia`) | Estenosis ≥ 50 % en cateterismo previo (`es_detalle_coronariopatia`) |
| 4 | **AAS en los últimos 7 días** (`es_criterio_aas`) | Uso previo de ácido acetilsalicílico (`es_detalle_aas`) |
| 5 | **Angina severa reciente** (`es_criterio_angina`) | ≥ 2 episodios en las últimas 24 h (`es_detalle_angina`) |
| 6 | **Marcadores de necrosis elevados** (`es_criterio_marcadores`) | Troponina o CK-MB elevadas (`es_detalle_marcadores`) |
| 7 | **Desviación del ST ≥ 0,5 mm** (`es_criterio_desviacion_st`) | En el ECG de ingreso (`es_detalle_desviacion_st`) |

### Total

| Concepto | Valor |
|---|---|
| Mínimo | 0 |
| Máximo | 7 |
| Puntuación | 1 punto por criterio (`es_puntuacion_total`) |

## Cómo explorar cada ítem (técnica)

1. **Edad.** Comprobar en la historia clínica; el corte es **≥ 65 años**.
2. **Factores de riesgo coronario.** Recoger **HTA, diabetes, dislipemia, tabaquismo e historia familiar** de cardiopatía isquémica; el criterio se cumple con **≥ 3**.
3. **Coronariopatía conocida.** Revisar informes de cateterismo previo (estenosis ≥ 50 %) o antecedentes de revascularización.
4. **AAS en los últimos 7 días.** Preguntar por la **medicación habitual** (incluida la autoadministración) y revisar la historia farmacológica.
5. **Angina severa reciente.** Cuantificar los **episodios de angina en las últimas 24 h**; ≥ 2 cumple el criterio.
6. **Marcadores de necrosis.** Revisar la **troponina o CK-MB** del ingreso: si están elevadas, el criterio se cumple (IAMSEST).
7. **Desviación del ST.** Revisar el **ECG de ingreso**: desviación ≥ 0,5 mm (elevación o descenso) cumple el criterio.

**Errores frecuentes:** no confirmar el antecedente de AAS; confundir factores de riesgo aislados con el criterio de «≥ 3»; usar el TIMI de UA/NSTEMI en un STEMI; y no recalcular cuando la troponina se eleva en las horas siguientes.

## Puntuación total e interpretación

| Puntos | Riesgo | Eventos a 14 días (app) | Actuación de enfermería |
|---|---|---|---|
| **0-1** | `Riesgo BAJO` (`es_timi_riesgo_bajo`) | ≈ 4,7 % (`es_eventos_14d_bajo`) | Vigilancia estándar, monitorización ECG y control de síntomas |
| **2** | `Riesgo INTERMEDIO` (`es_riesgo_intermedio`) | ≈ 8,3 % (`es_eventos_14d_intermedio`) | Vigilancia estrecha; asegurar el tratamiento antitrombótico; comunicar al equipo |
| **3-4** | `Riesgo ALTO` (`es_timi_riesgo_alto`) | ≈ 13,2 – 19,9 % (`es_eventos_14d_alto`) | **Estrategia invasiva precoz** según protocolo; vigilancia intensiva y control de signos de sangrado |
| **5-7** | `Riesgo MUY ALTO` (`es_timi_riesgo_muy_alto`) | ≈ 26,2 – 40,9 % (`es_eventos_14d_muy_alto`) | **Máxima vigilancia**, estrategia invasiva urgente y tratamiento antitrombótico intensivo; monitorización continua |

Debe registrarse el resultado y comunicarse al equipo médico, especialmente en puntuaciones **≥ 3**. La vigilancia de enfermería en estos pacientes incluye **dolor torácico, cambios del ECG, signos de sangrado** (por el tratamiento antitrombótico) y monitorización hemodinámica.

## Validez

El TIMI Risk Score para **UA/NSTEMI** fue desarrollado y validado por **Antman et al. (JAMA 2000)** en las cohortes de los ensayos **TIMI 11B** y **ESSENCE**, en pacientes con angina inestable o IAMSEST. La puntuación mostró una **relación graduada y consistente** entre el número de criterios y la incidencia de eventos (muerte, infarto o revascularización urgente) a los 14 días, desde en torno al **4,7 %** en las puntuaciones más bajas hasta en torno al **40,9 %** en las más altas, tal como refleja la app.

Su utilidad para **identificar a los pacientes que más se benefician de una estrategia invasiva precoz** ha sido confirmada en múltiples registros y estudios posteriores. No se incluyen cifras de sensibilidad o especificidad porque es una escala pronóstica, no diagnóstica. Las cifras de eventos proceden de las cohortes de validación originales y pueden variar con el tratamiento actual.

## Limitaciones y errores frecuentes

- **Este score es para UA/NSTEMI**; para el **STEMI** existe un TIMI Risk Score específico con criterios distintos (`es_nota_stemi`).
- La puntuación debe calcularse con los datos del **ingreso**; algunos criterios (troponina) pueden modificarse en las primeras horas y requerir recalcular.
- No incorpora otros factores pronósticos (insuficiencia renal, edad muy avanzada, comorbilidad, fragilidad), que deben considerarse clínicamente.
- **No mide el riesgo hemorrágico**, que es clave para decidir la intensidad del tratamiento antitrombótico.
- Complementa, pero no sustituye, a la valoración clínica y a la clasificación de **Killip** (`killip.md`) en el SCA.
- La definición de «≥ 3 factores de riesgo» puede dar lugar a variabilidad si no se aplican criterios homogéneos.

## Ejemplo práctico resuelto

**Caso.** Mujer de 72 años con dolor torácico en reposo, dos episodios en las últimas 24 h. Antecedentes: HTA, diabetes y dislipemia (3 factores de riesgo); toma AAS habitualmente; ECG de ingreso con descenso del ST de 1 mm; troponina elevada. Sin cateterismo previo conocido.

| Criterio | ¿Presente? |
|---|---|
| Edad ≥ 65 años | Sí |
| ≥ 3 factores de riesgo | Sí |
| Coronariopatía conocida | No |
| AAS en los últimos 7 días | Sí |
| Angina severa reciente (≥ 2 episodios/24 h) | Sí |
| Marcadores de necrosis elevados | Sí |
| Desviación del ST ≥ 0,5 mm | Sí |
| **Total** | **6 / 7** |

**Riesgo MUY ALTO (5-7), con ≈ 26,2-40,9 % de eventos a 14 días.**

**Actuación de enfermería:** monitorización ECG continua y hemodinámica, asegurar el tratamiento antitrombótico prescrito, vigilar **signos de sangrado** (hematomas, sangrado de encías, melenas, hematuria, déficit neurológico), control del dolor y de las constantes, preparar al paciente para la **estrategia invasiva urgente**, mantener ayuno si procede y registrar el score con su desglose.

## Relación con otras escalas

- **Killip:** clasifica la insuficiencia cardiaca en el IAM; complementa al TIMI en el SCA.
- **SOFA:** valora la disfunción orgánica en el paciente crítico.
- **NEWS2:** alerta precoz de deterioro global.
- **NEMS:** la estrategia invasiva y la monitorización incrementan la carga de enfermería.
- **Glasgow:** útil si hay complicaciones neurológicas (ictus asociado, hipoperfusión).

## Puntos clave

- Estratifica el **riesgo en UA/NSTEMI** con **7 criterios** de **1 punto** cada uno.
- **0-1** bajo; **2** intermedio; **3-4** alto; **5-7** muy alto.
- Los eventos a 14 días **aumentan de forma graduada** con la puntuación.
- A mayor puntuación, **mayor beneficio de estrategia invasiva precoz**.
- Se calcula con los **datos del ingreso**; recalcular si cambia la troponina.
- **No es aplicable al STEMI** (tiene su propio score).
- No mide el **riesgo hemorrágico**.
- Complementa a **Killip** y a la valoración clínica.
---
## Evidencia y referencias

- **Antman EM, et al.** The TIMI risk score for unstable angina/non-ST elevation MI. *JAMA* 2000;284:835-842.
- **Ibanez B, et al.** 2017 ESC Guidelines for the management of acute myocardial infarction in patients presenting with ST-segment elevation. *Eur Heart J* 2018.
- **Collet JP, et al.** 2020 ESC Guidelines for the management of acute coronary syndromes in patients presenting without persistent ST-segment elevation. *Eur Heart J* 2021.

> El TIMI clásico se aplica a UA/NSTEMI; no es el mismo que el TIMI de STEMI. Complementa a Killip y a la valoración hemodinámica.

---
## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **TIMI Risk Score** | Riesgo en SCA sin ST |
| **Killip** | Gravedad hemodinámica |
| **SCA** | Estratificación y tratamiento |
| **Hemodinámica** | Shock y perfusión |
