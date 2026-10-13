# MRC Sum Score (Medical Research Council · fuerza muscular global)

> 📖 **Fuentes:** De Jonghe B, Sharshar T, Lefaucheur JP, et al. *Paresis acquired in the intensive care unit: a prospective multicenter study.* JAMA. 2002;288(22):2859-2867. · Chulay M, Burns SM. *AACN Essentials of Critical Care Nursing.* McGraw-Hill.

## Qué mide y para qué sirve

El **MRC Sum Score** valora la **fuerza muscular global** del paciente crítico para detectar la **debilidad muscular adquirida en la UCI (ICU-AW)**. Explora **12 grupos musculares (6 bilaterales)** —abducción del hombro, flexión del codo, extensión de la muñeca, flexión de la cadera, extensión de la rodilla y dorsiflexión del pie—, puntuando cada uno de **0 a 5**, con un **total de 0 a 60** (`es_mrc_descripcion`). El criterio de **ICU-AW es un total < 48** (`es_mrc_info_criterio_con`).

Sirve para:

- **Diagnosticar la debilidad muscular adquirida en la UCI (ICU-AW)**.
- **Cuantificar la fuerza global** y seguir su evolución.
- **Guiar la movilización precoz y la rehabilitación**.
- **Estratificar el pronóstico** (más días de ventilación, estancia y mortalidad).
- **Documentar y comunicar** el estado funcional neuromuscular.

## Población diana

- **Pacientes adultos críticos** que **pueden colaborar** y sin sedación profunda (`es_mrc_info_nota`: «Requiere paciente colaborador. Valorar sin sedación profunda»).
- Especialmente indicado en pacientes con **ventilación mecánica prolongada, sepsis, SDRA o fallo multiorgánico**, en los que la ICU-AW es frecuente.
- **No es aplicable** en pacientes con sedación profunda, delirium grave, bloqueo neuromuscular, coma o incapacidad para obedecer órdenes.
- Debe interpretarse con cautela en pacientes con **lesiones neurológicas centrales o periféricas previas**, dolor o barreras idiomáticas.

## Cómo se puntúa

Se asigna a **cada uno de los 12 grupos musculares** una puntuación de **0 a 5** según la escala del Medical Research Council.

| Puntos | Fuerza | Cadena en la app |
|---|---|---|
| 0 | Sin contracción | `es_mrc_opcion_0` |
| 1 | Contracción sin movimiento | `es_mrc_opcion_1` |
| 2 | Movimiento sin gravedad | `es_mrc_opcion_2` |
| 3 | Movimiento contra gravedad | `es_mrc_opcion_3` |
| 4 | Movimiento contra resistencia | `es_mrc_opcion_4` |
| 5 | Fuerza normal (resistencia completa) | `es_mrc_opcion_5` |

### Grupos musculares valorados (app)

| # | Grupo | Cadena en la app |
|---|---|---|
| 1 | Abducción del hombro (C5-C6) | `es_mrc_grupo_1` |
| 2 | Flexión del codo (C5-C6) | `es_mrc_grupo_2` |
| 3 | Extensión de la muñeca (C6-C7) | `es_mrc_grupo_3` |
| 4 | Flexión de cadera (L1-L2) | `es_mrc_grupo_4` |
| 5 | Extensión de rodilla (L2-L4) | `es_mrc_grupo_5` |
| 6 | Dorsiflexión del pie (L4-L5) | `es_mrc_grupo_6` |
| 7 | Abducción del hombro **izquierdo** (C5-C6) | `es_mrc_grupo_7` |
| 8 | Flexión del codo **izquierdo** (C5-C6) | `es_mrc_grupo_8` |
| 9 | Extensión de muñeca **izquierda** (C6-C7) | `es_mrc_grupo_9` |
| 10 | Flexión de cadera **izquierda** (L1-L2) | `es_mrc_grupo_10` |
| 11 | Extensión de rodilla **izquierda** (L2-L4) | `es_mrc_grupo_11` |
| 12 | Dorsiflexión del pie **izquierdo** (L4-L5) | `es_mrc_grupo_12` |

> La app explora los 12 grupos de forma **bilateral** (los grupos 7-12 corresponden al lado izquierdo).

### Total

| Concepto | Valor |
|---|---|
| Mínimo | 0 |
| Máximo | 60 (12 grupos × 5) |
| Media por grupo | Se muestra como `Media: %1$.1f` (`es_mrc_media`) |
| Registro en la app | `TOTAL MRC` (`es_mrc_total_titulo`) — `%1$s / 60` (`es_mrc_total_valor`) |

## Cómo explorar cada ítem (técnica)

1. **Preparación.** Comprobar que el paciente está **despierto, colaborador y sin sedación profunda**; explicar la exploración; colocarlo en decúbito y asegurar una buena alineación articular.
2. **Exploración grupo a grupo.** Pedir al paciente que realice el movimiento **contra resistencia** y valorar la fuerza de 0 a 5. Empezar por el lado derecho y repetir en el izquierdo.
   - **Hombro:** abducción del brazo contra resistencia.
   - **Codo:** flexión del antebrazo contra resistencia.
   - **Muñeca:** extensión de la muñeca contra resistencia.
   - **Cadera:** flexión del muslo contra resistencia.
   - **Rodilla:** extensión de la pierna contra resistencia.
   - **Pie:** dorsiflexión contra resistencia.
3. **Criterios de puntuación.** 5 = fuerza normal; 4 = movimiento contra resistencia pero debilitado; 3 = movimiento contra gravedad; 2 = movimiento sin gravedad (en el plano); 1 = contracción sin movimiento; 0 = sin contracción.
4. **Repetir y registrar** cada grupo, y calcular el total (0-60) y la media.

