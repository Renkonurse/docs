# Índice de comorbilidad de Charlson

> 📖 **Fuentes:** Charlson ME, Pompei P, Ales KL, MacKenzie CR. *A new method of classifying prognostic comorbidity in longitudinal studies: development and validation.* J Chronic Dis. 1987;40(5):373-383. · MSD Manual Professional: https://www.msdmanuals.com/professional

## Qué mide y para qué sirve

El **índice de Charlson** cuantifica la **comorbilidad** del paciente y estima su **riesgo de mortalidad a largo plazo** (`f2_charlson_subtitulo`: «Comorbilidad + edad · mortalidad a 10 años»). Se compone de **19 condiciones** con pesos de **1, 2, 3 o 6 puntos** según su impacto pronóstico, más una **puntuación por edad** (1 punto por cada década a partir de los 50 años). La **puntuación total = suma de los pesos de las comorbilidades + puntos por edad**.

Sirve para:

- **Estratificar el riesgo basal** del paciente y ajustar el pronóstico más allá de la enfermedad aguda.
- **Comparar poblaciones** y ajustar por comorbilidad en investigación y en gestión clínica.
- **Orientar la planificación de cuidados** y las decisiones compartidas sobre intensidad terapéutica.
- **Estimar el consumo de recursos** y la necesidad de seguimiento al alta.

## Población diana

- **Pacientes adultos hospitalizados**, especialmente en medicina interna, urgencias, oncología y UCI.
- Es útil en pacientes **crónicos complejos** y en los que se plantean decisiones de intensidad terapéutica o de derivación.
- Su uso en **poblaciones pediátricas** requiere adaptaciones específicas (no es la versión de la app).
- Requiere una **historia clínica fiable**: sin antecedentes documentados la puntuación se infraestima.

## Cómo se puntúa

Instrucción de la app: *marca las comorbilidades presentes e introduce la edad* (`f2_charlson_instruccion`). Se marca cada condición presente y se pulsa `CALCULAR` (`f2_charlson_calcular`); el resultado se muestra como `CHARLSON %1$d` (`f2_charlson_total`).

### Comorbilidades (1 punto)

| Puntos | Condición | Cadena en la app |
|---|---|---|
| 1 | Infarto agudo de miocardio | `f2_charlson_c01` |
| 1 | Insuficiencia cardíaca congestiva | `f2_charlson_c02` |
| 1 | Enfermedad vascular periférica | `f2_charlson_c03` |
| 1 | Enfermedad cerebrovascular (sin hemiplejía) | `f2_charlson_c04` |
| 1 | Demencia | `f2_charlson_c05` |
| 1 | EPOC | `f2_charlson_c06` |
| 1 | Enfermedad del tejido conectivo | `f2_charlson_c07` |
| 1 | Úlcera péptica | `f2_charlson_c08` |
| 1 | Hepatopatía leve | `f2_charlson_c09` |
| 1 | Diabetes sin afectación de órgano diana | `f2_charlson_c10` |

### Comorbilidades (2 puntos)

| Puntos | Condición | Cadena en la app |
|---|---|---|
| 2 | Hemiplejía | `f2_charlson_c11` |
| 2 | Insuficiencia renal moderada-grave | `f2_charlson_c12` |
| 2 | Diabetes con afectación de órgano diana | `f2_charlson_c13` |
| 2 | Tumor sólido sin metástasis | `f2_charlson_c14` |
| 2 | Leucemia | `f2_charlson_c15` |
| 2 | Linfoma | `f2_charlson_c16` |

### Comorbilidades (3 y 6 puntos)

| Puntos | Condición | Cadena en la app |
|---|---|---|
| 3 | Hepatopatía moderada-grave | `f2_charlson_c17` |
| 6 | Tumor sólido metastásico | `f2_charlson_c18` |
| 6 | SIDA (no solo VIH) | `f2_charlson_c19` |

### Puntos por edad

La app añade **1 punto por cada década desde los 50 años** (`puntosEdad`), y muestra el desglose `Edad: +%1$d` (`f2_charlson_edad_puntos`).

| Edad (años) | Puntos |
|---|---|
| < 50 | 0 |
| 50-59 | 1 |
| 60-69 | 2 |
| 70-79 | 3 |
| 80-89 | 4 |
| ≥ 90 | 5 |

### Total

| Concepto | Valor |
|---|---|
| Fórmula | suma de pesos de comorbilidades + puntos por edad |
| Mínimo | 0 |
| Máximo | 37 (pesos de las 19 condiciones) + 5 (edad) = 42 |
| Registro en la app | `CHARLSON %1$d` (`f2_charlson_total`) |

El botón `f2_charlson_limpiar` (`LIMPIAR`) reinicia la selección y la edad.

## Cómo explorar cada ítem (técnica)

El índice **no se explora a pie de cama**: se construye a partir de la **historia clínica** y de la información del paciente y la familia.

