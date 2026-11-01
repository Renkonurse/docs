---
layout: default
title: "Corrección de iones y metabolismo"
---
# Corrección de iones y metabolismo

> 📖 **Fuentes:** UK Kidney Association. Clinical Practice Guideline: Management of Hyperkalaemia in Adults (2023): https://www.ukkidney.org/health-professionals/guidelines · KDIGO CKD-MBD Update (2017): https://kdigo.org/guidelines/ckd-mbd/ · Society for Endocrinology. Emergency management of acute hypocalcaemia (2016): https://www.endocrinology.org/clinical-practice/clinical-guidance/ · Berend K, et al. *N Engl J Med*. 2014;371:1434-1445.

El módulo **Iones y Metabólico** (`feature_iones`) agrupa cinco pantallas, más la pantalla F1 de corrección:

| Pantalla | Clase | Contenido |
|---|---|---|
| **Potasio** | `PotasioActivity` | Hipo/hiperpotasemia, riesgo ECG, déficit estimado y corrección |
| **Magnesio y Fósforo** | `MagnesioFosforoActivity` | Hipo/hipermagnesemia e hipo/hiperfosfatemia, reposición y producto Ca × P |
| **Calcio** | `CalcioActivity` | Ca total/corregido/iónico, clasificación y calculadora de ampollas |
| **Sodio** | `SodioActivity` | Hipo/hipernatremia, Na corregido, agua libre (ver [sodio y agua libre](sodio-agua-libre.html)) |
| **Osmolaridad y Metabólico** | `OsmolaridadMetabolicoActivity` | Osmolaridad, gap osmolar, anión gap, delta-delta, brecha urinaria, lactato y glucemia |
| **Corrección de iones (K/Mg/PO₄)** (F1) | `CorreccionIonesActivity` | Resumen de protocolo: vías, velocidades y contraindicaciones |

---

## 1. Potasio (`PotasioActivity`)

### Datos

| Campo | Unidad | Notas |
|---|---|---|
| **Potasio sérico** | mEq/L | Obligatorio |
| **Peso** | kg | Opcional (para el déficit estimado) |
| **Hallazgos ECG** | casillas | Opcional; si se marcan, la situación se considera **GRAVE** |

### Fórmulas y clasificación exactas

```
Déficit estimado de K (mEq) = (4,0 − K) × 100        [solo si K < 4,0]
```

> **Estimación teórica, no dosis de reposición:** el déficit corporal no puede deducirse con precisión de una regla fija por cada 1 mEq/L. No calcular ni administrar un reemplazo total automático; individualizar con controles.

`clasificarK()`:

| K (mEq/L) | Categoría |
|---|---|
| **< 2,5** | Hipopotasemia GRAVE |
| **2,5-2,9** | Hipopotasemia MODERADA |
| **3,0-3,4** | Hipopotasemia LEVE |
| **3,5-5,0** | Normopotasemia |
| **5,1-6,0** | Hiperpotasemia LEVE |
| **6,1-6,5** | Hiperpotasemia MODERADA |
| **> 6,5** | Hiperpotasemia GRAVE |

### Hallazgos ECG (casillas de la app)

**Sugerentes de hipopotasemia:** onda U prominente · aplanamiento/inversión de onda T · descenso del segmento ST · QT largo · extrasístoles/arritmias auriculares o ventriculares.

**Sugerentes de hiperpotasemia:** onda T picuda y estrecha (*tenting*) · PR prolongado · QRS ancho · pérdida de onda P · patrón *sine wave* · bradicardia/parada.

> *«Con alteraciones ECG, la situación se considera GRAVE → actuar ya.»*

### Reposición (orientación de seguridad)

| Vía | Velocidad máxima |
|---|---|
| **Cualquier acceso** | Concentración, velocidad y monitorización según preparado, prescripción y protocolo institucional; no usar límites de esta tabla como pauta universal |

