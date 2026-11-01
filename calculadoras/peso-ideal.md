---
layout: default
title: "Peso ideal, peso ajustado y porcentaje peso real/ideal"
---
# Peso ideal, peso ajustado y porcentaje peso real/ideal

> 📖 **Fuentes:** Devine BJ. Gentamicin therapy. Drug Intell Clin Pharm 1974;8:650-655. · ARDSNet. Ventilation with lower tidal volumes. N Engl J Med 2000;342:1301-1308. · Marino PL. The ICU Book. 4th ed. Wolters Kluwer.

## 1. Qué calcula y para qué sirve clínicamente

La pantalla `PesoIdealActivity` (`feature_utilidades`) calcula, a partir del **sexo** y la **altura**:

- **Peso ideal (PI)** por la **fórmula de Devine**.
- **Peso ajustado (AjBW)** cuando el peso actual supera al ideal.
- **Porcentaje peso real / ideal**.

Sirve para:

- **Dosificar fármacos** en obesidad (según ficha técnica: peso real, ideal o ajustado).
- Calcular el **volumen corriente** en ventilación mecánica (peso predicho, PBW).
- Fijar el **peso de referencia** en nutrición y en el balance hídrico.
- Interpretar el grado de desviación del peso respecto al ideal.

---

## 2. Fundamento y fórmulas (con unidades)

La fórmula de Devine estima el peso asociado a una talla y un sexo, con independencia de la grasa. El **peso ajustado** corrige parcialmente el exceso de peso en obesidad para dosificar fármacos.

**Fórmulas exactas implementadas** (`PesoIdealActivity.kt`):

```
altura (pulgadas) = altura (cm) / 2,54

Peso ideal (kg) = base + 2,3 × (pulgadas − 60)
      base = 50,0   si Hombre
      base = 45,5   si Mujer
      (redondeado a 1 decimal)

Peso ajustado (AjBW) = PI + 0,4 × (peso actual − PI)      [solo si peso actual > PI]
      (redondeado a 1 decimal; se calcula con el PI ya redondeado)

% peso real / ideal = (peso actual / PI) × 100            [redondeado a entero]
```

| Variable | Unidad |
|---|---|
| Altura | cm (y pulgadas internamente) |
| PI / peso actual / AjBW | kg |
| % peso real / ideal | % |

- **1 pulgada = 2,54 cm**; referencia de la fórmula: **60 pulgadas = 152,4 cm**.
- El **AjBW solo se muestra si el peso real supera al ideal**.

> ℹ️ En el módulo de **nutrición** (`Devine.kt`) se usa la misma base de Devine expresada en centímetros y, **cuando el IMC > 30**, el peso ajustado se reparte como `PI + 0,25 × (peso − PI)`, usando el **peso ajustado para las kcal** y el **peso ideal para las proteínas**. Es una variante de reparto nutricional distinta del 0,4 de esta pantalla: no mezclar ambas cifras.

---

## 3. Variables de entrada y valores normales

| Campo | Unidad | Obligatorio |
|---|---|---|
| Sexo | Hombre (H) / Mujer (M) | Sí |
| Altura | cm | Sí (precargada de la Valoración Integral si existe, editable) |
| Peso actual | kg | No (opcional) |

**Validaciones reales de la app:**

| Situación | Mensaje |
|---|---|
| Altura no numérica o ≤ 0 | *«Introduce una altura válida en cm»* |
| Peso actual escrito pero ≤ 0 | *«El peso actual debe ser mayor que 0»* |

**Valores de referencia (lectura del % peso real/ideal, tabla de la app):**

| Categoría | Rango |
|---|---|
| Bajo peso respecto al ideal | **< 90 %** |
| Peso adecuado | **90-110 %** |
| Por encima del peso adecuado | **110-120 %** |
| Sobrepeso / obesidad respecto al ideal | **> 120 %** |

---

## 4. Interpretación por rangos y actuación de enfermería

| % peso real/ideal | Categoría | Actuación de enfermería |
|---|---|---|
| **< 90 %** | Bajo peso | *«Valora la situación nutricional y el contexto clínico»*; registrar peso y talla, valorar ingesta y riesgo de desnutrición |
| **90-110 %** | Peso adecuado | Mantener; usar el peso actual para cálculos generales |
| **110-120 %** | Por encima del adecuado | Vigilar tendencia; revisar dosis según ficha |
| **> 120 %** | Sobrepeso/obesidad | Calcular el **AjBW** y revisar las dosis de fármacos de alto riesgo |