1. **Recogida de antecedentes.** Revisar informes de altas previas, historia de atención primaria, lista de problemas y medicación habitual (los fármacos orientan sobre la enfermedad: insulinas, inhaladores, anticoagulantes, antineoplásicos).
2. **Verificación de cada condición.** Comprobar que el diagnóstico está **documentado** y no solo sospechado; evitar duplicar la misma enfermedad con dos ítems (p. ej., enfermedad cerebrovascular y hemiplejía pueden coexistir, pero deben documentarse por separado).
3. **Puntos de atención por condición:**
   - **IAM:** antecedente de infarto documentado (no angina).
   - **ICC:** diagnóstico clínico o ecocardiográfico.
   - **Enfermedad vascular periférica:** claudicación, bypass, amputación por isquemia.
   - **Enfermedad cerebrovascular:** ictus o AIT previos, sin hemiplejía residual.
   - **Demencia:** diagnóstico establecido o deterioro cognitivo significativo.
   - **EPOC:** enfermedad pulmonar obstructiva crónica documentada.
   - **Enfermedad del tejido conectivo:** lupus, esclerosis sistémica, artritis reumatoide, polimiositis.
   - **Úlcera péptica:** antecedente documentado.
   - **Hepatopatía:** leve (sin hipertensión portal) frente a moderada-grave.
   - **Diabetes:** sin afectación de órgano diana (1) frente a con afectación (2).
   - **Insuficiencia renal moderada-grave:** creatinina elevada, diálisis o trasplante.
   - **Tumores:** sólido sin metástasis (2), metastásico (6); leucemia (2), linfoma (2).
   - **SIDA:** no basta con la infección por VIH.
4. **Edad.** Introducir la edad real del paciente; la app calcula automáticamente los puntos por década.

**Errores frecuentes:** marcar diagnósticos sin confirmación; olvidar la edad; confundir hepatopatía leve con moderada-grave; no diferenciar diabetes con o sin afectación de órgano diana; y no actualizar el índice cuando aparecen nuevos diagnósticos.

## Puntuación total e interpretación

| Total | Riesgo | Etiqueta de la app | Actuación de enfermería |
|---|---|---|---|
| **0** | Riesgo bajo | `f2_charlson_bajo` | Cuidados habituales; prevención estándar |
| **1-2** | Riesgo moderado | `f2_charlson_moderado` | Vigilar complicaciones; refuerzo de educación y adherencia |
| **3-4** | Riesgo alto | `f2_charlson_alto` | Plan de cuidados individualizado; coordinar seguimiento al alta; revisar polifarmacia |
| **≥ 5** | Riesgo muy alto | `f2_charlson_muy_alto` | Valorar intensidad terapéutica con el equipo; planificación de cuidados avanzados y soporte social |

## Validez

El índice de Charlson fue desarrollado y validado por Charlson et al. (J Chronic Dis 1987) en **pacientes médicos hospitalizados**, con seguimiento a 1 y 10 años, y demostró ser un **predictor independiente de mortalidad**. Desde entonces se ha validado en múltiples poblaciones y enfermedades, y se han propuesto adaptaciones (p. ej., el índice de Quan y las versiones con códigos ICD) y variantes que incorporan la edad.

No se incluyen cifras concretas de sensibilidad, especificidad o AUC porque varían según la población y el desenlace. Es una medida de **comorbilidad y pronóstico a largo plazo**, no de gravedad aguda.

## Limitaciones y errores frecuentes

- Se basa en la **presencia/ausencia de diagnósticos**, sin ponderar su gravedad ni su control actual.
- No recoge la **fragilidad ni el estado funcional**, que aportan información pronóstica adicional (usar **CFS**, `cfs.md`, o **Barthel**, `barthel.md`).
- La cumplimentación depende de la **calidad de la historia clínica**; la infradocumentación reduce la puntuación.
- Se diseñó para estudios **longitudinales** (mortalidad a 1-10 años); no es una escala de gravedad aguda como **SOFA** (`sofa.md`) o **APACHE II**.
- Existen **versiones actualizadas** del índice con otras condiciones y pesos; la app implementa la lista de 19 condiciones con pesos 1/2/3/6 y edad.
- No debe usarse **solo** para decisiones de limitación terapéutica: es un dato más junto con la fragilidad, la función y los deseos del paciente.

## Ejemplo práctico resuelto

**Caso.** Varón de 76 años, ingresado por descompensación de insuficiencia cardíaca.

- **Comorbilidades documentadas:** insuficiencia cardíaca congestiva (1), EPOC (1), diabetes con afectación de órgano diana (2) e ictus previo sin hemiplejía (1) → **5 puntos**.
- **Edad:** 76 años → **3 puntos**.
- **Total: 5 + 3 = 8 puntos** → **riesgo muy alto (≥ 5)**.

**Actuación de enfermería:** registrar el índice y su desglose, reforzar la educación sobre la insuficiencia cardíaca (peso diario, signos de alarma, adherencia), revisar la **polifarmacia** y las interacciones, coordinar el seguimiento con atención primaria y cardiología al alta, valorar el soporte social y comentar con el equipo los objetivos terapéuticos dada la comorbilidad elevada.

## Relación con otras escalas

- **CFS:** mide fragilidad funcional; complementa al Charlson en la valoración pronóstica.
- **Barthel:** valora la independencia funcional; útil junto con el Charlson para planificar el alta.
- **SOFA y APACHE II:** miden gravedad aguda, no comorbilidad.
- **NUTRIC/mNUTRIC:** el número de comorbilidades es uno de sus ítems.
- **MRC Sum Score:** la comorbilidad elevada se asocia a mayor debilidad adquirida y peor recuperación.

## Puntos clave

- Cuantifica la **comorbilidad** y estima la **mortalidad a largo plazo**.
- **19 condiciones** con pesos **1, 2, 3 o 6** + **1 punto por década desde los 50 años**.
- Total = suma de pesos + puntos por edad.
- **0** bajo; **1-2** moderado; **3-4** alto; **≥ 5** muy alto.
- Se construye con la **historia clínica**, no con exploración a pie de cama.
- Depende de la **calidad de la documentación**; hay que verificar cada diagnóstico.
- No mide fragilidad ni gravedad aguda: combinarlo con **CFS**, **Barthel**, **SOFA**.
- Actualizarlo cuando aparezcan nuevos diagnósticos.