- Vía y pauta dependen de síntomas, ECG, causa, pérdidas en curso, función renal, tolerancia oral y preparado; reposición IV de K es de alto riesgo.
- Monitorización ECG y repetición de K según gravedad, tratamiento y protocolo; tener en cuenta retraso de laboratorio, redistribución y rebote.
- Valorar Mg concomitante si hipopotasemia refractaria. Con digoxina, alteraciones electrolíticas requieren valoración clínica cuidadosa.

**Hiperpotasemia (principios de seguridad):**

1. Considerar pseudohiperpotasemia y repetir muestra si procede, **sin retrasar** la atención urgente ante síntomas, ECG compatible o valor gravemente elevado.
2. ECG/monitorización y evaluación urgente según gravedad; revisar fármacos contribuyentes con el equipo prescriptor, no suspenderlos automáticamente.
3. Tratamiento de urgencia (estabilización de membrana si está indicada, redistribución y eliminación) según guía vigente, formulación/ficha técnica y protocolo local. Calcio IV no reduce el K; las presentaciones de gluconato y cloruro no son intercambiables por volumen.
4. Insulina-glucosa puede causar hipoglucemia tardía; especificar pauta, concentración, controles de glucemia y vigilancia del K conforme al protocolo. Beta-agonistas son coadyuvantes; bicarbonato y diuréticos no son universales.
5. Planificar eliminación definitiva del K y valorar terapia renal sustitutiva urgente cuando esté indicada. Captores/resinas dependen del producto y no sustituyen medidas inmediatas.

### Ejemplo

K **2,8 mEq/L**, 70 kg:

```
Déficit ≈ (4,0 − 2,8) × 100 = 120 mEq
```

No convertir el déficit teórico en una dosis. La vía, cantidad y velocidad se prescriben según respuesta y límites del preparado/protocolo.

---

## 2. Magnesio (`MagnesioFosforoActivity`, pestaña Magnesio)

### Datos

| Campo | Unidad | Notas |
|---|---|---|
| **Magnesio sérico** | mg/dL **o** mmol/L | Convertible: **1 mmol/L = 2,43 mg/dL** |
| **Peso** | kg | Opcional, para la reposición |
| **Síntomas de hipomagnesemia** | casillas | Si hay alguno → tratar como GRAVE |

**Síntomas:** torsades de pointes / TV polimorfa · QT largo · calambres/fasciculaciones · tetania/signo de Trousseau · arritmias · **hipopotasemia refractaria** · **hipocalcemia refractaria**.

### Fórmulas y clasificación exactas

```
Conversión: mg/dL = mmol/L × 2,43

Reposición estimada de sulfato de magnesio (g):
    Aplicación: estimación matemática heredada; no es una fórmula validada de dosis ni sustituye prescripción.
```

`clasificarMg()`:

| Mg (mg/dL) | Categoría |
|---|---|
| **< 1,0** | Hipomagnesemia GRAVE |
| **1,0-1,3** | Hipomagnesemia GRAVE |
| **1,4-1,6** | GRAVE si hay síntomas · si no, MODERADA |
| **1,7-2,2** | Normomagnesemia |
| **2,3-4,0** | Hipermagnesemia LEVE |
| **4,1-6,0** | Hipermagnesemia MODERADA |
| **> 6,0** | Hipermagnesemia GRAVE |

### Reposición (recomendaciones de la app)

| Gravedad | Actuación |
|---|---|
| Cualquier gravedad | Tratamiento, preparación, monitorización y repetición dependen de síntomas, causa, función renal, vía y protocolo. Hipomagnesemia sintomática grave/torsades es una emergencia: activar algoritmo específico. |

Valorar alteraciones concomitantes y corregirlas si están indicadas; el magnesio puede contribuir a hipopotasemia/hipocalcemia refractarias. En torsades, seguir el algoritmo de reanimación vigente.

**Hipermagnesemia:** valorar síntomas, exposición, función renal y ECG. El tratamiento de toxicidad grave, calcio IV, fluidos/diuréticos o diálisis requiere indicación clínica y protocolo; evitar recomendaciones automáticas.

---

## 3. Fósforo (`MagnesioFosforoActivity`, pestaña Fósforo)

