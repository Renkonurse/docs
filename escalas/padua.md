---
layout: default
title: "Escala de Padua (Padua Prediction Score · riesgo tromboembólico)"
---
# Escala de Padua (Padua Prediction Score · riesgo tromboembólico)

> 📖 **Fuentes:** Barbar S, Noventa F, Rossetto V, et al. *A risk assessment model for the identification of hospitalized medical patients at risk for venous thromboembolism: the Padua Prediction Score.* J Thromb Haemost. 2010;8(11):2450-2457. · MSD Manual Professional: https://www.msdmanuals.com/professional

## Qué mide y para qué sirve

La **escala de Padua** valora el **riesgo tromboembólico (TEV)** en el paciente **médico hospitalizado** (`es_padua_info_description`) y sirve para decidir la **profilaxis antitrombótica**. Instrucción de la app (`es_padua_prompt`): *marca los factores presentes. Punto de corte: ≥ 4 = alto riesgo*. Consta de **11 factores** con puntuaciones de 1, 2 o 3 puntos.

Sirve para:

- **Identificar al paciente médico con alto riesgo de TEV** (TVP/TEP).
- **Indicar la tromboprofilaxis** (farmacológica o mecánica) de forma protocolizada.
- **Evitar la profilaxis innecesaria** en pacientes de bajo riesgo.
- **Estandarizar la valoración** del riesgo tromboembólico al ingreso.
- **Documentar y comunicar** el riesgo entre profesionales.

## Población diana

- **Pacientes adultos médicos hospitalizados** (no quirúrgicos), especialmente en medicina interna, neumología, cardiología, oncología y enfermedades infecciosas.
- Es aplicable al **ingreso** y en las reevaluaciones durante la hospitalización.
- **No está validada específicamente** en pacientes quirúrgicos (existen otras escalas, como Caprini) ni en **UCI**, donde casi todos los pacientes críticos puntúan ≥ 4.
- No está diseñada para **población pediátrica** ni obstétrica.

## Cómo se puntúa

Se marca cada factor presente; los puntos se suman.

| # | Factor | Detalle (app) | Puntos |
|---|---|---|---|
| 1 | **Cáncer activo** (`es_padua_item_active_cancer`) | Metástasis o tratamiento en últimos 6 meses (`es_padua_detail_active_cancer`) | **3** |
| 2 | **TEV previo** (`es_padua_item_previous_vte`) | TVP, TEP previos (`es_padua_detail_previous_vte`) | **3** |
| 3 | **Movilidad reducida** (`es_padua_item_reduced_mobility`) | Cama o silla ≥ 3 días (`es_padua_detail_reduced_mobility`) | **3** |
| 4 | **Trombofilia conocida** (`es_padua_item_known_thrombophilia`) | Déficit de proteína C/S, antifosfolípidos, etc. (`es_padua_detail_known_thrombophilia`) | **3** |
| 5 | **Trauma / cirugía reciente** (`es_padua_item_recent_trauma_surgery`) | ≤ 1 mes (`es_padua_detail_recent_trauma_surgery`) | **2** |
| 6 | **Edad ≥ 70 años** (`es_padua_item_age_70`) | — | **1** |
| 7 | **Fallo cardíaco / respiratorio** (`es_padua_item_heart_respiratory_failure`) | Insuf. cardíaca o EPOC (`es_padua_detail_heart_respiratory_failure`) | **1** |
| 8 | **IAM o ACV isquémico agudo** (`es_padua_item_acute_mi_ischemic_stroke`) | — | **1** |
| 9 | **Infección / enfermedad reumática** (`es_padua_item_infection_rheumatic_disease`) | Infección aguda o artritis reumatoide (`es_padua_detail_infection_rheumatic_disease`) | **1** |
| 10 | **Obesidad (IMC ≥ 30)** (`es_padua_item_obesity`) | — | **1** |
| 11 | **Tratamiento hormonal** (`es_padua_item_hormonal_treatment`) | Anticonceptivos, TRH, tamoxifeno, etc. (`es_padua_detail_hormonal_treatment`) | **1** |

