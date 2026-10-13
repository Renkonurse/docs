# Escala A-DIVA (predicción de acceso venoso difícil)

> 📖 **Fuentes:** van Loon FHJ, Puijn LAPM, Houthoofd S, Bouwman ARA. *Development of the A-DIVA Scale: a clinical predictive scale to identify difficult intravenous access in adult patients based on clinical observations.* Medicine (Baltimore). 2016;95(16):e3428. · Lynn-McHale Wiegand DJ, ed. *AACN Procedure Manual for Critical Care.* 7th ed. Elsevier.

## Qué mide y para qué sirve

La **escala A-DIVA** es una escala **predictiva** que estima la **probabilidad de fallar en el primer intento de canalización venosa periférica** en el paciente adulto (`es_adiva_subtitle`, `es_adiva_dialog_subtitle`). Marca los **factores presentes**; **cada factor suma 1 punto** (`es_adiva_description`). El total va de **0 a 5** (`es_adiva_score_value`).

Sirve para:

- **Anticipar la dificultad de canalización** antes de intentar el acceso.
- **Decidir quién y con qué técnica** debe realizar la canalización (personal experto, ecografía).
- **Evitar múltiples punciones**, retrasos del tratamiento y disconfort para el paciente.
- **Optimizar los recursos** (material de ecografía, personal experto).
- **Documentar y comunicar** la dificultad prevista.

> La app advierte: *la escala se desarrolló en pacientes quirúrgicos; úsala como orientación, no como certeza* (`es_adiva_note`).

## Población diana

- **Pacientes adultos quirúrgicos** (población de desarrollo y validación de la escala) y, con cautela, otros pacientes adultos que requieran canalización venosa periférica.
- Es útil en **urgencias, quirófano, hospitalización y UCI**.
- Debe aplicarse **antes del primer intento** de canalización.
- **No está validada** específicamente en población pediátrica ni en neonatos.

## Cómo se puntúa

Instrucción de la app (`es_adiva_mark_factors_hint`): *marca los factores presentes en el paciente*. Cada factor marcado suma **1 punto**.

| # | Factor (1 punto cada uno) | Cadena en la app |
|---|---|---|
| 1 | La vena elegida **NO es palpable** | `es_adiva_vein_not_palpable` |
| 2 | La vena elegida **NO es visible** | `es_adiva_vein_not_visible` |
| 3 | **Antecedente de canalización venosa difícil** | `es_adiva_previous_difficult_cannulation` |
| 4 | **Indicación de cirugía no programada o urgencia** | `es_adiva_unplanned_surgery_urgency` |
| 5 | **Diámetro de la vena igual o menor de 2 mm** | `es_adiva_vein_diameter_le_2mm` |

### Total

| Concepto | Valor |
|---|---|
| Mínimo | 0 |
| Máximo | 5 |
| Registro en la app | `PUNTUACIÓN A-DIVA` (`es_adiva_score_label`) — `%1$d / 5` (`es_adiva_score_value`) |

## Cómo explorar cada ítem (técnica)

1. **Vena no palpable.** Con el **torniquete colocado** y el brazo en declive, **palpar** las venas del antebrazo y del dorso de la mano; si la vena elegida no se palpa, marcar el factor.
2. **Vena no visible.** **Inspeccionar** con buena iluminación; si la vena no se visualiza, marcar el factor.
3. **Antecedente de canalización difícil.** **Preguntar** al paciente por canalizaciones previas difíciles y revisar la historia clínica y el registro de accesos.
4. **Cirugía no programada o urgencia.** Comprobar el **contexto clínico**: intervención urgente o no programada.
5. **Diámetro ≤ 2 mm.** Estimar el **calibre venoso** por palpación/visualización; si se dispone de **ecografía**, medir el diámetro real y considerar el factor si es ≤ 2 mm.

**Errores frecuentes:** valorar sin torniquete o con poca luz; no preguntar por canalizaciones previas; estimar el calibre sin ecografía (puede infraestimar la dificultad); y aplicar la escala después de varios intentos fallidos (debe aplicarse **antes** del primer intento).

## Puntuación total e interpretación

| Puntuación | Riesgo | Fallo en el primer intento | Actuación de enfermería |
|---|---|---|---|
| **0-1** | Riesgo bajo (`es_adiva_low_risk`) | ≈ 5 % (`es_adiva_low_risk_failure`) | Canalización habitual (`es_adiva_low_risk_recommendation`) |
| **2-3** | Riesgo medio (`es_adiva_medium_risk`) | ≈ 37 % (`es_adiva_medium_risk_failure`) | Valorar **ecografía guiada** y **personal experto** (`es_adiva_medium_risk_recommendation`) |
| **4-5** | Riesgo alto (`es_adiva_high_risk`) | ≈ 93 % (`es_adiva_high_risk_failure`) | **Ecografía guiada y personal experto desde el primer intento** (`es_adiva_high_risk_recommendation`) |