### Datos

| Campo | Unidad | Notas |
|---|---|---|
| **Fósforo sérico** | mg/dL **o** mmol/L | Convertible: **1 mmol/L = 3,10 mg/dL** |
| **Calcio total** | mg/dL | Opcional, para el **producto Ca × P** |
| **Peso** | kg | Para la reposición |

### Fórmulas y clasificación exactas

```
Conversión: mg/dL = mmol/L × 3,10

Reposición de fósforo (mmol):
    si P < 2,0 mg/dL y hay peso:
        mmol = peso × 0,16 × ((2,5 − P) / 2,5)     [el factor se acota entre 0,3 y 1,0]

Producto Ca × P (mg²/dL²) = Ca (mg/dL) × P (mg/dL)
    producto calculado para contexto; no usar como objetivo o umbral terapéutico aislado
```

`clasificarP()`:

| P (mg/dL) | Categoría |
|---|---|
| **< 1,0** | Hipofosfatemia GRAVE |
| **1,0-1,4** | Hipofosfatemia MODERADA |
| **1,5-2,4** | Hipofosfatemia LEVE |
| **2,5-4,5** | Normofosfatemia |
| **4,6-6,0** | Hiperfosfatemia LEVE |
| **6,1-8,0** | Hiperfosfatemia MODERADA |
| **> 8,0** | Hiperfosfatemia GRAVE |

> El resultado de cálculo no es una dosis validada ni una prescripción. En enfermedad renal crónica interpretar fósforo, calcio y PTH conjuntamente conforme a KDIGO; no usar un producto Ca × P aislado como objetivo universal.

### Reposición y cuidados

- Hipofosfatemia: ruta y reposición dependen de síntomas, magnitud, tolerancia, función renal y formulación; fosfato IV es de alto riesgo. Vigilar fósforo, Ca, K, Na, Mg y función renal según pauta.
- Riesgo de realimentación: seguir guía específica; valorar tiamina y monitorización/reposición de electrolitos según riesgo, no aplicar dosis universal por antecedente aislado de alcohol.
- Hiperfosfatemia: tratar causa y valorar dieta/captores/diálisis según enfermedad renal, síntomas y protocolo. No usar producto Ca×P como criterio único.

---

## 4. Calcio (`CalcioActivity`)

### Datos

| Campo | Unidad | Notas |
|---|---|---|
| **Ca total** | mg/dL | Al menos uno de los dos (total o iónico) |
| **Albúmina** | g/dL | Opcional, para corregir el Ca total |
| **Ca iónico** | mg/dL **o** mmol/L | Convertible: **1 mmol/L = 4,008 mg/dL** |
| **Síntomas de hipocalcemia** | casillas | Si hay alguno → tratar como GRAVE |

**Síntomas:** Chvostek · Trousseau · parestesias peribucales o en manos/pies · espasmos carpopedales · QT largo · convulsiones · laringoespasmo/estridor · hipotensión refractaria.

### Fórmulas exactas

```
Ca iónico (mg/dL) = Ca iónico (mmol/L) × 4,008

Ca corregido (mg/dL) = Ca total + 0,8 × (4,0 − albúmina)

Valor usado para clasificar (prioridad):
    1.º Ca iónico  →  2.º Ca corregido  →  3.º Ca total
```

`clasificarCa()`:

| Categoría | Ca **total** (mg/dL) | Ca **iónico** (mg/dL) |
|---|---|---|
| **Hipocalcemia GRAVE** | < 7,5 | < 4,0 |
| **Hipocalcemia MODERADA** (GRAVE si síntomas) | 7,5-8,4 | 4,0-4,5 |
| **Normocalcemia** | 8,5-10,5 | 4,6-5,3 |
| **Hipercalcemia LEVE** | 10,6-12,0 | 5,4-6,0 |
| **Hipercalcemia MODERADA** | 12,1-14,0 | > 6,0 |
| **Hipercalcemia GRAVE** | > 14,0 | — |

