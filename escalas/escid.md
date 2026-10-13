# ESCID · Escala de Conductas Indicadoras de Dolor

> 📖 **Fuentes:** Latorre-Marco I, Acevedo-Nuevo M, Solís-Muñoz M, et al. *Psychometric validation of the behavioral indicators of pain scale for the assessment of pain in mechanically ventilated and unable to self-report critical care patients (ESCID).* Med Intensiva. 2016;40(8):463-473. · Devlin JW, Skrobik Y, Gélinas C, et al. *PADIS Clinical Practice Guidelines.* Crit Care Med. 2018;46(9):e825-e873. · SEEIUC: https://www.seeiuc.org

## Qué mide y para qué sirve

La **ESCID (Escala de Conductas Indicadoras de Dolor)** es una escala **observacional** que valora el **dolor en el paciente crítico que no puede comunicarse** (sedado, intubado, con delirium o con alteración de la consciencia). Evalúa **5 conductas indicadoras de dolor**, cada una de **0 a 2 puntos**, con un total de **0 a 10**. La app muestra la escala completa con las 5 conductas y sus opciones (`itemsEscid`).

Sirve para:

- **Detectar el dolor** en el paciente que no puede autoinformarlo.
- **Guiar la analgesia** en el paciente crítico: indicar rescates, titular perfusiones y valorar la respuesta.
- **Evaluar el dolor durante los procedimientos** (aspiración de secreciones, curas, movilización, retirada de drenajes), cuando más aparece.
- **Diferenciar el dolor de otras causas** de agitación o de lucha con el ventilador.
- **Registrar y comunicar** de forma objetiva el dolor entre turnos.

Es la **alternativa española validada** a la EVA en el paciente no comunicativo; la app la describe como «escala observacional para pacientes críticos que no pueden comunicar el dolor» (`es_info_descripcion`).

## Población diana

- **Pacientes adultos críticos** que no pueden autoinformar el dolor: sedados, intubados, con delirium, con deterioro cognitivo avanzado o con alteración de la consciencia.
- Especialmente indicada en **pacientes en ventilación mecánica**.
- **No es válida** en el paciente con **bloqueo neuromuscular** (las conductas motoras no son valorables) ni en el paciente que puede comunicarse (en ese caso, usar **EVA**).
- Debe valorarse en **reposo y durante la movilización o los procedimientos**.

## Cómo se puntúa

Se selecciona **una única opción por conducta**. La app asigna **0 al primer nivel, 1 al segundo y 2 al tercero** de cada item.

### 1. Musculatura facial (`es_item1_nombre`)

| Puntos | Descripción | Cadena en la app |
|---|---|---|
| 0 | Relajada | `es_item1_op1` |
| 1 | En tensión, ceño fruncido / gesto de dolor | `es_item1_op2` |
| 2 | Ceño fruncido de forma habitual / dientes apretados | `es_item1_op3` |

### 2. «Tranquilidad» (`es_item2_nombre`)

| Puntos | Descripción | Cadena en la app |
|---|---|---|
| 0 | Tranquilo, relajado, movimientos normales | `es_item2_op1` |
| 1 | Movimientos ocasionales de inquietud y/o posición | `es_item2_op2` |
| 2 | Movimientos frecuentes incluyendo cabeza o extremidades | `es_item2_op3` |

### 3. Tono muscular (`es_item3_nombre`)

| Puntos | Descripción | Cadena en la app |
|---|---|---|
| 0 | Normal | `es_downton_option_normal` |
| 1 | Aumentado. Flexión | `es_item3_op2` |
| 2 | Rígido | `es_item3_op3` |

### 4. Adaptación a ventilación mecánica (VM) (`es_item4_nombre`)

| Puntos | Descripción | Cadena en la app |
|---|---|---|
| 0 | Tolerando ventilación mecánica | `es_item4_op1` |
| 1 | Tose pero tolera VM | `es_item4_op2` |
| 2 | Lucha con el respirador | `es_item4_op3` |