**Avisos reales:**

- **Altura < 152,4 cm:** la fórmula de Devine **no está validada**; el resultado es solo orientativo.
- **Peso < 90 % del ideal:** valora la situación nutricional y el contexto clínico.
- **En ventilación mecánica** el volumen tidal se calcula con el **peso ideal (PBW)**, no con el real.

---

## 5. Ejemplos numéricos resueltos (3)

**Ejemplo A — hombre de 175 cm**

```
pulgadas = 175 / 2,54 = 68,9
PI = 50 + 2,3 × (68,9 − 60) = 50 + 20,5 = 70,5 kg
```

**Ejemplo B — mujer de 160 cm y 82 kg**

```
pulgadas = 160 / 2,54 = 63,0
PI   = 45,5 + 2,3 × (63,0 − 60) = 45,5 + 6,9 = 52,4 kg
AjBW = 52,4 + 0,4 × (82 − 52,4) = 52,4 + 11,8 = 64,2 kg
% peso real / ideal = 82 / 52,4 × 100 = 156 %   → sobrepeso/obesidad respecto al ideal
```

**Ejemplo C — mujer de 150 cm (por debajo de 152,4 cm)**

```
La app calcula el PI, pero muestra el aviso de que la fórmula no está validada
por debajo de 152,4 cm y que el resultado es orientativo.
```

---

## 6. Limitaciones y errores frecuentes

| Limitación / error | Comentario |
|---|---|
| **Tallas < 152,4 cm** | Fórmula no validada |
| **Usar el peso real** para el VT en SDRA | Volutrauma (debe usarse el PBW) |
| **Confundir** peso ideal, ajustado y predicho (PBW) | Dosis o VT incorrectos |
| **Aplicar AjBW** cuando el peso real es menor que el ideal | La app no lo calcula (no procede) |
| Mezclar el AjBW de **0,4** (utilidades) con el reparto nutricional de **0,25** | Aportes calórico-proteicos erróneos |
| **Altura mal introducida** (pulgadas vs cm) | PI muy erróneo |
| **No registrar** sexo y talla usados | Cálculo no reproducible |
| Interpretar el % como diagnóstico nutricional | Es una **lectura orientativa**, no un diagnóstico |

---

## 7. Cuándo NO usarla

- **Tallas < 152,4 cm** sin criterio clínico.
- **Población pediátrica**: usar tablas pediátricas.
- **Amputaciones o deformidades de columna**: la talla real no refleja la longitud corporal.
- **Como único criterio de dosificación**: la ficha técnica de cada fármaco decide el peso a usar.
- **Embarazo**: usar curvas/valores específicos.
- **Como diagnóstico nutricional**: completar con valoración dietética y escalas de riesgo (ver [mNUTRIC](../escalas/mnutric.html)).

---

## 8. Relación con otras escalas y parámetros

- **[Volumen corriente protector](volumen-corriente-protector.html)**: el PBW es la fórmula de Devine en centímetros.
- **[Gasto urinario](gasto-urinario.html)**: opción de peso ideal para normalizar la diuresis.
- **[Balance hídrico](balance-hidrico.html)**: elección coherente del peso.
- **[Perfusiones](perfusiones.html)**: dosis por kg según el peso elegido.
- **[mNUTRIC](../escalas/mnutric.html)** / **[NUTRIC](../escalas/nutric.html)**: valoración del riesgo nutricional.
- **[Cockcroft-Gault y CKD-EPI](cockcroft-ckd-epi.html)**: el peso influye en el Cockcroft.

---

## 9. Puntos clave

- **PI hombre = 50 + 2,3 × (pulgadas − 60)**; **mujer = 45,5 + 2,3 × (pulgadas − 60)**; 1 pulgada = 2,54 cm.
- **AjBW = PI + 0,4 × (peso real − PI)**, solo si el peso real supera al ideal.
- **% peso = peso real / PI × 100**: < 90 bajo · 90-110 adecuado · 110-120 por encima · > 120 obesidad.
- En **ventilación mecánica** y en **nutrición** el peso de referencia no es siempre el real.
- Validar la fórmula solo con **tallas ≥ 152,4 cm**.
- Registrar siempre **sexo, talla y peso** utilizados para reproducir el cálculo.

---

## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **Peso ideal** | Peso ideal y ajustado |
| **Volumen corriente protector** | VT por peso ideal |
| **Función renal** | Cockcroft-Gault |
| **Perfusiones** | Dosis por kg |