> *«Con síntomas → tratar como GRAVE aunque el valor no sea extremo.»*
> *«Sin albúmina no se puede corregir. En pacientes críticos, hipoalbuminémicos o con IRA, el Ca iónico es más fiable.»*
> **Hipoalbuminemia:** la corrección del Ca total puede sobreestimar el Ca real → guiarse por el **iónico**.

### Calculadora de ampollas (Ca ELEMENTAL, no la sal)

| Presentación | Ca elemental por ampolla de 10 mL (1 g de sal) |
|---|---|
| **Gluconato cálcico 10 %** | **90 mg** (= **2,25 mmol**) |
| **Cloruro cálcico 10 %** | **273 mg** (= **6,8 mmol**) |

```
Ca elemental (mg)  = n.º de ampollas × 90    (gluconato)
                     n.º de ampollas × 273   (cloruro)
Ca elemental (mmol) = n.º de ampollas × 2,25 (gluconato)
                      n.º de ampollas × 6,8  (cloruro)
```

### Tratamiento sugerido (app)

- Calcio total corregido por albúmina es una estimación imperfecta, especialmente en enfermedad crítica; cuando la decisión clínica lo requiera, valorar calcio iónico y contexto ácido-base.
- Hipocalcemia sintomática o grave: emergencia; seleccionar sal, vía, dosis y monitorización según guía, acceso, función renal y protocolo. El cloruro cálcico es más irritante; no intercambiar volúmenes de cloruro y gluconato.
- Hipercalcemia: evaluar causa, síntomas, volemia, función renal y fármacos. Hidratación, calcitonina, antiresortivos, glucocorticoides o diálisis dependen de etiología/gravedad y requieren indicación individual; no aplicar pauta universal de fluidos o fármacos.

### Ejemplo

Ca total **7,8 mg/dL**, albúmina **2,5 g/dL**:

```
Ca corregido = 7,8 + 0,8 × (4,0 − 2,5) = 7,8 + 1,2 = 9,0 mg/dL   → normocalcemia
```

Sin la corrección, el Ca total parecía una hipocalcemia moderada; con albúmina baja, el valor corregido es normal.

---

## 5. Osmolaridad y Metabólico (`OsmolaridadMetabolicoActivity`)

### Datos

Sodio, cloro, bicarbonato, potasio (opcional, para AG con K), glucosa, BUN (urea en mg/dL), albúmina (para AG corregido) y **osmolaridad medida** (opcional, para el gap). Cálculo avanzado opcional: **brecha urinaria** con Na, K y Cl en orina.

### Fórmulas exactas

```
Osmolaridad calculada (mOsm/kg) = 2 × Na + glucosa/18 + BUN/2,8
Osmolaridad efectiva  (mOsm/kg) = 2 × Na + glucosa/18
Gap osmolar                     = osmolaridad medida − osmolaridad calculada

Anión gap (AG)          = Na − (Cl + HCO₃)
AG con K                = (Na + K) − (Cl + HCO₃)
AG corregido            = AG + 2,5 × (4,0 − albúmina)

Delta-delta (ΔAG/ΔHCO₃) = (AG − 12) / (24 − HCO₃)      [solo si HCO₃ < 24]

Brecha urinaria = (Na orina + K orina) − Cl orina
```

### Interpretación

**Osmolaridad** (normal 275-295 mOsm/kg; efectiva con tramo de aviso hasta 305):

| Valor | Color |
|---|---|
| < 275 | Naranja (baja) |
| 275-295 | Verde (normal) |
| 296-320 | Amarillo |
| > 320 | Rojo |

**Gap osmolar:**

| Valor | Lectura |
|---|---|
| **> 20** | Sospechar tóxicos (metanol, etilenglicol, isopropanol) o cetoacidosis |
| **10-20** | Rango dudoso: correlacionar con clínica |
| **≤ 10** | Normal |

**Anión gap** (normal **8-12 mEq/L**):

