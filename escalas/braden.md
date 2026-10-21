# Escala de Braden (riesgo de úlceras por presión)

> 📖 **Fuentes:** Bergstrom N, Braden BJ, Laguzza A, Holman V. *The Braden Scale for predicting pressure sore risk.* Nurs Res. 1987;36(4):205-210. · Chulay M, Burns SM. *AACN Essentials of Critical Care Nursing.* McGraw-Hill.

## Qué mide y para qué sirve

La **escala de Braden** valora el **riesgo de úlceras por presión (UPP)** a partir de **6 subescalas**: percepción sensorial, humedad, actividad, movilidad, nutrición y fricción/cizallamiento. Cada subescala puntúa de **1 a 4** (en fricción/cizallamiento solo 1 a 3), y la **suma total va de 6 a 23**: **a menor puntuación, mayor riesgo** (`es_braden_info_puntuacion_total`).

Sirve para:

- **Identificar a los pacientes con riesgo de UPP** y graduar ese riesgo.
- **Indicar las medidas preventivas** (cambios posturales, superficies de apoyo, cuidados de la piel).
- **Orientar la intervención** en cada subescala alterada.
- **Documentar y comunicar** el riesgo entre turnos.
- **Evaluar la evolución** del riesgo a lo largo del ingreso.

## Población diana

- **Pacientes adultos hospitalizados** con movilidad reducida, encamados o con alteración sensitiva: UCI, planta, unidades de rehabilitación, residencias.
- Es aplicable al **ingreso** y en las **reevaluaciones periódicas**.
- En **pacientes críticos** puede complementarse con escalas específicas de UCI (**Cubbin & Jackson**) o con la escala **EMINA**.
- **No está diseñada** para población pediátrica (existe la escala de Braden Q).

## Cómo se puntúa

Instrucción de la app: *selecciona una opción por subescala* (`es_selecciona_una_opcion_por_subescala`). Deben completarse las 6 subescalas (`es_progreso_subescalas`).

### 1. Percepción sensorial (`es_sub_percepcion_sensorial`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 4 | Sin limitación (responde a estímulos verbales) | `es_perc_sin_limitacion_verbal` |
| 3 | Ligeramente limitada | `es_cj_mobility_limited` |
| 2 | Muy limitada (solo responde a dolor) | `es_perc_muy_limitada_dolor` |
| 1 | Completamente limitada (inconsciente) | `es_perc_completamente_limitada` |

### 2. Humedad (`es_sub_humedad`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 4 | Raramente húmeda | `es_hum_raramente` |
| 3 | Ocasionalmente húmeda | `es_hum_ocasionalmente` |
| 2 | A menudo húmeda | `es_hum_a_menudo` |
| 1 | Constantemente húmeda | `es_hum_constantemente` |

### 3. Actividad (`es_sub_actividad`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 4 | Camina frecuentemente | `es_act_camina_frecuentemente` |
| 3 | Camina ocasionalmente | `es_act_camina_ocasionalmente` |
| 2 | Se desplaza en silla | `es_act_silla` |
| 1 | Encamado | `es_act_encamado` |

### 4. Movilidad (`es_sub_movilidad`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 4 | Sin limitación | `es_sin_limitacion` |
| 3 | Ligeramente limitada | `es_cj_mobility_limited` |
| 2 | Muy limitada | `es_muy_limitada` |
| 1 | Completamente inmóvil | `es_mov_completamente_inmovil` |

### 5. Nutrición (`es_sub_nutricion`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 4 | Excelente | `es_nut_excelente` |
| 3 | Adecuada | `es_adequate` |
| 2 | Probablemente inadecuada | `es_nut_probablemente_inadecuada` |
| 1 | Muy pobre | `es_nut_muy_pobre` |

### 6. Fricción y cizallamiento (`es_sub_friccion_cizallamiento`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 3 | Sin problema aparente | `es_fric_sin_problema` |
| 2 | Problema potencial | `es_fric_problema_potencial` |
| 1 | Problema | `es_fric_problema` |

