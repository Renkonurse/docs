# Asincronía paciente-ventilador (VAS · índice de asincronía)

> 📖 **Fuentes:** Thille AW, Rodriguez P, Cabello B, Lellouche F, Brochard L. *Patient-ventilator asynchrony during assisted mechanical ventilation.* Intensive Care Med. 2006;32(10):1515-1522. · Marino PL. *The ICU Book.* 4th ed. Wolters Kluwer.

## Qué mide y para qué sirve

La **asincronía paciente-ventilador** es la discordancia entre el esfuerzo respiratorio del paciente y el ciclo que le entrega el ventilador. Se valora **en la gráfica del ventilador** (curvas de presión, flujo y volumen) y puede cuantificarse con el **índice de asincronía (IA)**, que expresa el **porcentaje de ciclos asincrónicos** respecto al total. Detectar y corregir la asincronía de forma precoz **mejora el confort, reduce la sedación y acorta la duración de la ventilación mecánica** (`es_vas_dialogo_descripcion`).

Sirve para:

- **Cuantificar** el grado de asincronía y decidir si es clínicamente significativa.
- **Identificar el tipo** de asincronía y orientar el ajuste del ventilador.
- **Guiar la sedoanalgesia**: la asincronía mantenida aumenta el trabajo respiratorio y el disconfort.
- **Prevenir complicaciones**: peor intercambio gaseoso, prolongación de la ventilación mecánica, mayor necesidad de sedación y lesión pulmonar inducida por el ventilador.
- **Documentar y comunicar** el problema al intensivista.

La app implementa la **calculadora del índice**: se introducen el **nº de asincronías** y la **FR total** (`es_vas_label_asincronias`, `es_vas_label_fr_total`) y devuelve el porcentaje con su interpretación.

## Población diana

- **Pacientes adultos en ventilación mecánica**, especialmente en **modos asistidos/espontáneos** (PSV, asistido-control, proporcional), donde el esfuerzo del paciente determina el ciclo.
- Pacientes con **destete difícil**, disconfort, lucha con el ventilador o mala tolerancia.
- Pacientes con **sedación ligera** (en sedación profunda la asincronía puede quedar enmascarada porque el paciente no genera esfuerzo).
- **No aplicable** en ventilación controlada con bloqueo neuromuscular (no hay esfuerzo del paciente) ni en pacientes sin registro de curvas.

## Cómo se puntúa

Fórmula que muestra la app (`es_vas_formula`):

**IA = (nº de asincronías / FR total) × 100**

El cálculo interno de la app usa como denominador el total de ciclos registrados:

**IA = asincronías / (FR total + asincronías) × 100**

Es decir, se contabilizan las respiraciones **sin** asincronía más las asíncronas. Se mide sobre el registro de la gráfica del ventilador durante un periodo representativo (habitualmente 1 minuto o varios ciclos consecutivos).

| Entrada | Significado | Cadena en la app |
|---|---|---|
| Nº de asincronías | Ciclos con asincronía detectados en la gráfica | `es_vas_label_asincronias` |
| FR total (respiraciones) | Respiraciones del periodo valorado | `es_vas_label_fr_total` |
| Resultado | Índice de asincronía en % | `TOTAL ASINCRONÍAS` (`es_vas_total_asincronias`) |

## Cómo explorar cada ítem (técnica)

El índice **no se explora en el paciente, sino en las curvas del ventilador**. Técnica:

1. **Seleccionar un periodo estable** de al menos **1 minuto**, sin manipulación del circuito, aspiración ni cambios de parámetros.
2. **Registrar las curvas** de presión, flujo y volumen (idealmente en pantalla congelada o con el registro del ventilador).
3. **Contar los ciclos totales** del periodo y **los ciclos asincrónicos**, identificando el tipo de asincronía en cada uno (ver tabla inferior).
4. **Calcular el IA** e interpretarlo.
5. **Repetir la medición** en distintos momentos del día y tras los ajustes, para valorar la respuesta.

### Tipos de asincronía y ajustes recomendados

> Estas fichas forman parte de los recursos de la app (`es_asincronia_*`) y sirven de guía para identificar el tipo de asincronía en la gráfica.

