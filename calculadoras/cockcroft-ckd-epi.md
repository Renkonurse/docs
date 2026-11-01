---
layout: default
title: "Función renal estimada: Cockcroft-Gault y CKD-EPI 2021"
---
# Función renal estimada: Cockcroft-Gault y CKD-EPI 2021

> 📖 **Fuentes:** Cockcroft DW, Gault MH. Prediction of creatinine clearance from serum creatinine. Nephron 1976;16:31-41. · Levey AS, et al. CKD-EPI equation. Ann Intern Med 2009;150:604-612. · KDIGO. Clinical Practice Guideline for Acute Kidney Injury. Kidney Int Suppl 2012;2:1-138.

## 1. Qué calcula y para qué sirve clínicamente

La pantalla `CockcroftCkdEpiActivity` (`feature_utilidades`) estima la función renal con **dos ecuaciones** y avisa de que **no son intercambiables**:

- **Cockcroft-Gault (1976)**: aclaramiento de creatinina estimado (mL/min). Es la ecuación que figura en la mayoría de **fichas técnicas para el ajuste de dosis** de fármacos.
- **CKD-EPI 2021 (sin raza)**: filtrado glomerular estimado (mL/min/1,73 m²). Es la recomendada para **estadificar la enfermedad renal crónica** y para la detección/monitorización.

La lógica pura está en `LogicaRenal.kt`.

---

## 2. Fundamento y fórmulas (con unidades)

La creatinina sérica es un marcador de filtración glomerular. Como depende de la **masa muscular**, edad y sexo, las ecuaciones la corrigen con esos factores y (en Cockcroft) con el peso.

### Cockcroft-Gault (mL/min)

```
base = ((140 − edad) × peso (kg)) / (72 × creatinina (mg/dL))
CrCl = base × 0,85            si es mujer
CrCl = base                   si es hombre
```

### CKD-EPI 2021 (mL/min/1,73 m²), sin coeficiente racial

```
κ (kappa) = 0,7  (mujer)   ·   0,9  (hombre)
α (alfa)  = −0,241 (mujer) ·   −0,302 (hombre)

ratio    = creatinina (mg/dL) / κ
minRatio = min(ratio, 1)      maxRatio = max(ratio, 1)

FG = 142 × minRatio^α × maxRatio^(−1,200) × 0,9938^edad

FG = FG × 1,012               si es mujer
```

Constantes literales del código: **142**, **−1,200**, **0,9938** por año y factor mujer **1,012**.

| Variable | Unidad |
|---|---|
| Edad | años (entero) |
| Peso | kg (solo Cockcroft) |
| Creatinina | mg/dL |
| Resultado CG | mL/min |
| Resultado CKD-EPI | mL/min/1,73 m² |

---

## 3. Variables de entrada y valores normales

| Campo | Unidad | Validación real |
|---|---|---|
| Sexo | Hombre / Mujer | Botones (por defecto Hombre) |
| Edad | años | Entero > 0 |
| Peso | kg | > 0 (solo Cockcroft) |
| Creatinina | mg/dL | > 0 |

Si edad, peso o creatinina no son válidos → *«Introduce edad, peso y creatinina válidos»* y no se calcula ninguna de las dos.

**Valores de referencia de creatinina** (orientativos, según laboratorio):

| Población | Creatinina |
|---|---|
| Varón adulto | 0,7-1,2 mg/dL |
| Mujer adulta | 0,5-1,0 mg/dL |

---

## 4. Interpretación por rangos y actuación de enfermería

### Estadios de la enfermedad renal crónica (KDIGO) — se aplican al **FG estimado** (CKD-EPI)

| FG (mL/min/1,73 m²) | Estadio | Descripción | Actuación de enfermería |
|---|---|---|---|
| **≥ 90** | **G1** | Normal o alta | Sin disfunción por FG; vigilar si hay marcadores de daño renal |
| **60-89** | **G2** | Ligeramente disminuida | Seguimiento; ajustar fármacos según ficha |
| **45-59** | **G3a** | Ligera-moderadamente disminuida | Revisar dosis renales; vigilar creatinina y diuresis |
| **30-44** | **G3b** | Moderada-gravemente disminuida | Avisar; ajustar nefrotóxicos y contrastes |
| **15-29** | **G4** | Gravemente disminuida | Coordinar con nefrología; preparar TRRC si precisa |
| **< 15** | **G5** | Fallo renal | Valorar TRRC; extremar ajustes de fármacos |

La estadificación completa requiere además el **cociente albúmina/creatinina** (categorías A1-A3) y la causa.

### Actuación de enfermería general

- Registrar **peso, talla y edad** correctos y actualizados (son datos de la fórmula).
- Confirmar la **unidad de la creatinina** (mg/dL vs µmol/L): **1 mg/dL ≈ 88,4 µmol/L**.
- Comunicar un **descenso del FG** o creatinina en ascenso, junto a la diuresis y el balance.
- Al ajustar fármacos, usar **la misma ecuación que la ficha técnica**; no intercambiar resultados.
- Vigilar fármacos **nefrotóxicos** (aminoglucósidos, contraste, AINE, vancomicina) y ajustar.

---

## 5. Ejemplos numéricos resueltos (3)

