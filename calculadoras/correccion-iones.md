# Corrección de iones y metabolismo

> 📖 **Fuentes:** KDIGO. Clinical Practice Guideline for Acute Kidney Injury. Kidney Int Suppl 2012;2:1-138. · Berend K, et al. Physiological approach to assessment of acid-base disturbances. N Engl J Med 2014;371:1434-1445. · MSD Manual Professional: https://www.msdmanuals.com/professional

El módulo **Iones y Metabólico** (`feature_iones`) agrupa cinco pantallas, más la pantalla F1 de corrección:

| Pantalla | Clase | Contenido |
|---|---|---|
| **Potasio** | `PotasioActivity` | Hipo/hiperpotasemia, riesgo ECG, déficit estimado y corrección |
| **Magnesio y Fósforo** | `MagnesioFosforoActivity` | Hipo/hipermagnesemia e hipo/hiperfosfatemia, reposición y producto Ca × P |
| **Calcio** | `CalcioActivity` | Ca total/corregido/iónico, clasificación y calculadora de ampollas |
| **Sodio** | `SodioActivity` | Hipo/hipernatremia, Na corregido, agua libre (ver [sodio y agua libre](sodio-agua-libre.md)) |
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

> *«Aproximación (1 mEq/L bajo ≈ 100 mEq totales). NUNCA reponer el total de golpe: repartir en 24-48 h.»*

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

### Reposición: velocidades máximas (reales de la app)

| Vía | Velocidad máxima |
|---|---|
| **Periférica** | **≤ 10 mEq/h** y **máx 40 mEq/L** de suero |
| **Central** | **≤ 20 mEq/h** |
| **Arritmia grave / parada** | **20 mEq en 20 min por vía central** |

- **Hipopotasemia leve:** vía **oral** preferente (cloruro potásico 40-60 mEq/día repartidos con comidas); revisar causa (diuréticos, vómitos, diarrea, alcalosis, hiperaldosteronismo).
- **Moderada:** oral si tolera (60-80 mEq/día); si no tolera → IV **con monitorización ECG continua**.
- **En cada 1 mEq que se sube:** controlar K cada **2-4 h**.
- **⚠ Corregir magnesio siempre:** la hipomagnesemia perpetúa la hipopotasemia refractaria.
- **Digoxina:** extremar precaución con la reposición rápida.

**Hiperpotasemia (medidas de la app):**