### Total

| Concepto | Valor |
|---|---|
| Mínimo | 0 |
| Máximo | 20 (3+3+3+3+2+1+1+1+1+1+1) |
| Registro en la app | `TOTAL PADUA` (`es_padua_total`) |

## Cómo explorar cada ítem (técnica)

1. **Cáncer activo.** Revisar el diagnóstico oncológico: metástasis conocidas o tratamiento oncológico (quimioterapia, radioterapia, cirugía) en los **últimos 6 meses**.
2. **TEV previo.** Preguntar y revisar la historia por **TVP o TEP** previos; es un factor de alto peso.
3. **Movilidad reducida.** Valorar si el paciente permanece en **cama o silla ≥ 3 días** (incluye la situación previa al ingreso si es reciente).
4. **Trombofilia conocida.** Buscar antecedentes de **déficit de proteína C/S, antitrombina, antifosfolípidos, factor V Leiden** u otras trombofilias documentadas.
5. **Trauma / cirugía reciente.** Comprobar si ha habido **traumatismo o cirugía en el último mes**.
6. **Edad ≥ 70 años.** Comprobar en la historia.
7. **Fallo cardiaco o respiratorio.** Revisar el diagnóstico de **insuficiencia cardiaca o EPOC**.
8. **IAM o ACV isquémico agudo.** Comprobar si el ingreso actual o reciente incluye **infarto agudo de miocardio o ictus isquémico**.
9. **Infección o enfermedad reumática.** Valorar la presencia de **infección aguda o artritis reumatoide**.
10. **Obesidad.** Calcular el **IMC** (≥ 30).
11. **Tratamiento hormonal.** Preguntar por **anticonceptivos, terapia hormonal sustitutiva, tamoxifeno** u otros.

**Errores frecuentes:** no revisar la medicación hormonal; no confirmar el antecedente de TEV; estimar la movilidad sin referirse a los 3 días; y no valorar el **riesgo hemorrágico** antes de indicar la profilaxis.

## Puntuación total e interpretación

| Puntos | Riesgo | Etiqueta de la app | Actuación de enfermería |
|---|---|---|---|
| **0-3** | Bajo riesgo TEV | `es_padua_low_risk_tev` (`es_padua_info_range_low`) | No precisa profilaxis farmacológica sistemática; **movilización precoz** y reevaluación |
| **≥ 4** | **ALTO RIESGO TEV — profilaxis recomendada** | `es_padua_high_risk_tev` (`es_padua_info_range_high`) | Aplicar **tromboprofilaxis** según protocolo (HBPM ajustada a función renal, o medidas mecánicas si está contraindicada) y vigilar complicaciones |

> Nota de la app (`es_padua_info_note`): *en UCI casi todo crítico puntúa ≥ 4. Reevaluar al alta de UCI.*

La enfermera participa aplicando y vigilando la profilaxis: **heparinas de bajo peso molecular** (ajustadas a la función renal), **compresión neumática intermitente o medias de compresión** cuando la profilaxis farmacológica está contraindicada, y **movilización precoz**. La valoración incluye la **vigilancia de signos de TVP/TEP** (dolor y edema de extremidad, disnea, dolor torácico) y de **complicaciones hemorrágicas** de la profilaxis.

## Validez

La escala de Padua fue desarrollada y validada por **Barbar et al. (J Thromb Haemost 2010)** en una cohorte de **pacientes médicos hospitalizados**, con el objetivo de identificar a los que se benefician de tromboprofilaxis. En el estudio de validación, el grupo de **alto riesgo (≥ 4 puntos)** presentó una **incidencia de TEV significativamente mayor** que el de bajo riesgo, y la escala mostró capacidad para discriminar el riesgo tromboembólico.

Está incluida en las **recomendaciones de tromboprofilaxis** de las principales guías (ACCP/CHEST) para el paciente médico hospitalizado. No se incluyen cifras concretas de sensibilidad, especificidad o AUC porque varían según la población, la definición de TEV y el seguimiento; para el detalle debe consultarse la publicación original.

## Limitaciones y errores frecuentes

