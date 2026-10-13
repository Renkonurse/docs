# Índice de Barthel (independencia en actividades básicas de la vida diaria)

> 📖 **Fuentes:** Mahoney FI, Barthel DW. *Functional evaluation: the Barthel Index.* Md State Med J. 1965;14:61-65. · MSD Manual Professional: https://www.msdmanuals.com/professional

## Qué mide y para qué sirve

El **índice de Barthel** valora el **grado de independencia** del paciente en **10 actividades básicas de la vida diaria** (ABVD): alimentación, aseo, vestido, continencia, uso del retrete, traslados, deambulación y escaleras (`es_barthel_dialog_description`). Cada actividad puntúa según la ayuda necesaria; la **suma total va de 0 a 100** (a mayor puntuación, mayor independencia, `es_barthel_dialog_total_score`).

Sirve para:

- **Cuantificar la dependencia funcional** y objetivar la evolución del paciente.
- **Planificar los cuidados** y los recursos necesarios al alta (`es_dialog_useful`).
- **Detectar las actividades** en las que el paciente necesita ayuda.
- **Evaluar la respuesta** a la rehabilitación y a la movilización precoz.
- **Predecir** el destino al alta y las necesidades de apoyo social.

## Población diana

- **Pacientes adultos** con cualquier proceso que altere la funcionalidad: ictus, fracturas, postoperatorio, enfermedades neuromusculares, ancianos frágiles, pacientes críticos en recuperación.
- Es aplicable en **planta, rehabilitación y UCI** (cuando el paciente puede colaborar).
- **Requiere observación directa o información fiable** del cuidador; en pacientes con deterioro cognitivo avanzado puede sobreestimar la dependencia.
- **No está diseñado** para población pediátrica (existen otras escalas funcionales pediátricas).

## Cómo se puntúa

Instrucción de la app: *selecciona una opción por apartado* (`es_select_option_per_section`). Hay que completar los 10 apartados (`es_progress_sections`).

| # | Actividad (app) | Opciones y puntos |
|---|---|---|
| 1 | **Comer** (`es_item_eating`) | Independiente (come solo) **10** (`es_option_eats_independently`) · Necesita ayuda (cortar, untar) **5** (`es_option_needs_help_cutting`) · Dependiente **0** (`es_dependent`) |
| 2 | **Lavarse / bañarse** (`es_item_bathing`) | Independiente **5** (`es_independent`) · Dependiente **0** (`es_dependent`) |
| 3 | **Vestirse / desvestirse** (`es_item_dressing`) | Independiente (incluye botones, cordones) **10** (`es_option_dressing_independent`) · Necesita ayuda **5** (`es_needs_help`) · Dependiente **0** (`es_dependent`) |
| 4 | **Arreglarse (aseo personal)** (`es_item_grooming`) | Independiente (cara, pelo, dientes, afeitar) **5** (`es_option_grooming_independent`) · Dependiente **0** (`es_dependent`) |
| 5 | **Deposiciones** (`es_item_bowel`) | Continente **10** (`es_cj_incont_continent`) · Accidente ocasional **5** (`es_occasional_accident`) · Incontinente **0** (`es_incontinent`) |
| 6 | **Micción** (`es_item_bladder`) | Continente (o maneja sonda solo) **10** (`es_option_continent_catheter`) · Accidente ocasional **5** (`es_occasional_accident`) · Incontinente o sondado dependiente **0** (`es_option_incontinent_catheter`) |
| 7 | **Usar el retrete** (`es_item_toilet`) | Independiente **10** (`es_independent`) · Necesita ayuda **5** (`es_needs_help`) · Dependiente **0** (`es_dependent`) |
| 8 | **Trasladarse sillón / cama** (`es_item_transfers`) | Independiente **15** (`es_independent`) · Mínima ayuda **10** (`es_minimal_help`) · Gran ayuda, pero se mantiene sentado **5** (`es_major_help_sitting`) · Dependiente, no se mantiene sentado **0** (`es_dependent_not_sitting`) |
| 9 | **Deambular** (`es_item_mobility`) | Independiente (puede usar bastón) **15** (`es_option_mobility_independent_cane`) · Necesita ayuda física **10** (`es_needs_physical_help`) · Independiente en silla de ruedas **5** (`es_option_wheelchair_independent`) · Dependiente / inmovilizado **0** (`es_dependent_immobile`) |
| 10 | **Subir y bajar escaleras** (`es_item_stairs`) | Independiente **10** (`es_independent`) · Necesita ayuda **5** (`es_needs_help`) · Dependiente **0** (`es_dependent`) |

### Total

| Concepto | Valor |
|---|---|
| Mínimo | 0 |
| Máximo | **100** |
| Registro en la app | `TOTAL BARTHEL` (`es_total_barthel`, mostrado como `$total / 100`) |

## Cómo explorar cada ítem (técnica)

El Barthel se valora mediante **observación directa** (preferible) y **entrevista** al paciente o al cuidador.

1. **Comer.** Observar si es capaz de comer solo en un tiempo razonable; si necesita que le corten o le unten la comida, puntúa 5.
2. **Lavarse / bañarse.** Valorar si puede usar la ducha o el baño sin ayuda (incluye enjabonarse, aclararse y secarse).
3. **Vestirse.** Comprobar si se pone y quita la ropa, incluidos botones, cremalleras y cordones, en tiempo razonable.
4. **Arreglarse.** Valorar el aseo personal: lavarse la cara y las manos, peinarse, lavarse los dientes y afeitarse.
5. **Deposiciones.** Registrar la continencia fecal y la necesidad de ayuda (enema, supositorio).
6. **Micción.** Registrar la continencia urinaria; si el paciente maneja solo la sonda o el colector, se considera continente.
7. **Usar el retrete.** Valorar si puede llegar, sentarse, limpiarse y levantarse sin ayuda.
8. **Trasladarse.** Observar el paso de la cama al sillón y viceversa; distinguir la ayuda mínima de la gran ayuda y de la dependencia total.
9. **Deambular.** Valorar la marcha (con bastón permitido) o el manejo independiente de la silla de ruedas.
10. **Escaleras.** Valorar si sube y baja un tramo sin ayuda (con bastón permitido).