| Tipo | Qué se observa | Ajustes recomendados |
|---|---|---|
| **Disparo inefectivo** (`es_asincronia_disparo_inefectivo_nombre`) | Esfuerzo del paciente sin ciclo del ventilador (`..._desc`) | Reducir el trigger (más sensible, ej. −0,5 a −1 cmH₂O); valorar sedoanalgesia si hay esfuerzo excesivo; comprobar auto-PEEP; revisar la fuerza muscular |
| **Doble disparo** (`es_asincronia_doble_disparo_nombre`) | Dos ciclos seguidos tras un único esfuerzo (`..._desc`) | Aumentar el tiempo inspiratorio (Ti); valorar modo con ciclado por flujo; ajustar la sensibilidad del ciclado espiratorio; reducir la demanda ventilatoria (sedación, dolor) |
| **Auto-trigger** (`es_asincronia_auto_trigger_nombre`) | Ciclos del ventilador sin esfuerzo del paciente (`..._desc`) | Aumentar el umbral del trigger (menos sensible); buscar fugas en el circuito o en la cánula/TET; comprobar agua en las tubuladuras; descartar oscilaciones cardíacas (trigger cardíaco) |
| **Ciclado precoz o tardío** (`es_asincronia_ciclado_nombre`) | Ins/esp mal ajustados respecto al esfuerzo del paciente (`..._desc`) | Ciclado precoz → aumentar Ti o % de ciclado por flujo; ciclado tardío → reducir Ti o aumentar % de ciclado por flujo; valorar modo espontáneo (PSV); revisar sedoanalgesia y confort |
| **Flow starvation** (`es_asincronia_flow_starvation_nombre`) | Curva de flujo cóncava: el paciente «chupa» del ventilador (`..._desc`) | Aumentar el flujo inspiratorio (o rampa más rápida); cambiar a modo con flujo libre (PSV, PC); valorar dolor, ansiedad o fiebre; considerar sedoanalgesia |

**Antes de aumentar la sedación** hay que descartar causas corregibles: **dolor, hipoxemia, hipercapnia, auto-PEEP, secreciones, fugas, agua en el circuito y mal ajuste del trigger/Ti/flujo**.

## Puntuación total e interpretación

| Índice de asincronía | Significado | Cadena en la app | Actuación de enfermería |
|---|---|---|---|
| **≤ 10 %** | No significativa | `es_vas_interpretacion_no_significativa` (`es_vas_dialogo_nivel_no_significativa`) | Mantener parámetros; documentar y reevaluar periódicamente |
| **> 10 %** | **Significativa** | `es_vas_interpretacion_significativa` (`es_vas_dialogo_nivel_significativa`) | Revisar modo, trigger, Ti, flujo y sedoanalgesia; **comunicar al intensivista**; repetir la medición tras los ajustes |

El umbral del **10 %** es el criterio de asincronía significativa que aplica la app (clasificación `clasificacionAsincronia`: `> 10,0 %` → significativa) y coincide con el utilizado en la literatura para definir asincronía relevante.

## Validez

El índice de asincronía y su umbral del 10 % proceden del trabajo de **Thille et al. (Intensive Care Med 2006)**, realizado en **pacientes adultos en ventilación mecánica asistida**, donde se describió la prevalencia de la asincronía y su relación con la duración de la ventilación mecánica y el pronóstico. En ese estudio, la asincronía significativa (> 10 %) afectó a una proporción relevante de pacientes ventilados y se asoció a peor evolución.

La valoración de la asincronía requiere **interpretación experta de las curvas** del ventilador; su fiabilidad depende de la formación del observador. No se incluyen cifras concretas de sensibilidad, especificidad o AUC porque el índice no es una prueba diagnóstica, sino una medida cuantitativa de la interacción paciente-ventilador.

## Limitaciones y errores frecuentes

- La valoración requiere **experiencia en la interpretación de curvas** del ventilador; sin ellas el índice puede infravalorar el problema real.
- El índice es una **fotografía del momento**: deben repetirse las mediciones y compararlas con la evolución clínica.
- El registro debe hacerse con el paciente **estable y sin manipulación** del circuito (la aspiración, las fugas o los cambios de parámetros falsean el resultado).
- El **periodo de registro corto** puede no ser representativo; se recomienda al menos 1 minuto y, si es posible, varios periodos.
- En **sedación profunda** la asincronía puede no manifestarse porque el paciente no genera esfuerzo, aunque el ajuste sea inadecuado.
- La asincronía puede deberse a **factores del paciente** (dolor, ansiedad, secreciones, auto-PEEP) o del **ventilador** (trigger, Ti, flujo, fugas); hay que identificar la causa antes de ajustar.
- **No confundir** la asincronía con el dolor: ambas pueden coexistir y deben valorarse con sus escalas específicas (CPOT/ESCID).