### 5. Confortabilidad (`es_item5_nombre`)

| Puntos | Descripción | Cadena en la app |
|---|---|---|
| 0 | Cómodo, tranquilo | `es_item5_op1` |
| 1 | Se tranquiliza al tacto y/o a la voz. Fácil de distraer | `es_item5_op2` |
| 2 | Difícil de confortar al tacto o hablándole | `es_item5_op3` |

### Total

| Concepto | Valor |
|---|---|
| Mínimo | 0 (0+0+0+0+0) |
| Máximo | 10 (2 en cada una de las 5 conductas) |
| Registro en la app | `TOTAL ESCID` (`es_total_label`) · `es_escid_info_puntuacion_total` («Puntuación total: 0 – 10») |

## Cómo explorar cada ítem (técnica)

1. **Preparación.** Observar al paciente durante al menos **1 minuto** en reposo, sin manipulación, con la habitación en calma. Anotar primero la puntuación **en reposo**.
2. **Musculatura facial.** Observar la frente, las cejas y la boca: relajada (0), tensa con ceño fruncido o gesto de dolor (1), ceño fruncido mantenido o dientes apretados (2).
3. **«Tranquilidad».** Observar los movimientos: normales (0), inquietud o cambios de posición ocasionales (1), movimientos frecuentes de cabeza o extremidades (2).
4. **Tono muscular.** Valorar mediante **movilización pasiva suave** de un brazo: sin resistencia (0), resistencia (1), rigidez marcada (2). No forzar si hay dolor evidente o fracturas.
5. **Adaptación a la ventilación mecánica.** Observar la interacción con el ventilador y las curvas: tolera (0), tose pero tolera o presenta suspiros/gemidos (1), lucha con el respirador o presenta quejidos/llanto (2). En el paciente no intubado, valorar la voz (normal frente a quejidos).
6. **Confortabilidad.** Valorar la respuesta al tacto y a la voz: cómodo (0), se tranquiliza y es fácil de distraer (1), difícil de confortar (2).
7. **Repetir la valoración durante el procedimiento** (aspiración, cura, movilización) y **tras la analgesia**, para valorar la respuesta.

**Errores frecuentes:** valorar solo en reposo y no durante los procedimientos; no movilizar pasivamente el brazo para valorar el tono; atribuir la lucha con el ventilador solo al dolor sin descartar asincronía, secreciones o hipoxemia; no reevaluar tras la analgesia; y no formar al equipo, lo que aumenta la variabilidad entre observadores.

## Puntuación total e interpretación

| Puntuación | Significado | Cadena en la app | Actuación de enfermería |
|---|---|---|---|
| 0 | No dolor | `es_interp_no_dolor` (`es_info_rango_0`) | Mantener analgesia pautada si procede; reevaluar por turnos |
| 1-3 | Dolor leve-moderado | `es_interp_dolor_leve_moderado` (`es_info_rango_1_3`) | Medidas no farmacológicas y analgesia pautada; reevaluar |
| 4-6 | Dolor moderado-grave | `es_interp_dolor_moderado_grave` (`es_info_rango_4_6`) | **Rescate analgésico** según protocolo; comunicar si se repite; reevaluar |
| > 6 | Dolor muy intenso | `es_interp_dolor_muy_intenso` (`es_info_rango_mayor_6`) | **Actuación inmediata**: analgesia, aviso al equipo médico y reevaluación estrecha |

> Si el dolor **persiste a pesar del tratamiento**, hay que considerar otras posibles causas (`es_nota_persiste_dolor_tratamiento`).

Las puntuaciones seriadas permiten **valorar la respuesta al tratamiento** y ajustar la analgesia; deben registrarse junto con la intervención realizada (aspiración, cura, movilización) y la hora.

## Validez