**Ejemplo A — mujer de 68 años, 60 kg, creatinina 1,4 mg/dL**

```
Cockcroft-Gault:
  base = ((140 − 68) × 60) / (72 × 1,4) = 4320 / 100,8 = 42,9 mL/min
  CrCl = 42,9 × 0,85 = 36,4 → 36 mL/min

CKD-EPI 2021:
  κ = 0,7 ; α = −0,241 ; ratio = 1,4 / 0,7 = 2,0 → minRatio 1 ; maxRatio 2,0
  FG = 142 × 1^(−0,241) × 2^(−1,200) × 0,9938^68 ≈ 40,5
  FG = 40,5 × 1,012 ≈ 41,0 → 41 mL/min/1,73 m²
```

→ Discrepancia clínicamente relevante (36 vs 41): motivo del aviso de la app.

**Ejemplo B — varón de 45 años, 80 kg, creatinina 1,0 mg/dL**

```
CG:  base = ((140 − 45) × 80) / (72 × 1,0) = 7600 / 72 = 105,6 mL/min
CKD-EPI: κ = 0,9 ; ratio = 1,0/0,9 = 1,11 → minRatio 1 ; maxRatio 1,11
  FG = 142 × 1,11^(−1,200) × 0,9938^45 ≈ 142 × 0,882 × 0,757 ≈ 94,8 mL/min/1,73 m²
```

**Ejemplo C — mujer de 80 años, 50 kg, creatinina 2,0 mg/dL**

```
CG:  base = ((140 − 80) × 50) / (72 × 2,0) = 3000 / 144 = 20,8 mL/min
     CrCl = 20,8 × 0,85 = 17,7 → 18 mL/min (estadio G4 aproximado)
CKD-EPI: se calcula igualmente; puede diferir y debe interpretarse con el estadio KDIGO
```

---

## 6. Limitaciones y errores frecuentes

| Limitación / error | Comentario |
|---|---|
| **Confundir mL/min con mL/min/1,73 m²** | Cockcroft no está normalizado; CKD-EPI sí |
| **Usar el peso real siempre** en Cockcroft | En obesidad/edemas sobreestima el FG |
| **No corregir por superficie corporal** al comparar | Valores no equivalentes |
| Creatinina **normal con fallo renal** | Bajo músculo, dilución, falta de equilibrio |
| **No esperar el estado estacionario** | Tras cambios rápidos de función renal el valor no es fiable |
| Interferencias analíticas | Bilirrubina, hemólisis, fármacos |
| Poblaciones especiales | Amputados, sarcopenia, cirrosis, embarazo, trasplantados |
| **Unidad de creatinina** (mg/dL vs µmol/L) | Error de conversión |
| **Intercambiar** las dos ecuaciones al dosificar | Dosis errónea |

---

## 7. Cuándo NO usarla

- **AKI (lesión renal aguda)**: las ecuaciones de FG **no están validadas**; usar creatinina y diuresis (KDIGO).
- **Función renal inestable**: no hay estado estacionario; el valor no es interpretable.
- **Extremos de masa muscular** (sarcopenia grave, culturistas, amputaciones) sin criterio.
- **Embarazo**: usar ecuaciones específicas.
- **Como único criterio para TRRC o ingreso**: valorar clínica, iones, diuresis y balance.
- **Población pediátrica**: usar ecuaciones pediátricas (Schwartz).
- **Sin creatinina fiable** o con muestra hemolizada.

---

## 8. Relación con otras escalas y parámetros

- **[Gasto urinario](gasto-urinario.html)**: criterios KDIGO de AKI por diuresis.
- **[Balance hídrico](balance-hidrico.html)**: la diuresis y el balance completan la valoración renal.
- **[SOFA](../escalas/sofa.html)**: creatinina y diuresis puntúan el componente renal.
- **[Código Sepsis](../protocolos/codigo-sepsis.html)** y **[Shock](../protocolos/shock-critico.html)**: la perfusión renal y la AKI.
- **[TRRC](../protocolos/trrc.html)** y **[TRRC: cuidados](../guias-cuidados/trrc-cuidados.html)**: manejo de la disfunción renal grave.
- **[Peso ideal](peso-ideal.html)**: elección del peso en Cockcroft.

---

## 9. Puntos clave

- **Cockcroft-Gault** (mL/min): `((140 − edad) × peso) / (72 × creatinina)`, × 0,85 en mujer.
- **CKD-EPI 2021** (mL/min/1,73 m²): 142 × ratio^α × 1,200 × 0,9938^edad, × 1,012 en mujer.
- **No son intercambiables**: Cockcroft para ajuste de fármacos, CKD-EPI para estadificar.
- Estadios KDIGO G1-G5: ≥ 90 · 60-89 · 45-59 · 30-44 · 15-29 · < 15.
- En el **paciente crítico** la creatinina puede ser normal pese a fallo renal.
- Registrar edad, peso y creatinina correctos y **confirmar las unidades**.

---

## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **Función renal estimada** | Cockcroft-Gault y CKD-EPI |
| **Peso ideal** | Elección del peso |
| **Corrección de iones** | Ajuste de fármacos |
| **Fármacos de alto riesgo** | Dosis y monitorización |