**Errores frecuentes:** puntuar lo que el paciente «podría hacer» en lugar de lo que hace; no observar directamente; no registrar la ayuda real prestada; y valorar en un momento de fatiga o dolor, lo que infravalora la capacidad.

## Puntuación total e interpretación

| Puntuación | Grado de dependencia | Etiqueta de la app | Actuación de enfermería |
|---|---|---|---|
| **100** | Independiente | `es_independent` | Fomentar la autonomía; educación y prevención |
| **≥ 60** | Dependencia leve / independiente | `es_mild_dependency` (`es_dialog_range_60`: ≥ 60) | Apoyo puntual, adaptaciones y entrenamiento de la autonomía |
| **40-55** | Dependencia moderada | `es_moderate_dependency` (`es_dialog_range_40`: 40-55) | Ayuda parcial en ABVD, valorar rehabilitación y ayudas técnicas |
| **20-35** | Dependencia grave | `es_severe_dependency` (`es_dialog_range_20`: 20-35) | Cuidados de apoyo amplios, prevención de UPP y caídas, movilización y rehabilitación |
| **< 20** | Dependencia total | `es_total_dependency` (`es_dialog_range_less_20`: < 20) | Cuidados completos, prevención de complicaciones de la inmovilidad, planificación de recursos al alta |

Puntuaciones bajas obligan a reforzar la **prevención de UPP, caídas, úlceras y complicaciones de la inmovilidad**, así como la **movilización precoz**.

## Validez

El índice de Barthel fue publicado por **Mahoney y Barthel (Md State Med J 1965)** y es una de las escalas funcionales más utilizadas y traducidas del mundo. Está **validado en múltiples poblaciones** (ictus, ancianos, rehabilitación, pacientes hospitalizados) y muestra una **buena fiabilidad interobservador** y una **buena correlación con otras medidas de dependencia** y con el pronóstico funcional.

Su principal limitación psicométrica son los **efectos techo y suelo**: no discrimina bien entre los pacientes muy independientes ni entre los muy dependientes. No se incluyen cifras concretas de sensibilidad, especificidad o AUC porque no es una prueba diagnóstica, sino una medida de función.

## Limitaciones y errores frecuentes

- Tiene **efecto techo y suelo**: no discrimina bien en los extremos.
- La puntuación depende de la **interpretación del valorador**; conviene consensuar los criterios de cada actividad en el equipo.
- No recoge aspectos como la **función cognitiva, el dolor, el estado emocional o la calidad de vida**, que deben valorarse por separado.
- En pacientes con **deterioro cognitivo avanzado** puede **sobreestimar la dependencia** por falta de colaboración.
- **No mide la función instrumental** (compras, cocina, teléfono, medicación): para eso existen escalas como el índice de Lawton.
- Debe valorarse en un momento **estable** (sin dolor agudo ni fatiga extrema) y reevaluarse periódicamente.

## Ejemplo práctico resuelto

**Caso.** Mujer de 78 años, sexto día de ingreso tras ictus isquémico leve. Come sola (10), se lava con dificultad pero sin ayuda (5), se viste con ayuda para los botones (5), se arregla sola (5), es continente (10 y 10), usa el retrete con ayuda (5), se traslada con mínima ayuda (10), deambula con bastón (15) y sube escaleras con ayuda (5).

| Actividad | Puntos |
|---|---|
| Comer | 10 |
| Lavarse | 5 |
| Vestirse | 5 |
| Arreglarse | 5 |
| Deposiciones | 10 |
| Micción | 10 |
| Retrete | 5 |
| Traslados | 10 |
| Deambular | 15 |
| Escaleras | 5 |
| **Total** | **80** |

**Barthel = 80 → dependencia leve** (≥ 60).

**Actuación de enfermería:** registrar el perfil por actividades, reforzar la autonomía con ayudas técnicas (asiento de baño, cubiertos adaptados), entrenar el vestido con botones, coordinar con rehabilitación, prevenir caídas (bastón, calzado adecuado) y planificar el alta con apoyo domiciliario si precisa.

## Relación con otras escalas

- **CFS:** valora fragilidad global, incluidas las actividades instrumentales.
- **MRC Sum Score:** mide la fuerza muscular, que condiciona la independencia.
- **Braden y EMINA:** la inmovilidad y la dependencia incrementan el riesgo de UPP.
- **Morse y Downton:** la dependencia funcional es un factor de riesgo de caídas.
- **NUTRIC/mNUTRIC:** el estado funcional y nutricional están relacionados.

## Puntos clave

- Valora la **independencia en 10 ABVD**; total **0-100**.
- **100** independiente; **≥ 60** dependencia leve; **40-55** moderada; **20-35** grave; **< 20** total.
- Se valora por **observación directa** y entrevista.
- No discrimina bien en los extremos (**techo/suelo**).
- No recoge función cognitiva ni instrumental.
- Útil para **planificar el alta** y los recursos.
- Reevaluar periódicamente y tras cambios clínicos.
- Registrar la **ayuda real** prestada, no la capacidad potencial.