| Delta-delta | Interpretación |
|---|---|
| **< 0,4** | Acidosis metabólica hiperclorémica (AG normal + HCO₃ bajo): buscar pérdidas GI o ATR |
| **0,4-1,0** | Acidosis metabólica mixta: AG alto con componente hiperclorémico |
| **1,0-2,0** | Acidosis metabólica de AG alto pura (proporcional) |
| **> 2,0** | Acidosis metabólica de AG alto + alcalosis metabólica asociada (ΔHCO₃ < ΔAG) |

**Brecha urinaria:** **negativa (< 0)** → pérdidas gastrointestinales de bicarbonato (diarrea, íleo, fístula); **cercana a 0** → valorar contexto; **positiva (> 0)** → sugiere **acidosis tubular renal (ATR)** tipo 1 o 2.

> ℹ️ La pantalla de **Gasometría** usa unos rótulos ligeramente distintos para el delta-delta (mismos cortes numéricos): *< 0,4* hiperclorémica añadida · *0,4-1,0* acidosis metabólica pura (AG elevado) · *1,0-2,0* acidosis metabólica + alcalosis metabólica · *> 2* alcalosis metabólica predominante. Ver [gasometría](gasometria.html).

**Lactato:**

| Valor | Lectura |
|---|---|
| **< 2,0 mmol/L** | Normal |
| **2,0-3,9** | Elevado: buscar hipoperfusión, sepsis, hipoxia, convulsiones; vigilar tendencia |
| **≥ 2,0** | Elevado: interpretar tendencia, contexto, aclaramiento y causa; no equivale por sí solo a hipoperfusión |

**Glucemia:**

| Valor | Lectura |
|---|---|
| **< 54 mg/dL** | Hipoglucemia clínicamente significativa; tratar de inmediato según estado de consciencia, acceso y protocolo; reevaluar pronto |
| **54-69** | Hipoglucemia: regla **15/15** (15 g HC, medir a los 15 min) |
| **70-100** | Normal en ayunas |
| **101-125** | Alterada en ayunas (prediabetes) |
| **126-250** | Hiperglucemia: confirmar con HbA1c; pauta correctora del centro |
| **251-400** | Hiperglucemia marcada: descartar CAD/EHH |
| **> 400** | Hiperglucemia marcada: evaluar síntomas, cetonas, estado ácido-base, osmolaridad y volumen; no indica por sí sola fluidos agresivos ni insulina IV |

### Ejemplo

Na 138, glucosa 180, BUN 28 (mOsm medida 300):

```
Osm calculada = 2×138 + 180/18 + 28/2,8 = 276 + 10 + 10 = 296 mOsm/kg
Osm efectiva  = 276 + 10 = 286 mOsm/kg
Gap osmolar   = 300 − 296 = 4  → normal
```

---

## 6. Valores de referencia (pantalla `ValoresReferenciaActivity`)

### Electrolitos

| Parámetro | Rango normal | Valores críticos |
|---|---|---|
| **Sodio (Na)** | 135-145 mEq/L | **< 120 o > 160** |
| **Potasio (K)** | 3,5-5,0 mEq/L | **< 2,5 o > 6,5** |
| **Cloro (Cl)** | 98-107 mEq/L | — |
| **Calcio total** | 8,5-10,5 mg/dL | **< 7,0 o > 13,0** |
| **Calcio iónico** | 4,6-5,3 mg/dL | — |
| **Magnesio (Mg)** | 1,7-2,2 mg/dL | **< 1,0 o > 4,0** |
| **Fósforo (P)** | 2,5-4,5 mg/dL | **< 1,0 o > 8,0** |
| **Producto Ca × P** | No usar como objetivo terapéutico aislado | — |

### Metabólico

| Parámetro | Rango normal | Notas |
|---|---|---|
| **Glucosa en ayunas** | 70-100 mg/dL | Prediabetes 100-125 · DM ≥ 126 · crítico < 40 o > 400 |
| **Lactato** | < 2,0 mmol/L (orientativo) | Interpretar en contexto y tendencia; el valor aislado no define shock ni respuesta a fluidos |
| **Osmolaridad** | 275-295 mOsm/kg | — |
| **Anión gap** | 8-12 mEq/L | AG corregido por albúmina disponible |
| **Delta-delta** | 1,0-2,0 | — |
| **Brecha urinaria** | Sin rango universal | Interpretación limitada por amonio urinario, función renal y contexto; no diagnostica ATR por sí sola |
| **Urea (BUN)** | 7-20 mg/dL | — |
| **Creatinina** | varón 0,7-1,2 · mujer 0,5-1,0 mg/dL | — |
| **Albúmina** | 3,5-5,0 g/dL | — |

