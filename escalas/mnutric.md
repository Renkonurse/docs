# mNUTRIC (NUTRIC modificado, sin IL-6)

> 📖 **Fuentes:** Rahman A, Hasan RM, Agarwala R, Martin C, Day AG, Heyland DK. *Identifying critically-ill patients who will benefit most from nutritional therapy: further validation of the «modified NUTRIC» nutritional risk assessment tool.* Clin Nutr. 2016;35(1):158-162. · Heyland DK, Dhaliwal R, Jiang X, Day AG. *Identifying critically ill patients who benefit the most from nutrition therapy: the development and initial validation of a novel risk assessment tool (NUTRIC).* Crit Care Med. 2011;39(4):795-801. · Marino PL. *The ICU Book.* 4th ed. Wolters Kluwer.

## Qué mide y para qué sirve

El **mNUTRIC** es la versión **modificada del NUTRIC score** que **prescinde del IL-6**, una determinación no disponible de forma rutinaria. Mantiene las mismas variables clínicas (**edad, APACHE II, SOFA, comorbilidades y días desde el ingreso hospitalario hasta la UCI**) y su total va de **0 a 9** (`es_nutric_descripcion`). Identifica al paciente crítico que **más se beneficia de un soporte nutricional precoz y agresivo**.

Sirve para:

- **Identificar al paciente crítico de alto riesgo nutricional** sin necesidad de IL-6.
- **Indicar el soporte nutricional precoz e intensivo** en los pacientes de riesgo.
- **Evitar la sobrealimentación** en los de bajo riesgo.
- **Estratificar el pronóstico** y ajustar por riesgo nutricional.
- **Estandarizar la valoración** nutricional en UCI.

## Población diana

- **Pacientes adultos críticos** ingresados en UCI, con independencia del motivo de ingreso.
- Es la versión **práctica y más extendida** del NUTRIC, al no requerir IL-6.
- Requiere un **APACHE II y un SOFA del ingreso**.
- **No es aplicable** a población pediátrica ni a pacientes no críticos.

## Cómo se puntúa

Se elige **una opción por cada uno de los 5 apartados** (el IL-6 no se incluye) y se suman los puntos.

### 1. Edad (`es_cj_item_1_age`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 0 | < 50 años | `es_nutric_edad_menor_50` |
| 1 | 50-74 años | `es_nutric_edad_50_74` |
| 2 | ≥ 75 años | `es_nutric_edad_mayor_75` |

### 2. APACHE II al ingreso (`es_nutric_item_apache_ii`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 0 | < 15 | `es_nutric_apache_menor_15` |
| 1 | 15-19 | `es_nutric_apache_15_19` |
| 2 | 20-27 | `es_nutric_apache_20_27` |
| 3 | ≥ 28 | `es_nutric_apache_mayor_28` |

### 3. SOFA al ingreso (`es_nutric_item_sofa`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 0 | < 6 | `es_nutric_sofa_menor_6` |
| 1 | 6-9 | `es_nutric_sofa_6_9` |
| 2 | ≥ 10 | `es_nutric_sofa_mayor_10` |

### 4. Nº de comorbilidades (`es_nutric_item_comorbilidades`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 0 | 0-1 | `es_nutric_rango_0_1` |
| 1 | ≥ 2 | `es_nutric_rango_mayor_2` |

### 5. Días desde el ingreso hospitalario a UCI (`es_nutric_item_dias_ingreso`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 0 | 0-1 | `es_nutric_rango_0_1` |
| 1 | ≥ 2 | `es_nutric_rango_mayor_2` |

### Total

| Concepto | Valor |
|---|---|
| Mínimo | 0 |
| Máximo | **9** |
| Diferencia con NUTRIC | No incluye el ítem de **IL-6** (que en NUTRIC suma 0-1 punto) |
| Registro en la app | `TOTAL NUTRIC` (`es_nutric_total_titulo`) |

## Cómo explorar cada ítem (técnica)

1. **Edad.** Registrar la edad real del paciente.
2. **APACHE II del ingreso.** Obtener la puntuación **APACHE II de las primeras 24 h** en UCI.
3. **SOFA del ingreso.** Utilizar el **SOFA de las primeras 24 h** con los peores valores del día (véase `sofa.md`).
4. **Comorbilidades.** Contar las enfermedades crónicas relevantes (puede apoyarse en el **Charlson**, `charlson.md`).
5. **Días desde el ingreso hospitalario a UCI.** Calcular el tiempo entre el ingreso en el hospital y el ingreso en UCI.

**Errores frecuentes:** calcular el APACHE II o el SOFA fuera de la ventana del ingreso; contar comorbilidades menores; olvidar el tiempo previo de hospitalización; y **sumar el ítem de IL-6** por error (en mNUTRIC no existe).

## Puntuación total e interpretación

| Puntuación | Riesgo | Etiqueta de la app | Actuación de enfermería |
|---|---|---|---|
| **0-4** | Bajo riesgo nutricional | `es_nutric_bajo_riesgo` (`es_nutric_info_bajo_riesgo`) | Evitar la sobrealimentación; ajustar el aporte y monitorizar la tolerancia |
| **≥ 5** | **Alto riesgo — considerar soporte nutricional agresivo** | `es_nutric_alto_riesgo` (`es_nutric_info_alto_riesgo`) | **Nutrición precoz (24-48 h)**, aporte calórico-proteico adecuado y seguimiento estrecho; coordinar con la unidad de nutrición |