1. **Primero descartar pseudo-hiperK** (hemólisis de muestra, torniquete prolongado, puño cerrado).
2. Retirar fármacos que suben K (IECA, ARA2, espironolactona, AINE, trimetoprim, heparina).
3. Dieta baja en potasio + **resinas** (Kayexalate 15-30 g oral o enema); furosemida si sobrecarga o función renal conservada.
4. Moderada: lo anterior + **insulina rápida 10 UI IV + 25 g glucosa**; considerar **salbutamol nebulizado 10-20 mg**; **bicarbonato 1 M 50 mEq** si acidosis metabólica.
5. Grave / con cambios ECG: 🚨 **estabilizar membrana con gluconato cálcico 10 % 10 mL IV en 5-10 min** (no baja el K, protege el corazón; repetible si el ECG no mejora) + **shift** con insulina-glucosa + **eliminación** (furosemida/resinas/**diálisis** si refractaria o IRA/IRC).
6. **Monitor ECG continuo** y glucemia cada 30 min tras la insulina.

### Ejemplo

K **2,8 mEq/L**, 70 kg:

```
Déficit ≈ (4,0 − 2,8) × 100 = 120 mEq
```

Repartir en 24-48 h, nunca de golpe; con vía periférica ≤ 10 mEq/h → mínimo ~12 h solo para la reposición IV.

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
    si Mg < 2,0 mg/dL:  g = (2,0 − Mg) × 1,5      [acotado entre 1,0 y 12,0 g]
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
| **Leve** | **Vía oral**: óxido de magnesio 400-800 mg/día o magnesio quelado. Buscar causa (diuréticos, IBP, alcohol, diarrea, hipoparatiroidismo). |
| **Moderada** | **Sulfato de magnesio 2 g IV en 1 h** (o 1-2 g IM). Controlar Mg, K y Ca a las 4-6 h. ECG basal previo. |
| **Grave** | 🚨 **Sulfato de magnesio 2 g IV en 5-15 min**; mantenimiento 0,5-1 g/h según Mg. **Monitorizar ECG continuo y reflejos rotulianos cada 15 min.** En IRC, reducir dosis. **Antídoto:** gluconato cálcico 1 g IV. |

> **Corregir siempre** la hipoK y la hipoCa asociadas (son refractarias hasta normalizar el Mg).
> En **torsades:** bolo inicial de **2 g en 5-15 min**.

**Hipermagnesemia:** leve → retirar aportes exógenos y vigilar función renal (causa principal: IRC). Moderada → suero salino 0,9 % + furosemida (si función renal conservada) y monitorización ECG (riesgo de bradicardia y bloqueos). Grave → 🚨 **gluconato cálcico 1 g IV** (antagonista directo) + suero salino/furosemida; **hemodiálisis** si IRC grave; vigilar reflejos osteotendinosos, FR y conciencia.

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
    riesgo de calcificación si > 55
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

> *«Estimación orientativa. Vía oral preferente si tolera (0,32 mmol/kg/día). IV solo si grave o no tolera (0,16-0,32 mmol/kg/día).»*
> En **IRC**, objetivo 2,5-4,5 mg/dL y **producto Ca × P < 55**.

### Reposición y cuidados

- **Leve:** vía **oral** (fosfato monobásico sódico/potásico 1-2 g/día repartidos) + aumento dietético.
- **Moderada:** oral preferente **0,32 mmol/kg/día** repartidos; si no tolera o se requiere rápido → IV **0,16-0,32 mmol/kg en 6-12 h**.
- **Grave:** 🚨 fósforo IV **0,32 mmol/kg en 4-6 h** (fosfato potásico o sódico según el K); monitorizar Ca, K, Mg y función renal cada 6 h; **vía central preferente** por osmolaridad alta; riesgo de **hipocalcemia por precipitación**.
- **⚠ Síndrome de realimentación:** si ayuno prolongado, bajo peso o alcoholismo → reponer **P + K + Mg + tiamina**; en alcoholismo, **tiamina 200-300 mg IV** antes de iniciar el aporte.
- **Hiperfosfatemia:** restricción dietética de fósforo; **quelantes** (sevelámero, carbonato cálcico con las comidas) si IRC; grave → riesgo de calcificación y arritmias, **hemodiálisis** si IRC grave o refractaria; revisar aportes IV de fosfato en nutrición parenteral.

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

- **Hipocalcemia leve:** calcio oral (carbonato cálcico 500-1000 mg/8 h) + calcitriol 0,25-0,5 µg/día; tratar causa (hipoparatiroidismo, déficit de vitamina D, hipomagnesemia, pancreatitis); controlar Mg y albúmina.
- **Hipocalcemia moderada/grave:** 🚨 **gluconato cálcico 10 % 10-20 mL IV en 10 min** (preferible al cloruro por vía periférica); después infusión continua **0,5-1,5 mg/kg/h de Ca elemental**; monitorizar ECG continuo y Ca iónico cada 4-6 h; **corregir el magnesio siempre**; evitar el cloruro cálcico periférico (irritante, extravasación grave).
- **Hipercalcemia:** retirar causas (tiazidas, litio, vitamina D, calcio oral, IECA); buscar causa (hiperparatiroidismo primario, neoplasia, sarcoidosis); hidratación oral 2-3 L/día si tolera y **suero salino 0,9 % IV 2-4 L/24 h** (cuidado en cardiópatas/IRC); calcitonina 4 UI/kg SC/IM cada 12 h; **ácido zoledrónico 4 mg IV en 15 min** (o pamidronato 60-90 mg); glucocorticoides si causa granulomatosa/linfoma; **hemodiálisis** con bajo Ca en el baño si IRC o refractaria; **NO usar furosemida** salvo sobrecarga.

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

> ℹ️ La pantalla de **Gasometría** usa unos rótulos ligeramente distintos para el delta-delta (mismos cortes numéricos): *< 0,4* hiperclorémica añadida · *0,4-1,0* acidosis metabólica pura (AG elevado) · *1,0-2,0* acidosis metabólica + alcalosis metabólica · *> 2* alcalosis metabólica predominante. Ver [gasometría](gasometria.md).

**Lactato:**

| Valor | Lectura |
|---|---|
| **< 2,0 mmol/L** | Normal |
| **2,0-3,9** | Elevado: buscar hipoperfusión, sepsis, hipoxia, convulsiones; vigilar tendencia |
| **4,0-9,9** | Hipoperfusión grave: reanimación hemodinámica agresiva |
| **≥ 10** | Shock grave: mortalidad elevada, reanimación inmediata y valorar UCI |

**Glucemia:**

| Valor | Lectura |
|---|---|
| **< 54 mg/dL** | Hipoglucemia GRAVE: glucosa IV inmediata; en consciente, 15-20 g de HC oral; reevaluar a los 15 min |
| **54-69** | Hipoglucemia: regla **15/15** (15 g HC, medir a los 15 min) |
| **70-100** | Normal en ayunas |
| **101-125** | Alterada en ayunas (prediabetes) |
| **126-250** | Hiperglucemia: confirmar con HbA1c; pauta correctora del centro |
| **251-400** | Hiperglucemia marcada: descartar CAD/EHH |
| **> 400** | Hiperglucemia GRAVE: 🚨 riesgo de CAD/EHH, hidratación agresiva, insulina IV, control de K y osmolaridad |

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
| **Producto Ca × P** | < 55 mg²/dL² (en IRC) | — |

### Metabólico

| Parámetro | Rango normal | Notas |
|---|---|---|
| **Glucosa en ayunas** | 70-100 mg/dL | Prediabetes 100-125 · DM ≥ 126 · crítico < 40 o > 400 |
| **Lactato** | < 2,0 mmol/L | > 4 hipoperfusión · > 10 shock · crítico ≥ 4,0 |
| **Osmolaridad** | 275-295 mOsm/kg | — |
| **Anión gap** | 8-12 mEq/L | AG corregido por albúmina disponible |
| **Delta-delta** | 1,0-2,0 | — |
| **Brecha urinaria** | −10 a +10 mEq/L | Negativa: pérdidas GI · Positiva: ATR |
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
| **Potasio (K)** | Reposición por vía **central: máximo 20 mEq/h**; por vía **periférica: máximo 10 mEq/h**. Monitorizar ECG y niveles de potasio. |
| **Magnesio (Mg)** | **2 g en 2 horas** (o según protocolo), vigilando **reflejos osteotendinosos y tensión arterial**. |
| **Fosfato (PO₄)** | Administración **preferentemente por vía central**, según protocolo de reposición del centro. |
| **Contraindicaciones y precauciones** | Separar siempre el resultado analítico del protocolo de reposición y de las contraindicaciones (**oliguria, insuficiencia renal, hiperpotasemia…**). **Revaluar antes de repetir dosis.** |

---

## 8. Cuidados de enfermería y reglas de seguridad

- **Corregir despacio** y con **monitorización ECG** en las alteraciones graves (K, Mg, Ca).
- Ajustar todas las dosis en **insuficiencia renal** y en **oliguria**: riesgo de acumulación.
- **Vía periférica:** K ≤ 10 mEq/h y ≤ 40 mEq/L; fosfato y calcio preferentemente por vía central (el gluconato cálcico es la excepción tolerada por periferia).
- **Vigilar el punto de infusión**: el cloruro cálcico y el fosfato son irritantes y pueden causar extravasación grave.
- **Repetir la analítica** tras cada corrección (K cada 2-4 h al subir 1 mEq/h; Mg, K y Ca a las 4-6 h; Ca iónico cada 4-6 h en la hipocalcemia grave).
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
Déficit estimado = (4,0 − 2,8) × 100 = 120 mEq
Plan: repartir en 24-48 h; con vía periférica ≤ 10 mEq/h → > 12 h si es solo IV;
      corregir magnesio y monitorizar ECG y K cada 2-4 h
```

**Ejemplo B — reposición de magnesio**

```
Mg = 1,2 mg/dL (sin síntomas), 60 kg
Clasificación: < 1,4 → HIPOMAGNESEMIA GRAVE
Dosis de sulfato = (2,0 − 1,2) × 1,5 = 1,2 g  (acotada 1,0-12,0 g)
Plan: 2 g IV en 5-15 min si es grave/sintomática; si no, 2 g IV en 1 h;
      monitorizar reflejos rotulianos y ECG; antídoto: gluconato cálcico 1 g
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
| **Superar las velocidades máximas** (K periférico 10 mEq/h, central 20 mEq/h) | Riesgo de flebitis y arritmias |
| **No corregir el magnesio** | HipoK e hipoCa refractarias |
| **No ajustar en insuficiencia renal/oliguria** | Acumulación de iones |
| **Ignorar el ECG** | Cambios graves no detectados |
| **Usar el Ca total sin corregir por albúmina** | Sobrestima el Ca real en hipoalbuminemia |
| **No convertir unidades** (mmol/L vs mg/dL) | Mg 2,43 · P 3,10 · Ca 4,008 |
| **No declarar los síntomas** (Mg, Ca) | Se pierde la clasificación de gravedad |
| **No repetir analítica** | Corrección incompleta o excesiva |
| **Olvidar el síndrome de realimentación** | Ver [realimentación](../protocolos/realimentacion.md) |

---

## 11. Cuándo NO usarla

- **Como sustituto del protocolo de reposición** del centro.
- **Sin analítica fiable** o con muestra hemolizada (falsa hiperpotasemia).
- **En AKI/IRC avanzada** sin ajuste nefrológico.
- **En la hiperpotasemia con cambios ECG**: primero estabilizar la membrana, no solo «bajar el número» (ver [RCP y soporte vital](../protocolos/rcp-sva.md)).
- **En hipofosfatemia con producto Ca × P elevado** sin control del calcio.
- **En el paciente en TRRC** sin considerar la eliminación extracorpórea.
- **Para pautar la reposición sin reevaluar** tras cada dosis.

---

## 12. Relación con otras escalas y parámetros

- **[Gasometría](gasometria.md)**: anión gap, delta-delta y osmolaridad.
- **[Gasto urinario](gasto-urinario.md)** y **[balance hídrico](balance-hidrico.md)**: oliguria y sobrecarga condicionan la reposición.
- **[Cockcroft-Gault y CKD-EPI](cockcroft-ckd-epi.md)**: ajuste renal.
- **[SOFA](../escalas/sofa.md)**: creatinina, plaquetas y disfunción orgánica.
- **[Síndrome de realimentación](../protocolos/realimentacion.md)**: reposición conjunta de P, K y Mg.
- **[TRRC](../protocolos/trrc.md)**: eliminación de iones y control del calcio con citrato.
- **[RCP y soporte vital](../protocolos/rcp-sva.md)**: corrección en la parada cardiaca.

---

## 13. Puntos clave

- **K:** déficit ≈ (4,0 − K) × 100 mEq; máximo **10 mEq/h periférico** y **20 mEq/h central**; corregir siempre el **Mg**.
- **Mg:** 1 mmol/L = 2,43 mg/dL; reposición = (2,0 − Mg) × 1,5 g (acotada 1-12 g); grave → 2 g IV en 5-15 min.
- **P:** 1 mmol/L = 3,10 mg/dL; reposición = peso × 0,16 × ((2,5 − P)/2,5) mmol; **producto Ca × P < 55**.
- **Ca:** corregido = Ca + 0,8 × (4,0 − albúmina); gluconato 10 % 1 g = **90 mg** (2,25 mmol); cloruro 10 % 1 g = **273 mg** (6,8 mmol).
- **Osm = 2×Na + glucosa/18 + BUN/2,8**; **AG = Na − (Cl + HCO₃)**, normal 8-12.
- Corregir **despacio**, con **monitorización ECG** y **analítica de control**; ajustar en insuficiencia renal.

---

## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **Corrección de iones** | Sodio, potasio, calcio, magnesio y fósforo |
| **Gasometría** | Ácido-base y electrolitos |
| **Sodio y agua libre** | Hiponatremia e hipernatremia |
| **Valores de referencia** | Rangos analíticos |