### Conversiones rápidas

| Magnitud | Equivalencia |
|---|---|
| Magnesio | 1 mmol/L = **2,43 mg/dL** |
| Fósforo | 1 mmol/L = **3,10 mg/dL** |
| Calcio | 1 mmol/L = **4,008 mg/dL** |

> **Filas con fondo rojo suave = valores críticos (avisar al médico).**

---

## 7. Pantalla F1 «Corrección de iones (K/Mg/PO₄)»

Resumen de protocolo que muestra la pantalla:

| Ion | Protocolo de la app |
|---|---|
| **Potasio (K)** | Alto riesgo: vía, concentración, velocidad y monitorización según prescripción, preparado y protocolo institucional. |
| **Magnesio (Mg)** | Individualizar preparación, velocidad, controles y ajuste renal según indicación y protocolo. |
| **Fosfato (PO₄)** | Alto riesgo: preparación y acceso según concentración/osmolaridad y protocolo del centro. |
| **Contraindicaciones y precauciones** | Separar siempre el resultado analítico del protocolo de reposición y de las contraindicaciones (**oliguria, insuficiencia renal, hiperpotasemia…**). **Revaluar antes de repetir dosis.** |

---

## 8. Cuidados de enfermería y reglas de seguridad

- **Corregir despacio** y con **monitorización ECG** en las alteraciones graves (K, Mg, Ca).
- Ajustar todas las dosis en **insuficiencia renal** y en **oliguria**: riesgo de acumulación.
- Vía, concentración y velocidad de electrolitos IV según preparado y política local; vigilar extravasación. No trasladar límites de una formulación/centro a otro.
- **Vigilar el punto de infusión**: el cloruro cálcico y el fosfato son irritantes y pueden causar extravasación grave.
- Repetir analítica según gravedad, cinética, tratamiento y protocolo; no usar intervalos fijos para todas las situaciones.
- **Corregir el magnesio siempre** que haya hipoK o hipoCa refractarias.
- Registrar **síntomas y hallazgos ECG** (Chvostek, Trousseau, QT largo, ondas U, T picudas) antes y después de la reposición.
- Ante **valores críticos**, avisar al médico de forma inmediata.
- Las cifras y pautas son **orientativas**: mandan la prescripción y el protocolo del centro.

---

## 9. Ejemplos numéricos resueltos (3)

**Ejemplo A — déficit de potasio**

```
K = 2,8 mEq/L, 70 kg
Clasificación: < 3,0 → HIPOPOTASEMIA MODERADA
Estimación de la app = (4,0 − 2,8) × 100 = 120 mEq
No convertir esta cifra en dosis. Confirmar causa, ECG, función renal y pérdidas; prescribir reposición/controles conforme al protocolo.
```

**Ejemplo B — reposición de magnesio**

```
Mg = 1,2 mg/dL (sin síntomas), 60 kg
Clasificación: < 1,4 → HIPOMAGNESEMIA GRAVE
Estimación de la app = (2,0 − 1,2) × 1,5 = 1,2 g (no es una pauta validada)
La decisión de tratar, formulación, dosis y monitorización dependen de síntomas, función renal y protocolo.
```

**Ejemplo C — osmolaridad y anión gap**

```
Na 138 mEq/L, glucosa 180 mg/dL, BUN 28 mg/dL, Cl 100, HCO₃ 18, osmolaridad medida 300
Osm calculada = 2×138 + 180/18 + 28/2,8 = 276 + 10 + 10 = 296 mOsm/kg
Osm efectiva  = 276 + 10 = 286 mOsm/kg
Gap osmolar   = 300 − 296 = 4  → normal (≤ 10)
AG = 138 − (100 + 18) = 20 mEq/L → ELEVADO (> 12)
```