Un **mNUTRIC ≥ 5** identifica al paciente de **alto riesgo** que se beneficia de **nutrición precoz (24-48 h), aporte calórico-proteico adecuado y monitorización estrecha** de la tolerancia. En pacientes de **bajo riesgo (0-4)** debe evitarse la sobrealimentación y ajustar el aporte a la evolución clínica. La enfermera participa registrando los datos del score, administrando el soporte nutricional y vigilando la **tolerancia digestiva** (residuo, distensión, diarrea, vómitos), la **glucemia** y el **riesgo de síndrome de realimentación**.

## Validez

El **mNUTRIC** fue validado por **Rahman et al. (Clin Nutr 2016)** como **validación adicional de la versión modificada sin IL-6** del NUTRIC, en pacientes críticos. En los estudios de validación, los pacientes con **mNUTRIC elevado** presentaron **peor pronóstico** y **mayor beneficio del aporte calórico-proteico elevado**, de forma similar a la versión original con IL-6.

Es la versión **más utilizada en la práctica clínica** por no requerir una determinación no disponible de forma rutinaria. No se incluyen cifras concretas de sensibilidad, especificidad o AUC porque varían según la población y el desenlace; para el detalle debe consultarse la publicación original y las validaciones posteriores.

## Limitaciones y errores frecuentes

- Al prescindir del IL-6, pierde el componente **inflamatorio** del score original; su capacidad discriminativa es, aun así, similar en las validaciones.
- Se aplica exclusivamente a **pacientes críticos adultos**.
- Requiere **APACHE II y SOFA del ingreso**: si se calculan en otro momento, la puntuación varía.
- No mide el **estado nutricional previo** ni la desnutrición: valora el riesgo de mala evolución **modificable con la nutrición**.
- La **sobrealimentación** también es perjudicial: no debe intensificarse el soporte en todos los pacientes.
- Las comorbilidades deben contarse con criterios homogéneos.
- Debe complementarse con la **valoración clínica y analítica** (albúmina, proteínas, peso, ingesta) y con la monitorización de la tolerancia.

## Ejemplo práctico resuelto

**Caso.** Varón de 55 años ingresado en UCI por neumonía grave, con 1 día de hospitalización previa. APACHE II 18, SOFA 7, una sola comorbilidad (HTA). No se dispone de IL-6.

| Apartado | Valor | Puntos |
|---|---|---|
| Edad | 50-74 años | 1 |
| APACHE II | 15-19 | 1 |
| SOFA | 6-9 | 1 |
| Comorbilidades | 0-1 | 0 |
| Días hasta UCI | 0-1 | 0 |
| **Total** | | **3** |

**mNUTRIC = 3 → bajo riesgo nutricional (0-4).**

**Actuación de enfermería:** mantener un aporte nutricional ajustado a la evolución clínica, **evitando la sobrealimentación**, monitorizar la tolerancia (residuo, distensión, glucemia), reevaluar el score si aparecen complicaciones o se prolonga la estancia y registrar el resultado con su desglose. Si el SOFA o el APACHE II empeoraran, recalcular el mNUTRIC.

## Relación con otras escalas

- **NUTRIC con IL-6:** versión original (0-10); útil si se dispone de IL-6.
- **SOFA:** aporta el componente de disfunción orgánica.
- **APACHE II:** aporta el componente de gravedad.
- **Charlson:** ayuda a contabilizar las comorbilidades.
- **Braden/EMINA:** el riesgo nutricional agrava el riesgo de UPP.
- **MRC Sum Score:** el estado nutricional influye en la debilidad muscular adquirida.

## Puntos clave

- Es el **NUTRIC sin IL-6**; total **0-9**.
- **5 apartados**: edad, APACHE II, SOFA, comorbilidades y días hasta UCI.
- **0-4** bajo riesgo; **≥ 5** alto riesgo → soporte **precoz y agresivo**.
- Es la versión **más utilizada** por no requerir IL-6.
- Usar el **APACHE II y SOFA del ingreso**.
- Evitar la **sobrealimentación** en pacientes de bajo riesgo.
- No mide desnutrición previa: mide **riesgo modificable con la nutrición**.
- Monitorizar **tolerancia** y **síndrome de realimentación**.
---
## Evidencia y referencias

- **Heyland DK, et al.** Identifying critically ill patients who benefit the most from nutrition therapy: the development and initial validation of a novel risk assessment tool. *Crit Care* 2011;15:R268.
- **Rahman A, et al.** Identifying critically-ill patients who will benefit most from nutritional therapy: further validation of the modified NUTRIC nutritional risk assessment tool. *Clin Nutr* 2016;35:158-162.
- **Compher C, et al.** ASPEN guidelines for the provision of nutrition support therapy in the adult critically ill patient. *JPEN* 2022.

> mNUTRIC no requiere IL-6, lo que facilita su uso. Un valor ≥ 5 identifica alto riesgo nutricional y puede orientar una nutrición más agresiva, sin olvidar la tolerancia.

---
## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **mNUTRIC** | Riesgo nutricional sin IL-6 |
| **NUTRIC** | Versión con IL-6 |
| **Nutrición enteral** | Inicio y progresión |
| **Síndrome de realimentación** | Prevención y control |