La ESCID fue desarrollada y **validada psicométricamente en pacientes críticos adultos españoles** que no podían autoinformar el dolor, incluidos **pacientes en ventilación mecánica** (Latorre-Marco et al., Med Intensiva 2016). Los estudios de validación muestran **buenas propiedades psicométricas**: consistencia interna, fiabilidad interobservador y sensibilidad al cambio tras la analgesia, con capacidad para discriminar la presencia de dolor en el paciente no comunicativo.

Las guías **PADIS 2018** recomiendan el uso de escalas observacionales de dolor (como CPOT o BPS) en el paciente crítico que no puede autoinformar; la ESCID es la alternativa validada en español, avalada por el grupo de trabajo de la SEEIUC. No se incluyen cifras concretas de sensibilidad, especificidad o AUC porque varían según la población y el punto de corte; para el detalle psicométrico debe consultarse la publicación original.

## Limitaciones y errores frecuentes

- Es una escala **observacional**, por lo que puede haber **variabilidad entre valoradores**; conviene formar al equipo en su uso.
- En el paciente **bajo bloqueo neuromuscular** las conductas motoras no son valorables.
- Algunas conductas pueden confundirse con **delirium, ansiedad o disnea**; hay que integrar el resultado con el resto de la valoración clínica.
- No sustituye a la valoración del paciente que sí puede comunicarse (usar **EVA** en ese caso).
- La **analgesia previa** puede enmascarar las conductas; valorar antes del rescate cuando sea posible.
- El **tono muscular** requiere movilización pasiva y puede estar alterado por lesiones, espasticidad o rigidez de otra causa.
- El dolor **neuropático** puede no expresarse con estas conductas; valorar el contexto clínico.

## Ejemplo práctico resuelto

**Caso.** Varón de 58 años, en ventilación mecánica tras cirugía abdominal, con sedación ligera y sin comunicación verbal. Se valora antes de una cura de la herida.

- **Musculatura facial:** ceño fruncido y gesto de dolor → **1**.
- **«Tranquilidad»:** movimientos ocasionales de inquietud → **1**.
- **Tono muscular:** resistencia a la movilización pasiva del brazo → **1**.
- **Adaptación a la VM:** tose pero tolera el ventilador → **1**.
- **Confortabilidad:** se tranquiliza al hablarle, fácil de distraer → **1**.

**Total: 5 puntos → dolor moderado-grave (4-6).**

**Actuación de enfermería:** administrar el **rescate analgésico** prescrito **antes** de la cura, realizarla con técnica suave, **reevaluar la ESCID tras la analgesia y tras el procedimiento**, registrar el valor inicial y final, la hora y la intervención, y comunicar al equipo si el dolor se repite o persiste a pesar del tratamiento (en cuyo caso hay que buscar otras causas: infección de la herida, distensión, retención, etc.).

## Relación con otras escalas

- **EVA:** escala autoinformada; se usa cuando el paciente puede comunicarse.
- **CPOT:** escala observacional alternativa, muy extendida y recomendada por PADIS.
- **BPS:** otra escala observacional de dolor validada en UCI.
- **RASS:** la agitación puede deberse al dolor; valorar el dolor antes de aumentar la sedación.
- **CAM-ICU:** el dolor no controlado es un factor precipitante de delirium.
- **VAS (asincronía):** la lucha con el ventilador puede ser dolor, asincronía o ambas; hay que diferenciarlas.

## Puntos clave

- Valora el **dolor observacional** en el paciente crítico no comunicativo.
- **5 conductas** de **0 a 2** puntos; total **0-10**.
- **0** no dolor; **1-3** leve-moderado; **4-6** moderado-grave; **> 6** muy intenso.
- Valorar **en reposo y durante los procedimientos**.
- **Reevaluar tras la analgesia** para comprobar la respuesta.
- Es la alternativa **validada en español** a la EVA; recomendada por PADIS y SEEIUC.
- No es valorable con **bloqueo neuromuscular**.
- Si el dolor persiste pese al tratamiento, **buscar otras causas**.