---

## 10. Limitaciones y errores frecuentes

| Limitación / error | Comentario |
|---|---|
| **Reponer el déficit total de golpe** | Riesgo de arritmias y sobrecarga |
| **Usar velocidades genéricas sin comprobar preparado/protocolo** | Riesgo de daño tisular, arritmia, sobredosificación o infratratamiento |
| **No corregir el magnesio** | HipoK e hipoCa refractarias |
| **No ajustar en insuficiencia renal/oliguria** | Acumulación de iones |
| **Ignorar el ECG** | Cambios graves no detectados |
| **Usar el Ca total sin corregir por albúmina** | Sobrestima el Ca real en hipoalbuminemia |
| **No convertir unidades** (mmol/L vs mg/dL) | Mg 2,43 · P 3,10 · Ca 4,008 |
| **No declarar los síntomas** (Mg, Ca) | Se pierde la clasificación de gravedad |
| **No repetir analítica** | Corrección incompleta o excesiva |
| **Olvidar el síndrome de realimentación** | Ver [realimentación](../protocolos/realimentacion.html) |

---

## 11. Cuándo NO usarla

- **Como sustituto del protocolo de reposición** del centro.
- **Sin analítica fiable** o con muestra hemolizada (falsa hiperpotasemia).
- **En AKI/IRC avanzada** sin ajuste nefrológico.
- **En la hiperpotasemia con cambios ECG**: primero estabilizar la membrana, no solo «bajar el número» (ver [RCP y soporte vital](../protocolos/rcp-sva.html)).
- **En hipofosfatemia con producto Ca × P elevado** sin control del calcio.
- **En el paciente en TRRC** sin considerar la eliminación extracorpórea.
- **Para pautar la reposición sin reevaluar** tras cada dosis.

---

## 12. Relación con otras escalas y parámetros

- **[Gasometría](gasometria.html)**: anión gap, delta-delta y osmolaridad.
- **[Gasto urinario](gasto-urinario.html)** y **[balance hídrico](balance-hidrico.html)**: oliguria y sobrecarga condicionan la reposición.
- **[Cockcroft-Gault y CKD-EPI](cockcroft-ckd-epi.html)**: ajuste renal.
- **[SOFA](../escalas/sofa.html)**: creatinina, plaquetas y disfunción orgánica.
- **[Síndrome de realimentación](../protocolos/realimentacion.html)**: reposición conjunta de P, K y Mg.
- **[TRRC](../protocolos/trrc.html)**: eliminación de iones y control del calcio con citrato.
- **[RCP y soporte vital](../protocolos/rcp-sva.html)**: corrección en la parada cardiaca.

---

## 13. Puntos clave

- **K:** la cifra de déficit es una estimación no prescriptiva; vía/velocidad/monitorización según situación y protocolo.
- **Mg:** 1 mmol/L = 2,43 mg/dL; la ecuación de la app no es una dosis validada.
- **P:** 1 mmol/L = 3,10 mg/dL; la estimación no sustituye una pauta; el producto Ca × P no es un objetivo aislado.
- **Ca:** corregido = Ca + 0,8 × (4,0 − albúmina); gluconato 10 % 1 g = **90 mg** (2,25 mmol); cloruro 10 % 1 g = **273 mg** (6,8 mmol).
- **Osm = 2×Na + glucosa/18 + BUN/2,8**; **AG = Na − (Cl + HCO₃)**, normal 8-12.
- Individualizar tratamiento, monitorización y controles; ajustar a función renal y protocolo vigente. Estas pantallas son de apoyo, no prescriben dosis.

---

## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **Corrección de iones** | Sodio, potasio, calcio, magnesio y fósforo |
| **Gasometría** | Ácido-base y electrolitos |
| **Sodio y agua libre** | Hiponatremia e hipernatremia |
| **Valores de referencia** | Rangos analíticos |
