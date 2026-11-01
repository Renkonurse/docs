---
layout: default
title: "Pérdidas insensibles"
---
# Pérdidas insensibles

> 📖 **Fuentes:** KDIGO. Clinical Practice Guideline for Acute Kidney Injury. Kidney Int Suppl 2012;2:1-138. · Marino PL. The ICU Book. 4th ed. Wolters Kluwer. · SEEIUC: https://www.seeiuc.org

## 1. Qué calcula y para qué sirve clínicamente

La pantalla `MainActivity` (`feature_perdidasinsensibles`) calcula las **pérdidas insensibles (P.I.)** del periodo, el **agua endógena** y el **balance neto** que hay que incorporar al balance hídrico.

Sirve para:

- **Estimar las pérdidas de agua no medibles** (evaporación cutánea y respiratoria).
- **Ajustar el balance hídrico** cuando no se puede medir todo lo que pierde el paciente.
- **Anticipar necesidades de fluidos** en pacientes con fiebre, taquipnea, ventilación mecánica o sudoración.
- **Evitar errores de balance** que llevarían a sobrecarga o depleción.

---

## 2. Fundamento y fórmulas (con unidades)

Las pérdidas insensibles son pérdidas de agua **no medibles** que no se registran como diuresis, heces o drenajes: **sudoración, respiración y evaporación**. La estimación se basa en el **peso**, el **estado respiratorio**, la **fiebre** y la **diaforesis**; el organismo además produce **agua endógena** por el metabolismo.

**Fórmulas exactas implementadas** (`calcularPerdidas()` en `MainActivity.kt`):

```
Basal (mL)         = factor del estado respiratorio (mL/kg/h) × peso (kg) × horas
Fiebre (mL)        = 0,1 × peso (kg) × grados extra × horas de fiebre      [solo si fiebre activa]
Sudor (mL)         = tasa de diaforesis (mL/h) × horas
Total P.I. (mL)    = basal + fiebre + sudor
Agua endógena (mL) = 12,5 × horas          (300 mL / 24 h)
Balance neto (mL)  = total P.I. − agua endógena
```

| Variable | Unidad |
|---|---|
| Peso | kg |
| Horas | h |
| Grados extra | °C (por encima de 37,5 °C) |
| Tasa de diaforesis | mL/h |
| Resultados | mL (enteros) |

- Los resultados se **redondean a enteros (mL)**.
- Si hay fiebre activa pero **grados extra = 0 o horas de fiebre = 0**: *«Sin grados extra o sin horas de fiebre no hay pérdida por fiebre: solo se suman el basal y el sudor.»*

---

## 3. Variables de entrada y valores normales (factores y tasas)

**Factores basales según estado respiratorio** (tabla real de la app):

| Estado | Factor |
|---|---|
| **Respiración espontánea** | **0,5 mL/kg/h** |
| **VM sin humidificación** | **1 mL/kg/h** |
| **VM con humidificación** | **0,25 mL/kg/h** |

**Tasa de diaforesis:**

| Grado | Tasa |
|---|---|
| **Ninguna** | 0 mL/h |
| **Leve** | 10 mL/h |
| **Moderada** | 20 mL/h |
| **Severa** | 40 mL/h |

**Fiebre:** **0,1 mL/kg/h por grado extra** (por encima de **37,5 °C**).

**Agua endógena:** **12,5 mL/h** (300 mL/24 h).

**Valores por defecto de la pantalla:** peso 70 kg (o el de la Valoración Integral), horas 24, grados extra 1,0, horas de fiebre 0.

---

## 4. Interpretación del resultado y actuación de enfermería

- **Total P.I.** = pérdidas insensibles del periodo (basal + fiebre + sudor). La app **envía a Monitorización el TOTAL de P.I.** (campo `perdidas_ins` del Balance), **no el neto**.
- **Agua endógena** = agua producida por el metabolismo; se contabiliza como **ingreso**.
- **Neto = total P.I. − agua endógena**:
  - **Neto negativo** → añadir a **Egresos** (pérdidas netas de agua).
  - **Neto positivo** → añadir a **Ingresos** (el agua endógena supera las pérdidas insensibles).

| Situación | Actuación de enfermería |
|---|---|
| **Paciente afebril, espontáneo** | Registrar basal; vigilar patrón respiratorio y temperatura |
| **Fiebre** | Medir temperatura real y anotar las horas de fiebre; aumentar la vigilancia de fluidos |
| **Sudoración moderada/severa** | Cambiar ropa de cama, valorar aportes, registrar el grado |
| **VM sin humidificación** | Máximas pérdidas (1 mL/kg/h): extremar la vigilancia del balance |
| **Quemados / taquipnea marcada** | Las pérdidas reales suelen superar la estimación: avisar y ajustar con el equipo |

