---
layout: default
title: "Gasto urinario (diuresis)"
---
# Gasto urinario (diuresis)

> 📖 **Fuentes:** KDIGO. Clinical Practice Guideline for Acute Kidney Injury. Kidney Int Suppl 2012;2:1-138. · Devine BJ. Gentamicin therapy. Drug Intell Clin Pharm 1974;8:650-655. · MSD Manual Professional: https://www.msdmanuals.com/professional

## 1. Qué calcula y para qué sirve clínicamente

La pantalla `GastoUrinarioActivity` (`feature_utilidades`) calcula la **diuresis en mL/kg/h** a partir del volumen, las horas y el peso, y la clasifica clínicamente. Sirve para:

- **Detectar precozmente la lesión renal aguda (AKI)**: la oliguria es criterio diagnóstico y un signo de alarma temprano.
- **Evaluar la respuesta a volumen** y la perfusión renal.
- **Monitorizar la evolución** del paciente crítico y la respuesta a diuréticos o a la TRRC.
- **Cuantificar la diuresis** para el balance hídrico y el registro por turnos.

Es una de las variables de monitorización más accesibles y con mayor valor pronóstico: la oliguria sostenida se asocia a peor evolución.

---

## 2. Fundamento y fórmula (con unidades)

El gasto urinario se **normaliza por peso y por tiempo** para poder comparar entre pacientes y periodos de distinta duración. El resultado expresa la **producción de orina por kilogramo y hora**.

**Fórmula exacta implementada** (`GastoUrinarioActivity.kt`):

```
Gasto urinario (mL/kg/h) = volumen del periodo (mL) / [ peso (kg) × horas del periodo (h) ]
```

| Variable | Unidad | Descripción |
|---|---|---|
| Volumen | mL | Orina recogida en el periodo |
| Peso | kg | Peso **real** o **ideal (Devine)** según el selector |
| Horas | h | Duración real del periodo |
| **Resultado** | **mL/kg/h** | Diuresis normalizada |

La app muestra la fórmula con los datos: `%1$s mL ÷ (%2$s kg × %3$s h)`.

**Peso ideal (Devine) cuando se selecciona «Peso ideal»** (`alturaIdealDevine`):

```
pulgadas = altura (cm) / 2,54
Peso ideal (kg) = base + 2,3 × (pulgadas − 60)
      base = 50,0 (Hombre) · 45,5 (Mujer)
```

---

## 3. Variables de entrada y valores normales

| Campo | Unidad | Notas |
|---|---|---|
| Volumen del periodo | mL | Obligatorio, > 0 |
| Horas del periodo | h | Obligatorio, > 0 |
| Tipo de peso | Peso real / Peso ideal | Selector |
| Peso (real) | kg | Precargado desde la Valoración Integral, editable |
| Altura | cm | Solo si se elige peso ideal |
| Sexo | Hombre / Mujer | Solo si se elige peso ideal |

**Validación real:** si volumen, horas o peso no son números > 0 → *«Rellena todos los campos con números válidos»*; si se elige peso ideal y la altura no es válida → error de altura.

**Valores de referencia:**

| Situación | Valor |
|---|---|
| Diuresis normal orientativa (adulto) | ≥ 0,5 mL/kg/h |
| Anuria clínica | < 100 mL/24 h |
| Criterio de oliguria KDIGO | < 0,5 mL/kg/h durante ≥ 6 h |

---

## 4. Interpretación por rangos y actuación de enfermería

`categoriaGu()` clasifica con estos cortes exactos:

| Categoría | Rango (mL/kg/h) | Color | Actuación de enfermería |
|---|---|---|---|
| **Anuria** | **< 0,1** | Rojo | Avisar al médico de inmediato; comprobar sonda/colector, valorar ecografía vesical y perfusión; revisar balance |
| **Oliguria marcada** | **0,1-0,3** | Rojo | Avisar; reevaluar volemia, PAM y fármacos nefrotóxicos; registrar tendencia horaria |
| **Oliguria** | **0,3-0,5** | Amarillo | Vigilar; correlacionar con balance y perfusión; intensificar controles |
| **Diuresis adecuada** | **0,5-1** | Verde | Mantener monitorización y registro por turnos |
| **Poliuria ligera** | **1-2** | Azul | Vigilar pérdidas y balance; revisar diuréticos y glucemia |
| **Poliuria marcada** | **> 2** | Amarillo | Vigilar deshidratación y electrolitos; revisar diuréticos, fase de recuperación de AKI, diabetes insípida |

Avisos reales de la app:

- Si la categoría es de oliguria/anuria: *«Diuresis baja (oliguria / anuria): valora la perfusión renal y el balance hídrico y avisa al médico según el protocolo de tu unidad.»*
- Siempre: *«Criterios orientativos (p. ej. RIFLE / KDIGO), no un dogma: no sustituyen al juicio clínico ni los protocolos de tu unidad.»*

---

## 5. Criterios KDIGO de AKI (marco de referencia)

**Por diuresis:**

| Estadio | Criterio de diuresis |
|---|---|
| **1** | < 0,5 mL/kg/h durante **6-12 h** |
| **2** | < 0,5 mL/kg/h durante **≥ 12 h** |
| **3** | < 0,3 mL/kg/h durante **≥ 24 h** **o** anuria ≥ 12 h |