> La app dispone además del nivel «Problema grave» (`es_fric_problema_grave`), pero la pantalla utiliza los **tres niveles** indicados (3-2-1).

### Total

| Concepto | Valor |
|---|---|
| Mínimo | 6 |
| Máximo | 23 |
| Registro en la app | `TOTAL BRADEN` — `%1$d / 23` (`es_total_braden`, `es_total_braden_valor`) |

## Cómo explorar cada ítem (técnica)

1. **Percepción sensorial.** Valorar la capacidad de **responder a la presión**: si el paciente percibe y comunica el malestar. En el paciente sedado o inconsciente, la puntuación es 1.
2. **Humedad.** Observar el grado de **exposición de la piel a la humedad** (sudor, orina, heces, exudado, drenajes): desde raramente hasta constantemente húmeda.
3. **Actividad.** Valorar el **nivel de actividad física**: camina frecuentemente, ocasionalmente, se desplaza en silla o está encamado.
4. **Movilidad.** Valorar la **capacidad de cambiar de posición** y de controlar el tronco y las extremidades.
5. **Nutrición.** Valorar la **ingesta habitual** de alimentos y proteínas, el estado de la albúmina y el peso; en UCI considerar la nutrición enteral/parenteral y su adecuación.
6. **Fricción y cizallamiento.** Valorar el **riesgo de lesión por movimiento**: necesidad de ayuda para movilizarse, deslizamiento en la cama, espasticidad, contracturas o agitación.

**Errores frecuentes:** valorar la percepción sensorial en un paciente sedado sin tenerlo en cuenta; no registrar la humedad de la noche; estimar la nutrición «a ojo»; y no inspeccionar la piel durante la valoración.

## Puntuación total e interpretación

| Puntuación | Riesgo de UPP | Etiqueta de la app | Actuación de enfermería |
|---|---|---|---|
| **≥ 19** | Sin riesgo | `es_no_risk` (`es_info_sin_riesgo`) | Cuidados habituales de la piel; reevaluación periódica |
| **15-18** | Riesgo bajo | `es_braden_riesgo_bajo` (`es_info_riesgo_bajo`) | Cambios posturales programados, higiene y observación de la piel |
| **13-14** | Riesgo moderado | `es_cj_risk_moderate` (`es_info_riesgo_moderado`) | Superficies de apoyo, cambios posturales frecuentes, cuidado de la humedad y nutrición |
| **10-12** | Riesgo alto | `es_adiva_high_risk` (`es_info_riesgo_alto`) | Medidas preventivas intensivas; revisar el plan cada turno |
| **≤ 9** | Riesgo muy alto | `es_braden_riesgo_muy_alto` (`es_info_riesgo_muy_alto`) | Prevención máxima, superficies especiales, movilización y vigilancia continua de la piel |

**A menor puntuación, mayor riesgo**: un resultado **≤ 12** obliga a instaurar **medidas preventivas intensivas**. Se recomienda **reevaluar al menos cada 24-48 h** en pacientes de riesgo y siempre ante cambios clínicos (`es_info_reevaluacion`). La enfermera debe vigilar las **prominencias óseas** (sacro, talones, trocánteres, occipucio, codos) e inspeccionar la piel en cada cambio postural. Las subescalas orientan la intervención concreta: humedad → cambio frecuente de absorbentes y protección cutánea; movilidad/actividad → movilización precoz; nutrición → valoración nutricional; fricción → técnicas de movilización sin arrastre.

## Validez

La escala de Braden fue publicada por **Bergstrom et al. (Nurs Res 1987)** y es una de las escalas de riesgo de UPP **más utilizadas y validadas internacionalmente**, con versiones traducidas a numerosos idiomas y adaptaciones para UCI (Braden Q en pediatría). Su **sensibilidad y especificidad son moderadas y dependen del punto de corte** elegido: puntuaciones bajas identifican bien el riesgo, mientras que los puntos de corte más altos aumentan la sensibilidad a costa de la especificidad.