Resumen que muestra la app (`es_adiva_range_low`, `es_adiva_range_medium`, `es_adiva_range_high`):

- 0-1 puntos · Riesgo bajo (≈ 5 % de fallo)
- 2-3 puntos · Riesgo medio (≈ 37 % de fallo)
- 4-5 puntos · Riesgo alto (≈ 93 % de fallo)

El resultado incluye la recomendación (`es_adiva_recommendation_label`: `Recomendación: %1$s`). La enfermera debe **registrar** los factores presentes, el número de intentos, la técnica utilizada y el resultado, para facilitar futuras canalizaciones y mejorar la práctica.

## Validez

La escala A-DIVA fue **desarrollada y validada por van Loon et al. (Medicine 2016)** en una población de **pacientes quirúrgicos adultos**, a partir de observaciones clínicas sencillas (visibilidad, palpabilidad, calibre venoso, antecedentes y contexto de urgencia). En la cohorte de validación, los grupos de riesgo mostraron **tasas de fallo en el primer intento del orden del 5 %, 37 % y 93 %**, tal como refleja la app, lo que demuestra una buena capacidad de discriminación en esa población.

Su aplicación en otras poblaciones (médicos, UCI, pediatría) no está validada específicamente, por lo que debe usarse como **orientación** (`es_adiva_note`). No se incluyen cifras de sensibilidad, especificidad o AUC porque varían según la población y el desenlace; para el detalle debe consultarse la publicación original.

## Limitaciones y errores frecuentes

- La escala se desarrolló y validó en **pacientes quirúrgicos** (`es_adiva_note`); en otras poblaciones su rendimiento puede diferir: debe usarse como **orientación, no como certeza**.
- Los factores son **observacionales** (palpación, visibilidad, diámetro estimado), por lo que la valoración puede variar entre profesionales.
- No recoge otros factores relevantes como la **hipovolemia, los edemas, la fragilidad cutánea, el historial de extravasaciones, la agitación** del paciente o la **quimioterapia reciente**.
- El diámetro venoso «≤ 2 mm» se estima clínicamente; con **ecografía** puede medirse con más precisión.
- No debe usarse para **justificar no intentar** el acceso: orienta sobre quién y cómo debe hacerlo.
- La puntuación debe aplicarse **antes del primer intento**; aplicarla después pierde valor predictivo.
- Escalas relacionadas: **Maddox** (`maddox.md`) y **VIP** (`vip.md`) para valorar las complicaciones una vez canalizado.

## Ejemplo práctico resuelto

**Caso.** Varón de 58 años que ingresa para cirugía urgente de abdomen agudo. En la valoración previa a la canalización: la vena del antebrazo no es palpable ni visible; refiere que en ingresos anteriores necesitaron varios intentos; y por ecografía el diámetro venoso es de 1,8 mm.

| Factor | ¿Presente? |
|---|---|
| Vena no palpable | Sí |
| Vena no visible | Sí |
| Antecedente de canalización difícil | Sí |
| Cirugía no programada / urgencia | Sí |
| Diámetro ≤ 2 mm | Sí |
| **Total** | **5 / 5** |

**Riesgo alto (4-5), con ≈ 93 % de fallo en el primer intento.**

**Actuación de enfermería:** solicitar **personal experto** y realizar la canalización con **ecografía guiada desde el primer intento**, preparar material alternativo (catéter adecuado, vena alternativa), explicar el procedimiento al paciente, registrar la puntuación, la técnica, el número de intentos y el resultado, y documentar el acceso para futuras canalizaciones.

## Relación con otras escalas

- **Maddox y VIP:** valoran la flebitis una vez canalizado el acceso.
- **NEWS2:** la urgencia clínica puede condicionar el contexto de canalización.
- **NEMS:** el uso de ecografía y personal experto incrementa el consumo de recursos.
- **Barthel/CFS:** en pacientes frágiles o dependientes la canalización puede ser más difícil.
- **RASS:** la agitación dificulta la canalización y aumenta el número de intentos.

## Puntos clave

- Predice el **fallo en el primer intento** de canalización venosa periférica.
- **5 factores** de **1 punto**; total **0-5**.
- **0-1** bajo (≈ 5 %); **2-3** medio (≈ 37 %); **4-5** alto (≈ 93 %).
- En riesgo alto-medio: **ecografía guiada y personal experto**.
- Aplicarla **antes del primer intento**.
- Desarrollada en **pacientes quirúrgicos**: usarla como orientación.
- Registrar factores, intentos, técnica y resultado.
- No sustituye al juicio clínico ni a la valoración del acceso.