**Por creatinina sérica** (complementario):

| Estadio | Criterio de creatinina |
|---|---|
| **1** | 1,5-1,9 × basal **o** aumento ≥ 0,3 mg/dL |
| **2** | 2,0-2,9 × basal |
| **3** | ≥ 3,0 × basal **o** ≥ 4,0 mg/dL **o** inicio de TRRC |

> El diagnóstico de AKI requiere cumplir **cualquiera** de los criterios (diuresis o creatinina). La diuresis permite detectar la AKI **antes** que la creatinina.

---

## 6. Ejemplos numéricos resueltos (3)

**Ejemplo A — oliguria**

```
Volumen 400 mL en 8 h, peso real 70 kg
GU = 400 / (70 × 8) = 400 / 560 = 0,71 mL/kg/h  → diuresis adecuada
```

**Ejemplo B — oliguria marcada**

```
Volumen 120 mL en 8 h, peso real 80 kg
GU = 120 / (80 × 8) = 120 / 640 = 0,19 mL/kg/h  → oliguria marcada (< 0,3)
```

**Ejemplo C — poliuria marcada**

```
Volumen 2 500 mL en 12 h, peso real 70 kg
GU = 2500 / (70 × 12) = 2500 / 840 = 2,98 mL/kg/h  → poliuria marcada (> 2)
```

**Ejemplo D — con peso ideal (Devine)**

```
Mujer, altura 160 cm → pulgadas = 63,0 → PI = 45,5 + 2,3 × 3,0 = 52,4 kg
Volumen 500 mL en 8 h
GU = 500 / (52,4 × 8) = 500 / 419,2 = 1,19 mL/kg/h  → poliuria ligera
```

---

## 7. Limitaciones y errores frecuentes

| Limitación / error | Comentario |
|---|---|
| **Medir mal el volumen** (estimar «a ojo») | Error acumulado en el balance |
| **Usar las horas del turno** en vez de las horas reales | GU falsamente alto o bajo |
| **Mezclar peso real e ideal** en el mismo seguimiento | Valores no comparables |
| **Sonda acodada, obstruida o con fugas** | Oliguria falsa |
| Pérdidas **no recogidas** (arrastre, incontinencia, diálisis) | Subestima la diuresis |
| **Diuresis de una sola medida** sin tendencia | Falsa alarma o detección tardía |
| Peso precargado **desactualizado** | GU erróneo |
| La diuresis **no equivale a función renal** | Puede ser normal en la AKI no oligúrica |
| Diuréticos recientes | Aumentan la diuresis sin mejorar la función renal |

---

## 8. Cuándo NO usarla

- **Sin recogida fiable de orina** (paciente sin sonda con incontinencia): el valor no es interpretable.
- **En diálisis** o con pérdidas por TRRC: la diuresis no refleja el balance real de fluidos.
- **Como único criterio de AKI**: en la AKI no oligúrica la diuresis es normal; usar también la creatinina.
- **Para decidir diuréticos de forma aislada**: valorar volemia, PAM, ecografía y balance.
- **Con pesos aberrantes** (edemas masivos, obesidad mórbida) sin criterio: elegir el peso según protocolo y mantenerlo.
- **En periodos muy cortos** (< 1-2 h): el valor es poco representativo.

---

## 9. Relación con otras escalas y parámetros

- **[Balance hídrico](balance-hidrico.html)**: la diuresis es la principal salida del balance.
- **[Pérdidas insensibles](perdidas-insensibles.html)**: se suman a las salidas no medidas.
- **[Cockcroft-Gault y CKD-EPI](cockcroft-ckd-epi.html)**: complementan la valoración renal (filtrado).
- **[KDIGO / criterios de AKI]** (este documento): estadificación.
- **[SOFA](../escalas/sofa.html)**: la creatinina y la diuresis (< 500 mL/día) puntúan en el componente renal.
- **[Código Sepsis](../protocolos/codigo-sepsis.html)** y **[Shock](../protocolos/shock-critico.html)**: la oliguria es un marcador de hipoperfusión.
- **[TRRC](../protocolos/trrc.html)** y **[TRRC: cuidados](../guias-cuidados/trrc-cuidados.html)**: manejo cuando la AKI requiere depuración extracorpórea.
- **[Peso ideal](peso-ideal.html)**: elección del peso.

---

## 10. Puntos clave

- `GU = volumen / (peso × horas)`, en **mL/kg/h**.
- **< 0,5 mL/kg/h** es oliguria y criterio KDIGO si persiste ≥ 6 h.
- Anuria < 0,1; oliguria marcada 0,1-0,3; oliguria 0,3-0,5; adecuada 0,5-1; poliuria ligera 1-2; poliuria marcada > 2.
- Medir el volumen real y las **horas reales**; registrar por turnos y valorar la **tendencia**.
- Comprobar siempre que la sonda y el colector funcionan antes de atribuir la oliguria al paciente.
- La diuresis orienta, pero se interpreta junto al **balance**, la **PAM**, el **lactato** y la **creatinina**.

---

## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **Gasto urinario** | Diuresis horaria |
| **Balance hídrico** | Ingresos y pérdidas |
| **Shock crítico** | Perfusión renal |
| **Función renal** | Creatinina y filtrado |