No se incluyen cifras concretas de sensibilidad, especificidad o AUC porque varían según la población, el punto de corte y la incidencia de UPP; para el detalle debe consultarse la publicación original y las revisiones sistemáticas.

## Limitaciones y errores frecuentes

- Es una escala **predictiva**, no diagnóstica: **no sustituye a la inspección de la piel**.
- No incluye factores relevantes en UCI como la **inestabilidad hemodinámica, el uso de vasopresores, la ventilación mecánica o los dispositivos médicos** (pueden causar UPP por presión de dispositivos).
- Puede **sobreestimar el riesgo** en pacientes con limitación sensorial crónica estable.
- La subescala de **nutrición** depende de información que no siempre es fiable.
- La puntuación puede variar entre valoradores; conviene formación y consenso.
- No debe usarse de forma aislada: integrarla con la valoración clínica y con la inspección de la piel.

## Ejemplo práctico resuelto

**Caso.** Varón de 80 años, encamado tras fractura de cadera, con incontinencia urinaria y fecal, somnoliento y con ingesta escasa.

| Subescala | Valor | Puntos |
|---|---|---|
| Percepción sensorial | Responde a estímulos verbales | 4 |
| Humedad | Constantemente húmeda | 1 |
| Actividad | Encamado | 1 |
| Movilidad | Completamente inmóvil | 1 |
| Nutrición | Probablemente inadecuada | 2 |
| Fricción/cizallamiento | Problema (necesita ayuda para moverse) | 1 |
| **Total** | | **10** |

**Braden = 10 → riesgo alto (10-12).**

**Actuación de enfermería:** instaurar medidas preventivas intensivas (cambios posturales cada 2 h, superficie de apoyo, protección de prominencias), manejar la humedad con absorbentes y protección cutánea, revisar la piel en cada cambio de posición, coordinar la valoración nutricional, enseñar a la familia la movilización segura y **reevaluar cada 24 h**. Registrar la puntuación, las medidas y las lesiones observadas.

## Relación con otras escalas

- **EMINA:** alternativa validada en España para el riesgo de UPP.
- **Cubbin & Jackson:** escala específica del paciente crítico.
- **Barthel:** la dependencia funcional se relaciona con el riesgo de UPP.
- **CFS:** la fragilidad aumenta el riesgo de lesiones cutáneas.
- **MRC Sum Score:** la debilidad adquirida prolonga la inmovilidad.

## Puntos clave

- Valora el **riesgo de UPP** con **6 subescalas**; total **6-23**.
- **A menor puntuación, mayor riesgo**.
- **≥ 19** sin riesgo; **15-18** bajo; **13-14** moderado; **10-12** alto; **≤ 9** muy alto.
- Reevaluar **cada 24-48 h** y ante cambios clínicos.
- **No sustituye a la inspección de la piel**.
- No recoge factores específicos de UCI (vasopresores, dispositivos).
- Las subescalas **orientan la intervención** concreta.
- Formación y consenso del equipo para reducir la variabilidad.
---
## Evidencia y referencias

- **Bergstrom N, et al.** The Braden Scale for predicting pressure sore risk. *Nurs Res* 1987;36:205-210.
- **Pancorbo-Hidalgo PL, et al.** Risk assessment scales for pressure ulcer prevention: a systematic review. *J Adv Nurs* 2006.
- **NPIAP/EPUAP/PPPIA.** Prevention and Treatment of Pressure Ulcers/Injuries: Clinical Practice Guideline. 2019.

> La escala tiene validez predictiva moderada; ninguna escala sustituye la valoración clínica de la piel y de los factores de riesgo.

---
## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **Escala de Braden** | Riesgo de úlceras por presión |
| **Prevención de UPP** | Medidas según el nivel de riesgo |
| **Cuidados de la piel** | Inspección y protección |
| **EMINA / Cubbin & Jackson** | Alternativas en planta y críticos |