**Errores frecuentes:** explorar con el paciente sedado, con dolor o cansado; no sujetar la articulación para aislar el movimiento; valorar «a ojo» sin resistencia; no explorar ambos lados; y no documentar la puntuación de cada grupo.

## Puntuación total e interpretación

| Puntuación | Significado | Etiqueta de la app | Actuación de enfermería |
|---|---|---|---|
| **≥ 48** | Fuerza conservada — **sin ICU-AW** | `es_mrc_interp_conservada` (`es_mrc_info_criterio_sin`) | Mantener movilización precoz y reevaluar periódicamente |
| **< 48** | **ICU-AW confirmada** (debilidad adquirida en UCI) | `es_mrc_interp_icuaw` (`es_mrc_info_criterio_con`) | Intensificar **movilización precoz y rehabilitación**, control del dolor y de la sedación, optimizar nutrición y glucemia; comunicar al equipo |

La app muestra `es_mrc_interp_incompleto` («Completa las 6 valoraciones») mientras no se han puntuado todos los grupos, y dispone además de la etiqueta `es_mrc_interp_leve` («Debilidad leve») para gradaciones intermedias. Un total **< 48** se asocia a **más días de ventilación mecánica, estancia prolongada, mayor mortalidad y peor recuperación funcional**.

## Validez

El MRC Sum Score fue establecido como criterio de **debilidad muscular adquirida en la UCI** por **De Jonghe et al. (JAMA 2002)**, en un **estudio prospectivo multicéntrico** de pacientes críticos. El punto de corte de **< 48 puntos** se consolidó como definición operativa de **ICU-AW**, y la escala es el **estándar de referencia** para su diagnóstico en pacientes que colaboran.

Su fiabilidad depende de la **formación del explorador** y de la **colaboración del paciente**; en manos entrenadas muestra una buena fiabilidad interobservador. Como alternativas o complementos se utilizan la **dinamometría de mano** (handgrip) y otras escalas de fuerza, útiles cuando el paciente no puede completar los 12 grupos. No se incluyen cifras concretas de sensibilidad, especificidad o AUC porque varían según la población y el criterio de referencia; para el detalle debe consultarse la publicación original.

## Limitaciones y errores frecuentes

- Requiere **colaboración del paciente**; en sedación profunda, delirium o bloqueo neuromuscular no es aplicable.
- Puede verse dificultado por **dolor, barreras idiomáticas, afasia o lesiones neurológicas** periféricas/centrales previas.
- La exploración de **12 grupos bilaterales** consume tiempo; conviene formación y una sistemática ordenada.
- La **valoración subjetiva** de la resistencia introduce variabilidad entre exploradores.
- Las **alteraciones articulares, fracturas o vendajes** pueden limitar la exploración de algunos grupos (registrar como no valorable, no como 0).
- La **sedación y la analgesia** modifican la fuerza aparente; valorar en condiciones estables.
- Existen otras herramientas (dinamometría, escala de Chelsea) que pueden complementarlo.
- Debe repetirse de forma **seriada** (p. ej., cada 48 h) para detectar cambios.

## Ejemplo práctico resuelto

**Caso.** Varón de 60 años, séptimo día de ventilación mecánica por SDRA, despierto y colaborador, con sedación suspendida. Se explora la fuerza de los 12 grupos:

| Grupo | Derecha | Izquierda |
|---|---|---|
| Abducción del hombro | 3 | 3 |
| Flexión del codo | 4 | 4 |
| Extensión de la muñeca | 3 | 3 |
| Flexión de cadera | 4 | 4 |
| Extensión de rodilla | 3 | 3 |
| Dorsiflexión del pie | 2 | 2 |
| **Subtotal** | **19** | **19** |

**Total = 38 / 60 → < 48 → ICU-AW confirmada.**

**Actuación de enfermería:** registrar el total y la puntuación por grupos, iniciar/intensificar la **movilización precoz** y la rehabilitación (con fisioterapia), controlar el **dolor** y ajustar la sedación para permitir la participación, optimizar la **nutrición** y el control de la **glucemia**, prevenir complicaciones de la inmovilidad (UPP, TVP, atelectasias) y **repetir la valoración cada 48 h** para seguir la evolución. Comunicar el resultado al equipo médico.

## Relación con otras escalas

- **Barthel:** valora la independencia funcional; complementa la valoración de la fuerza.
- **CFS:** la fragilidad previa agrava la debilidad adquirida.
- **Índice de Tobin:** la debilidad muscular condiciona el patrón respiratorio y el destete.
- **NUTRIC/mNUTRIC:** el estado nutricional influye en la fuerza y en la recuperación.
- **RASS:** la sedación condiciona la aplicabilidad y la puntuación.
- **Braden/EMINA:** la inmovilidad aumenta el riesgo de UPP.

## Puntos clave

- Valora la **fuerza de 12 grupos musculares** (6 bilaterales) de **0 a 5**; total **0-60**.
- **< 48** define la **debilidad muscular adquirida en la UCI (ICU-AW)**.
- Requiere **paciente colaborador** y sin sedación profunda.
- Es el **estándar de referencia** para el diagnóstico de ICU-AW.
- Explorar **ambos lados** y con **resistencia** para graduar la fuerza.
- La ICU-AW se asocia a **más ventilación, estancia y mortalidad**.
- La **movilización precoz** es la intervención clave.
- Repetir de forma **seriada** para valorar la evolución.