## Ejemplo práctico resuelto

**Caso.** Varón de 60 años en ventilación mecánica en modo PSV durante el destete. La enfermera observa que el paciente «lucha» con el respirador y presenta disconfort.

- En el registro de 1 minuto se contabilizan **24 respiraciones** y **5 ciclos con doble disparo**.
- **IA = 5 / (24 + 5) × 100 = 17,2 %** → **asincronía significativa (> 10 %)**.

**Actuación de enfermería:** documentar el índice y el tipo (doble disparo), comprobar el dolor con CPOT/ESCID, revisar el Ti y el ciclado espiratorio con el equipo, descartar fugas y auto-PEEP, y **comunicar al intensivista**. Repetir la medición tras los ajustes para comprobar la mejoría; si el disconfort persiste, valorar sedoanalgesia una vez descartadas las causas corregibles.

## Relación con otras escalas

- **Índice de Tobin (RSBI):** valora el patrón respiratorio para el destete; la asincronía puede falsear la medición.
- **ROX:** valora la respuesta a la cánula nasal de alto flujo; no se aplica en ventilación mecánica invasiva.
- **CPOT y ESCID:** el dolor puede manifestarse como lucha con el ventilador; hay que valorarlo y tratarlo.
- **RASS:** graduúa la sedación y ayuda a interpretar el esfuerzo del paciente.
- **CAM-ICU:** el disconfort y la mala tolerancia favorecen el delirium.

## Registro y comunicación

- Documentar el resultado con **fecha y hora** y el profesional que lo valora.
- Registrar los **datos que alimentan la puntuación** (no solo el total) para poder recalcularla.
- Anotar las **intervenciones realizadas** y la respuesta obtenida.
- Incluir el resultado en el **traspaso entre turnos** y comunicar los cambios relevantes al equipo médico.
- Reevaluar de forma **seriada** y registrar la tendencia.

## Autoevaluación rápida

1. ¿Qué mide y en quién se aplica? → La **asincronía paciente-ventilador** en pacientes en ventilación mecánica asistida.
2. ¿Cuál es su rango y su punto de corte? → Índice de asincronía en %; **> 10 %** se considera significativa.
3. ¿Qué hacer ante un resultado de riesgo (> 10 %)? → Revisar modo, trigger, Ti, flujo y sedoanalgesia, y **comunicar al intensivista**.

## Puntos clave

- Mide la **discordancia entre el paciente y el ventilador** mediante el **índice de asincronía (IA)**.
- **IA ≤ 10 %** no significativa; **> 10 %** significativa.
- Se calcula **contando ciclos asincrónicos** en las curvas durante un periodo representativo.
- Los tipos principales son **disparo inefectivo, doble disparo, auto-trigger, ciclado precoz/tardío y flow starvation**.
- Cada tipo tiene **ajustes específicos**; identificar el tipo es tan importante como cuantificar el índice.
- Antes de sedar más, **descartar dolor, hipoxia, secreciones, fugas y auto-PEEP**.
- La asincronía mantenida **prolonga la ventilación mecánica** y empeora el confort.
- Requiere **formación en lectura de curvas** y registro seriado.
---
## Evidencia y referencias

- **Thille AW, et al.** Patient-ventilator asynchrony during assisted mechanical ventilation. *Intensive Care Med* 2006;32:1515-1522.
- **Blanch L, et al.** Validation of the Better Care system to detect ineffective efforts during expiration in mechanically ventilated patients. *Intensive Care Med* 2012.
- **Pham T, et al.** Asynchrony consequences and management. *Crit Care Clin* 2018.

> El índice cuantifica ciclos asincrónicos; un valor > 10 % se considera relevante, pero la interpretación depende del tipo de asincronía y de la clínica. No sustituye la lectura de las curvas.

---
## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **Asincronía (VAS)** | Porcentaje de ciclos asincrónicos |
| **Modos ventilatorios** | Ajuste de trigger, flujo y ciclado |
| **Alarmas respiratorias** | Deterioro y auto-PEEP |
| **Sedoanalgesia** | Confort y esfuerzo |
