# NUTRIC Score (con IL-6) · riesgo nutricional en el paciente crítico

> 📖 **Fuentes:** Heyland DK, Dhaliwal R, Jiang X, Day AG. *Identifying critically ill patients who benefit the most from nutrition therapy: the development and initial validation of a novel risk assessment tool (NUTRIC score).* Crit Care Med. 2011;39(4):795-801. · Marino PL. *The ICU Book.* 4th ed. Wolters Kluwer.

## Qué mide y para qué sirve

El **NUTRIC score** identifica a los **pacientes críticos que más se benefician de un soporte nutricional agresivo** (`es_nutric_info_descripcion`). Combina variables de **edad, gravedad (APACHE II y SOFA), comorbilidad, tiempo hasta el ingreso en UCI e inflamación (IL-6)**. En su versión **con IL-6** el total va de **0 a 10**; la versión **sin IL-6 (mNUTRIC)** va de **0 a 9** (`es_nutric_descripcion`).

Sirve para:

- **Identificar al paciente de alto riesgo nutricional** que se beneficia de un soporte precoz e intensivo.
- **Evitar la sobrealimentación** en pacientes de bajo riesgo.
- **Guiar la intensidad del soporte nutricional** (aporte calórico-proteico, vía de administración).
- **Estratificar el pronóstico** y ajustar por riesgo nutricional en investigación.
- **Estandarizar la valoración** nutricional en UCI.

## Población diana

- **Pacientes adultos críticos** ingresados en UCI, con independencia del motivo de ingreso.
- Es especialmente útil en pacientes con **estancia prolongada, gravedad elevada o comorbilidad importante**.
- Requiere un **APACHE II y un SOFA del ingreso** y la determinación de **IL-6** (si está disponible).
- **No es aplicable** a población pediátrica ni a pacientes no críticos.

## Cómo se puntúa

Se elige **una opción por cada uno de los 6 apartados** y se suman los puntos.

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

### 6. IL-6 (si disponible) (`es_nutric_item_il6`)

| Puntos | Opción | Cadena en la app |
|---|---|---|
| 0 | < 400 pg/mL | `es_nutric_il6_menor_400` |
| 1 | ≥ 400 pg/mL | `es_nutric_il6_mayor_400` |

### Total

| Concepto | Valor |
|---|---|
| Mínimo | 0 |
| Máximo (con IL-6) | **10** |
| Máximo (sin IL-6 · mNUTRIC) | **9** |
| Registro en la app | `TOTAL NUTRIC` (`es_nutric_total_titulo`) |

## Cómo explorar cada ítem (técnica)

1. **Edad.** Registrar la edad real del paciente.
2. **APACHE II del ingreso.** Obtener la puntuación **APACHE II calculada en las primeras 24 h** del ingreso en UCI; si no está disponible, calcularla con los parámetros habituales (variables fisiológicas, edad y salud crónica).
3. **SOFA del ingreso.** Utilizar el **SOFA de las primeras 24 h** (véase `sofa.md`), con los peores valores del día.
4. **Comorbilidades.** Contar las enfermedades crónicas relevantes del paciente (puede apoyarse en el índice de **Charlson**, `charlson.md`).
5. **Días desde el ingreso hospitalario a UCI.** Calcular el tiempo transcurrido entre el ingreso en el hospital y el ingreso en UCI.
6. **IL-6.** Si el laboratorio la determina, registrar el valor (pg/mL) y aplicar el corte de 400; si no está disponible, usar la versión sin IL-6 (mNUTRIC).

**Errores frecuentes:** calcular el APACHE II o el SOFA en un momento distinto al ingreso (cambia la puntuación); contar comorbilidades menores; olvidar el tiempo previo de hospitalización; y usar el NUTRIC sin IL-6 y sumar igualmente el apartado 6.

## Puntuación total e interpretación

| Puntuación | Riesgo | Etiqueta de la app | Actuación de enfermería |
|---|---|---|---|
| **0-4** | Bajo riesgo nutricional | `es_nutric_bajo_riesgo` (`es_nutric_info_bajo_riesgo`) | Evitar la sobrealimentación; ajustar el aporte a la evolución; monitorizar la tolerancia |
| **≥ 5** | **Alto riesgo — considerar soporte nutricional agresivo** | `es_nutric_alto_riesgo` (`es_nutric_info_alto_riesgo`) | **Nutrición precoz (24-48 h)**, aporte calórico-proteico adecuado y seguimiento estrecho; coordinar con la unidad de nutrición |

Un NUTRIC **≥ 5** identifica al paciente que **se beneficia de soporte nutricional precoz e intensivo**. En pacientes de **bajo riesgo (0-4)** debe evitarse la **sobrealimentación** y el exceso de calorías. La enfermera contribuye aportando datos para el score y es clave en la **administración, tolerancia y seguimiento** del soporte nutricional (residuo gástrico, distensión, diarrea, glucemia, balance nitrogenado). La valoración debe completarse con parámetros clínicos y analíticos (albúmina, proteínas, peso, ingesta) y con la valoración del riesgo de **síndrome de realimentación**.