> *«Estimación orientativa de apoyo: no sustituye al juicio clínico ni a los protocolos del centro.»*

---

## 5. Ejemplos numéricos resueltos (3)

**Ejemplo A — VM sin humidificación, 24 h, 70 kg, sin fiebre ni sudor**

```
Basal         = 1,0 × 70 × 24 = 1680 mL
Fiebre        = 0
Sudor         = 0
Total P.I.    = 1680 mL
Agua endógena = 12,5 × 24 = 300 mL
Neto          = 1680 − 300 = 1380 mL   → añadir a Egresos
```

**Ejemplo B — espontáneo, 12 h, 80 kg, fiebre (2 °C extra, 6 h), diaforesis moderada**

```
Basal         = 0,5 × 80 × 12 = 480 mL
Fiebre        = 0,1 × 80 × 2 × 6 = 96 mL
Sudor         = 20 × 12 = 240 mL
Total P.I.    = 480 + 96 + 240 = 816 mL
Agua endógena = 12,5 × 12 = 150 mL
Neto          = 816 − 150 = 666 mL     → añadir a Egresos
```

**Ejemplo C — VM con humidificación, 24 h, 60 kg, diaforesis leve**

```
Basal         = 0,25 × 60 × 24 = 360 mL
Fiebre        = 0
Sudor         = 10 × 24 = 240 mL
Total P.I.    = 600 mL
Agua endógena = 12,5 × 24 = 300 mL
Neto          = 600 − 300 = 300 mL     → añadir a Egresos
```

---

## 6. Limitaciones y errores frecuentes

| Limitación / error | Comentario |
|---|---|
| **Estimación orientativa** | En el paciente crítico la pérdida real puede diferir |
| **Ajustar mal el estado respiratorio** | 0,25 ↔ 1 mL/kg/h (hasta 4 veces): es el factor que más cambia el resultado |
| **Olvidar el agua endógena** | Se sobreestiman las pérdidas netas |
| **No registrar temperatura y horas de fiebre** | Pérdida por fiebre mal calculada |
| **Confundir total y neto** | A Monitorización va el **total**, no el neto |
| **Quemados, taquipnea, hipertermia prolongada** | La estimación queda corta |
| **No incluir el neto en el balance** | Balance hídrico incompleto |
| Peso **desactualizado** | Cálculo proporcionalmente erróneo |
| Periodos de tiempo mal definidos | Resultado no comparable |

---

## 7. Cuándo NO usarla

- **Como medida exacta**: es una estimación; no sustituye a la medición de pérdidas cuantificables.
- **En quemados extensos** sin protocolo específico: las pérdidas son muy superiores a la fórmula.
- **En pacientes con drenajes, ostomías o fístulas de alto débito**: medir esas pérdidas aparte.
- **En diálisis/TRRC**: el balance de la máquina manda para la eliminación de volumen.
- **Sin peso fiable**: el cálculo es proporcional al peso.
- **Como único criterio de reposición de fluidos**: integrar con constantes, diuresis y balance.

---

## 8. Relación con otras escalas y parámetros

- **[Balance hídrico](balance-hidrico.html)**: las P.I. netas se suman a las salidas.
- **[Gasto urinario](gasto-urinario.html)**: principal salida medible, complementaria a las P.I.
- **[Termorregulación](../protocolos/termorregulacion.html)**: manejo de la fiebre y la hipertermia.
- **[Shock: tipos y manejo](../protocolos/shock-critico.html)**: contexto de la reanimación con fluidos.
- **[Código Sepsis](../protocolos/codigo-sepsis.html)**: la fiebre y las pérdidas en la sepsis.
- **[Peso ideal](peso-ideal.html)**: elección del peso.

---

## 9. Puntos clave

- **Basal = factor × peso × horas**; factores **0,5 / 1 / 0,25 mL/kg/h** según espontánea / VM sin / VM con humidificación.
- **Fiebre = 0,1 × peso × grados extra × horas** (grados por encima de 37,5 °C).
- **Sudor = 0 / 10 / 20 / 40 mL/h** según diaforesis ninguna/leve/moderada/severa.
- **Agua endógena = 12,5 × horas** (300 mL/24 h).
- **Total P.I. = basal + fiebre + sudor**; **neto = total − agua endógena**.
- A Monitorización se envía el **total**, no el neto. Registrar temperatura, sudoración y estado respiratorio en cada turno.

---

## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **Pérdidas insensibles** | Estimación |
| **Balance hídrico** | Balance total |
| **Termorregulación** | Fiebre y pérdidas |
| **Quemados** | Reposición y monitorización |
