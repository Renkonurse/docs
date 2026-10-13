# Índice ROX (ROX Index · Respiratory Rate-Oxygenation Index)

> 📖 **Fuentes:** Roca O, Messika J, Caralt B, et al. *Predicting success of high-flow nasal cannula in pneumonia patients with hypoxemic respiratory failure: the utility of the ROX index.* J Crit Care. 2016;35:200-205. · Marino PL. *The ICU Book.* 4th ed. Wolters Kluwer.

## Qué mide y para qué sirve

El **índice ROX** predice la **respuesta a la oxigenoterapia de alto flujo (CNAF)** en el paciente con insuficiencia respiratoria hipoxémica aguda. Combina la **oxigenación** (SpO₂/FiO₂) con la **frecuencia respiratoria**, de modo que un valor alto indica buena respuesta y un valor descendente sugiere deterioro respiratorio y posible necesidad de **intubación**.

Sirve para:

- **Predecir el éxito o el fracaso de la CNAF** y decidir si el paciente puede mantenerse con este soporte.
- **Detectar precozmente el deterioro** respiratorio y anticipar la escalada de soporte (ventilación no invasiva o intubación).
- **Evitar intubaciones tardías** y también intubaciones innecesarias.
- **Objetivar la respuesta** al tratamiento y documentar la evolución.
- **Comunicar** de forma estandarizada la situación respiratoria entre turnos.

## Población diana

- **Pacientes adultos con insuficiencia respiratoria hipoxémica aguda** tratados con **cánula nasal de alto flujo**: neumonía, SDRA leve-moderado, insuficiencia respiratoria postoperatoria, etc.
- Es especialmente útil en la **neumonía** con hipoxemia, población en la que se desarrolló y validó.
- **No es aplicable** a la ventilación mecánica invasiva ni a otros dispositivos de oxigenoterapia convencional.
- Requiere que la **SpO₂ sea fiable** y que la FiO₂ administrada esté correctamente registrada.

## Cómo se puntúa

Fórmula que muestra la app (`es_rox_formula`):

**ROX = (SpO₂ / FiO₂) / FR**

| Entrada | Unidad / formato | Cadena en la app |
|---|---|---|
| SpO₂ | % (ej. 96) | `es_rox_label_spo2` |
| FiO₂ | **%** (ej. 21, 40, 60, 100); la app calcula FiO₂ en fracción dividiendo entre 100 | `es_rox_label_fio2` · `es_rox_fio2_hint` |
| FR | rpm | `es_frecuencia_respiratoria` · `es_rox_unit_rpm` |

> Nota de la app: `es_rox_fio2_fraction_note` recuerda que la FiO₂ se usa en fracción (0,21-1,0); por eso el campo se introduce en % y la app aplica la conversión.

**Momento de medida** (`es_rox_calculation_note`): se calcula a las **2, 6 y 12 horas** del inicio de la CNAF. Un valor descendente sugiere deterioro respiratorio y posible necesidad de intubación.

## Cómo explorar cada ítem (técnica)

1. **SpO₂.** Registrar la saturación **en el mismo momento** que la FiO₂ y la FR, con el paciente en reposo relativo y sin manipulación reciente. Comprobar que la señal es fiable (buena perfusión periférica, sin movimiento, sensor bien colocado).
2. **FiO₂.** Anotar la **FiO₂ real programada** en el dispositivo de alto flujo, expresada en **porcentaje** (21, 40, 60, 100). No estimarla «a ojo»: condiciona directamente el índice.
3. **Frecuencia respiratoria.** Contar las respiraciones durante **1 minuto completo**, con el paciente en reposo y sin dolor ni fiebre que la incrementen.
4. **Calcular el ROX** con los tres valores simultáneos y **repetirlo a las 2, 6 y 12 horas** del inicio de la CNAF y siempre ante cambios clínicos.
5. **Registrar la tendencia**: más importante que un valor aislado.

**Errores frecuentes:** usar una FiO₂ aproximada; medir SpO₂ y FiO₂ en momentos distintos; no comprobar la fiabilidad de la SpO₂; no repetir la medición a las 2, 6 y 12 h; y no integrar el índice con el trabajo respiratorio y la gasometría.

## Puntuación total e interpretación

| ROX | Significado | Cadena en la app | Actuación de enfermería |
|---|---|---|---|
| **> 4,88** | Éxito probable · buena respuesta a CNAF | `es_exito_probable` · `es_rox_success_detail` (`es_rox_range_success`) | Mantener la CNAF, vigilar la evolución y repetir el índice según protocolo |
| **3,85 - 4,88** | Zona intermedia · reevaluar en 2 h y valorar escalada | `es_rox_intermediate` · `es_rox_intermediate_detail` (`es_rox_range_intermediate`) | **Reevaluar en 2 horas**, vigilancia estrecha de FR, SpO₂, FiO₂ y trabajo respiratorio; avisar si empeora |
| **< 3,85** | Fracaso probable · considerar intubación / escalada de soporte | `es_rox_failure` · `es_rox_failure_detail` (`es_rox_range_failure`) | **Signo de alarma**: comunicar al equipo médico y preparar la escalada de soporte (ventilación no invasiva o intubación) |

Un ROX **> 4,88** a las 2-12 h apoya el **mantenimiento de la CNAF**. Un ROX **entre 3,85 y 4,88** obliga a **reevaluar en 2 horas**. Un ROX **< 3,85** es un signo de **alarma**. La **tendencia** es más informativa que un valor aislado: debe registrarse la serie temporal (2, 6 y 12 h) para detectar el deterioro precozmente.