## Validez

El NUTRIC score fue **desarrollado y validado por Heyland et al. (Crit Care Med 2011)** en una **amplia base de datos multicéntrica de pacientes críticos**, donde mostró una relación entre la puntuación y los desenlaces (mortalidad, estancia) y, de forma relevante, una **mayor respuesta al aporte calórico-proteico elevado en los pacientes de mayor puntuación**. Es decir, no solo predice riesgo, sino que identifica a los pacientes que **más se benefician del tratamiento nutricional**.

Se ha validado en múltiples cohortes internacionales, con y sin IL-6. No se incluyen cifras concretas de sensibilidad, especificidad o AUC porque varían según la población y el desenlace; para el detalle debe consultarse la publicación original y las validaciones posteriores.

## Limitaciones y errores frecuentes

- El **IL-6 no está disponible de forma rutinaria** en la mayoría de las unidades; sin él se usa el **mNUTRIC (0-9)**, con el mismo punto de corte (≥ 5) y utilidad pronóstica similar (`mnutric.md`).
- El NUTRIC se diseñó para **pacientes críticos**; no es aplicable a otras poblaciones hospitalarias.
- Requiere un **APACHE II y un SOFA** calculados en el ingreso; si se calculan en otro momento, la puntuación cambia.
- No es una escala de **desnutrición**: valora el **riesgo de mala evolución modificable por la nutrición**, no el estado nutricional previo.
- La **sobrealimentación** también es perjudicial: no debe intensificarse el soporte en todos los pacientes.
- Las comorbilidades deben contarse con criterios homogéneos para evitar variabilidad.
- Debe complementarse con la valoración clínica y con la monitorización de la tolerancia.

## Ejemplo práctico resuelto

**Caso.** Mujer de 78 años ingresada en UCI por shock séptico de origen urinario, con 3 días de hospitalización previa. APACHE II 24, SOFA 11, dos comorbilidades (EPOC y diabetes), IL-6 disponible de 520 pg/mL.

| Apartado | Valor | Puntos |
|---|---|---|
| Edad | ≥ 75 años | 2 |
| APACHE II | 20-27 | 2 |
| SOFA | ≥ 10 | 2 |
| Comorbilidades | ≥ 2 | 1 |
| Días hasta UCI | ≥ 2 | 1 |
| IL-6 | ≥ 400 pg/mL | 1 |
| **Total** | | **9** |

**NUTRIC = 9 → alto riesgo (≥ 5).**

**Actuación de enfermería:** iniciar el **soporte nutricional precoz (en las primeras 24-48 h)** según protocolo, con aporte calórico-proteico adecuado y vigilancia de la tolerancia (residuo gástrico, distensión, diarrea, glucemia), coordinar con la unidad de nutrición, monitorizar el **riesgo de síndrome de realimentación** (fósforo, potasio, magnesio) y registrar el score con su desglose y la evolución.

## Relación con otras escalas

- **mNUTRIC:** versión sin IL-6 (0-9), de uso más extendido.
- **SOFA:** aporta el componente de disfunción orgánica.
- **APACHE II:** aporta el componente de gravedad.
- **Charlson:** ayuda a contabilizar las comorbilidades.
- **Braden/EMINA:** el riesgo nutricional agrava el riesgo de UPP.
- **MRC Sum Score:** el estado nutricional influye en la debilidad muscular adquirida.

## Puntos clave

- Identifica al paciente crítico que **más se beneficia del soporte nutricional**.
- **6 apartados**: edad, APACHE II, SOFA, comorbilidades, días hasta UCI e IL-6.
- Total **0-10 con IL-6** y **0-9 sin IL-6 (mNUTRIC)**.
- **0-4** bajo riesgo; **≥ 5** alto riesgo → soporte **precoz y agresivo**.
- Evitar la **sobrealimentación** en pacientes de bajo riesgo.
- Usar el **APACHE II y SOFA del ingreso**.
- No mide desnutrición previa: mide **riesgo modificable con la nutrición**.
- Monitorizar la **tolerancia** y el **síndrome de realimentación**.
---
## Evidencia y referencias

- **Heyland DK, et al.** Identifying critically ill patients who benefit the most from nutrition therapy: the development and initial validation of a novel risk assessment tool. *Crit Care* 2011;15:R268.
- **Rahman A, et al.** Further validation of the modified NUTRIC nutritional risk assessment tool. *Clin Nutr* 2016.
- **Compher C, et al.** ASPEN guidelines for the provision of nutrition support therapy in the adult critically ill patient. *JPEN* 2022.

> La versión original incluye IL-6, que no está disponible de forma rutinaria; por eso se usa mNUTRIC. La puntuación orienta, no impone una terapia nutricional agresiva.

---
## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **NUTRIC** | Riesgo nutricional con IL-6 |
| **mNUTRIC** | Versión sin IL-6 |
| **Nutrición enteral** | Inicio y progresión |
| **Síndrome de realimentación** | Prevención y control |