- Está diseñada y validada en **pacientes médicos hospitalizados**; su aplicación en **UCI** o en pacientes quirúrgicos no está validada específicamente (en UCI prácticamente todos puntúan ≥ 4, lo que limita su capacidad de discriminación).
- Algunos factores son **difíciles de precisar** en el paciente crítico (inmovilización previa, tratamiento hormonal) y pueden **infraestimar** el riesgo.
- No sustituye a la valoración individual del **riesgo hemorrágico** antes de iniciar la profilaxis.
- No incorpora **parámetros analíticos** (D-dímero, trombofilia no conocida) ni la **duración** del riesgo.
- El riesgo **cambia con la evolución** del paciente: debe reevaluarse al ingreso, ante cambios clínicos y **al alta de UCI**.
- La definición de «movilidad reducida» puede aplicarse de forma variable entre profesionales.

## Ejemplo práctico resuelto

**Caso.** Mujer de 74 años ingresada por neumonía. Antecedentes: EPOC, obesidad (IMC 32), tratamiento hormonal sustitutivo. Permanece encamada desde el ingreso (3 días).

| Factor | Puntos |
|---|---|
| Edad ≥ 70 años | 1 |
| Fallo respiratorio (EPOC) | 1 |
| Obesidad (IMC ≥ 30) | 1 |
| Tratamiento hormonal | 1 |
| Movilidad reducida (cama ≥ 3 días) | 3 |
| **Total** | **7** |

**Alto riesgo TEV (≥ 4) → profilaxis recomendada.**

**Actuación de enfermería:** administrar la **HBPM** prescrita (comprobar dosis y función renal), valorar el **riesgo hemorrágico**, vigilar signos de **sangrado** y de **TVP/TEP**, fomentar la **movilización precoz** y las medidas mecánicas si procede, y **reevaluar la escala** al alta de la unidad o ante cambios clínicos. Registrar el total y las medidas aplicadas.

## Relación con otras escalas

- **SOFA:** valora la disfunción orgánica; en UCI sustituye al Padua como parte de la valoración de gravedad.
- **NEWS2:** alerta precoz de deterioro global.
- **NEMS:** la profilaxis y la vigilancia incrementan la carga de enfermería.
- **Braden/EMINA:** la inmovilidad es un factor común de riesgo de UPP y de TEV.
- **MRC Sum Score:** la debilidad adquirida prolonga la inmovilidad y el riesgo trombótico.

## Puntos clave

- Valora el **riesgo tromboembólico** en el paciente **médico hospitalizado**.
- **11 factores** con puntuaciones de **1, 2 o 3**; total **0-20**.
- **0-3** bajo riesgo; **≥ 4** alto riesgo y **profilaxis recomendada**.
- Se calcula **al ingreso** y se **reevalúa** con la evolución y al alta de UCI.
- Antes de profilaxis, valorar el **riesgo hemorrágico**.
- Vigilar **signos de TVP/TEP y de sangrado**.
- En **UCI** casi todos puntúan ≥ 4: su capacidad de discriminación es limitada.
- Complementar con **movilización precoz** y medidas mecánicas si procede.

---

## Evidencia y referencias

- **Barbar S, et al.** A risk assessment model for the identification of hospitalized medical patients at risk for venous thromboembolism: the Padua Prediction Score. *J Thromb Haemost* 2010;8:2450-2457.
- **Konstantinides SV, et al.** 2019 ESC Guidelines for the diagnosis and management of acute pulmonary embolism. *Eur Heart J* 2020;41:543-603.
- **ACCP.** Antithrombotic therapy for VTE disease: CHEST Guideline. 2016 (actualización).

> La escala identifica riesgo trombótico; no valora el riesgo de sangrado. La decisión de profilaxis debe equilibrar ambos y ajustarse a la función renal y al contexto.

---

## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **Escala de Padua** | Riesgo tromboembólico |
| **Profilaxis de TEV** | Medidas mecánicas y farmacológicas |
| **Sangrado** | Contraindicaciones y vigilancia |
| **Cuidados de enfermería** | Movilización y registro |