## Validez

El índice ROX fue desarrollado y validado por **Roca et al. (J Crit Care 2016)** en **pacientes adultos con neumonía e insuficiencia respiratoria hipoxémica tratados con cánula nasal de alto flujo**. En el estudio original, un **ROX ≥ 4,88** medido a las 2, 6 y 12 horas del inicio de la CNAF se asoció a un **menor riesgo de intubación**, mientras que valores descendentes o inferiores a 3,85 se asociaron a mayor riesgo de fracaso del soporte.

El índice ha sido validado en cohortes posteriores y en distintos contextos de insuficiencia respiratoria hipoxémica, y es una de las herramientas más utilizadas para monitorizar la respuesta a la CNAF. No se incluyen cifras concretas de sensibilidad, especificidad o AUC porque varían según la población, el momento de medición y el desenlace evaluado; para el detalle debe consultarse la publicación original.

## Limitaciones y errores frecuentes

- Solo es aplicable a pacientes con **oxigenoterapia de alto flujo**; no es válido para ventilación mecánica convencional ni para otros dispositivos.
- Requiere que la **SpO₂ sea fiable** (buena perfusión, sin artefactos de movimiento o hipoperfusión periférica).
- La FiO₂ debe introducirse en **porcentaje** (21, 40, 60, 100) tal como pide la app, y corresponder al valor real administrado.
- Debe integrarse con el resto de la valoración respiratoria (gasometría, trabajo respiratorio, radiología) y no sustituye al juicio clínico.
- El índice **no incorpora el trabajo respiratorio** ni el uso de musculatura accesoria, que son claves en la decisión de intubar.
- En pacientes con **enfermedad pulmonar crónica con hipercapnia** la interpretación de la SpO₂ y de la FiO₂ puede requerir matices.
- La medición aislada es poco informativa: lo importante es la **tendencia** y la respuesta al ajuste de la FiO₂ y del flujo.

## Ejemplo práctico resuelto

**Caso.** Varón de 62 años con neumonía bilateral e insuficiencia respiratoria hipoxémica, iniciando cánula nasal de alto flujo a 50 L/min con FiO₂ 60 %.

- A las 2 horas: **SpO₂ 94 %**, **FiO₂ 60 %**, **FR 28 rpm**.
- **ROX = (94 / 0,60) / 28 = 156,7 / 28 = 5,6** → **> 4,88 → éxito probable**.

**Actuación de enfermería:** mantener la CNAF con la FiO₂ y el flujo programados, vigilar la tolerancia (FR, SpO₂, trabajo respiratorio, confort), **repetir el ROX a las 6 y 12 horas**, documentar la serie temporal y avisar al equipo si el índice desciende o aparece fatiga respiratoria. Si descendiera por debajo de 3,85, preparar la escalada de soporte.

## Relación con otras escalas

- **Índice de Tobin (RSBI):** valora el destete de la ventilación mecánica invasiva; el ROX valora la respuesta a la CNAF.
- **Murray (LIS):** cuantifica la gravedad de la lesión pulmonar/SDRA.
- **NEWS2:** alerta precoz de deterioro global, complementaria al ROX.
- **VAS (asincronía):** útil si el paciente pasa a ventilación mecánica.
- **SOFA:** valora la disfunción orgánica, incluida la respiratoria.

## Registro y comunicación

- Documentar el resultado con **fecha y hora** y el profesional que lo valora.
- Registrar los **datos que alimentan la puntuación** (no solo el total) para poder recalcularla.
- Anotar las **intervenciones realizadas** y la respuesta obtenida.
- Incluir el resultado en el **traspaso entre turnos** y comunicar los cambios relevantes al equipo médico.
- Reevaluar de forma **seriada** y registrar la tendencia.

## Autoevaluación rápida

1. ¿Qué mide y en quién se aplica? → La **respuesta a la cánula nasal de alto flujo** en el paciente con insuficiencia respiratoria hipoxémica.
2. ¿Cuál es su rango y su punto de corte? → **> 4,88** éxito probable; **3,85-4,88** zona intermedia; **< 3,85** fracaso probable.
3. ¿Qué hacer ante un resultado de riesgo (< 3,85)? → **Comunicar** al equipo y preparar la escalada de soporte (VNI o intubación).
4. ¿Cuándo se mide? → A las **2, 6 y 12 horas** del inicio de la CNAF y ante cambios clínicos.

## Preguntas frecuentes

- **¿Es válido en ventilación mecánica invasiva?** No: solo se aplica con CNAF.
- **¿Qué FiO₂ se introduce?** La **real** administrada, en porcentaje (21, 40, 60, 100).
- **¿Y si la SpO₂ no es fiable?** Repetir la medición con buena perfusión y sensor bien colocado.

## Puntos clave

- Predice la **respuesta a la cánula nasal de alto flujo** en la insuficiencia respiratoria hipoxémica.
- **ROX = (SpO₂ / FiO₂) / FR**, con la FiO₂ en fracción.
- **> 4,88** éxito probable; **3,85-4,88** intermedio; **< 3,85** fracaso probable.
- Se calcula a las **2, 6 y 12 horas** del inicio de la CNAF.
- Registrar la **FiO₂ real** y una **SpO₂ fiable** en el mismo momento.
- La **tendencia descendente** es un signo de alarma.
- No incorpora el **trabajo respiratorio**: integrarlo con la valoración clínica.
- Solo válido con **CNAF**, no con ventilación mecánica.
