# Balance hídrico y nutricional

> 📖 **Fuentes:** KDIGO. Clinical Practice Guideline for Acute Kidney Injury. Kidney Int Suppl 2012;2:1-138. · Marino PL. The ICU Book. 4th ed. Wolters Kluwer. · SEEIUC: https://www.seeiuc.org

## 1. Qué calcula y para qué sirve clínicamente

La pantalla `BalanceActivity` (`feature_nutricion`) reúne en una sola tarjeta de resultado:

- **Balance nutricional**: cumplimiento de **kcal** y **proteínas** (administrado frente a previsto).
- **Balance hídrico**: **entradas − salidas**.
- **Diuresis por kg**.

Sirve para:

- **Cuantificar el aporte** nutricional real y detectar la **infraalimentación** o la **sobrealimentación**.
- **Detectar sobrecarga o depleción de fluidos** y orientar la reposición o la restricción.
- **Evaluar la tolerancia** a la nutrición enteral y la progresión del aporte.
- **Relacionar** el balance hídrico con la diuresis y el estado de perfusión.

Los tres bloques son **independientes**: se rellena solo lo que se tenga.

---

## 2. Fundamento y fórmulas (con unidades)

**Fórmulas exactas implementadas** (`calcularBalance()` en `BalanceActivity.kt`):

```
Cumplimiento calórico (%)  = (kcal administradas / kcal previstas) × 100      [0 si previstas = 0]
Cumplimiento proteico (%)  = (prot. administradas / prot. previstas) × 100    [0 si previstas = 0]
Balance hídrico (mL)       = entradas − salidas
Diuresis por kg            = diuresis / peso          [solo si peso > 0 y diuresis > 0]
```

| Variable | Unidad |
|---|---|
| Kcal previstas / administradas | kcal |
| Proteínas previstas / administradas | g |
| Entradas / salidas | mL |
| Diuresis | **mL/24 h** (según el campo de la app) |
| Peso | kg |

> ℹ️ **Nota de unidades (discrepancia real):** el campo de diuresis está rotulado en **mL/24 h**, por lo que `diuresis / peso` son estrictamente **mL/kg/24 h**, aunque la app etiqueta la tarjeta como *«mL/kg/h»*. Si se quiere el valor en mL/kg/h, dividir el resultado entre 24 (o introducir la diuresis horaria). Para la interpretación clínica es preferible usar la calculadora específica de **[gasto urinario](gasto-urinario.md)**.

**Validación real:** si no hay ningún dato (`kcalPrev = 0`, `protPrev = 0`, `entradas = 0` y `salidas = 0`), la app muestra *«Introduce al menos un par de valores (previsto + administrado) o el balance hídrico»* y no calcula.

---

## 3. Variables de entrada y valores normales

| Bloque | Campo | Unidad |
|---|---|---|
| Nutricional | Kcal previstas | kcal |
| Nutricional | Kcal administradas | kcal |
| Nutricional | Proteínas previstas | g |
| Nutricional | Proteínas administradas | g |
| Hídrico | Entradas | mL |
| Hídrico | Salidas | mL |
| Hídrico | Diuresis | mL/24 h |
| Hídrico | Peso | kg |

**Valores de referencia orientativos del balance hídrico diario:**

| Balance (mL/24 h) | Lectura |
|---|---|
| **−500 a +500** | Aceptable |
| **> +1000** | Positivo marcado (sobrecarga) |
| **< −1000** | Negativo marcado (depleción) |

**Cumplimiento nutricional de referencia:** objetivo habitual **≥ 80 %** de las kcal y proteínas previstas.

---

## 4. Interpretación por rangos y actuación de enfermería

### Cumplimiento calórico y proteico

| Valor | Color | Mensaje de la app | Actuación de enfermería |
|---|---|---|---|
| **≥ 80 %** | Verde | *«Cumplimiento adecuado (≥ 80 %)»* | Mantener el plan; vigilar tolerancia |
| **60-79 %** | Amarillo | *«Cumplimiento parcial. Revisar tolerancia y progresión.»* | Revisar residuo gástrico, náuseas, diarrea y ritmo de infusión; ajustar con el equipo |
| **< 60 %** | Rojo | *«Cumplimiento bajo (< 60 %). Reevaluar causa y ajustar plan.»* | Buscar causa (íleo, intolerancia, interrupciones por pruebas), reevaluar plan y avisar |

### Balance hídrico

| Valor | Color | Mensaje de la app | Actuación de enfermería |
|---|---|---|---|
| **> +1000 mL** | Rojo | *«Balance positivo marcado. Valorar diurético y ajustar aportes.»* | Avisar; vigilar edemas, crepitantes, disnea, ganancia de peso |
| **0 a +1000 mL** | Amarillo | *«Balance positivo leve. Vigilar tendencia.»* | Registrar tendencia, revisar aportes |
| **< 0 mL** | Verde | *«Balance dentro de rangos aceptables.»* | Mantener registro |
| **< −1000 mL** | Verde | *«Balance negativo marcado. Valorar reposición.»* | Vigilar signos de hipovolemia; avisar si hay taquicardia/hipotensión |

### Diuresis por kg

| Valor | Color | Mensaje | Actuación |
|---|---|---|---|
| **≥ 0,5** | Verde | *«Diuresis adecuada (≥ 0,5 mL/kg/h)»* | Mantener monitorización |
| **< 0,5** | Rojo | *«🚨 Oliguria (< 0,5 mL/kg/h). Reevaluar volemia y perfusión renal.»* | Avisar; revisar volemia, PAM, sonda y nefrotóxicos |

---

## 5. Contexto clínico (marco de referencia)

- El **balance acumulado** se valora con la **tendencia** (no un valor puntual) y con el **peso diario**.
- La **sobrecarga hídrica** se estima como *porcentaje de sobrecarga = balance acumulado / peso inicial × 100*; porcentajes **> 10 %** se asocian a peor pronóstico y obligan a valorar diuréticos o TRRC. *La app no calcula este porcentaje: es un marco de interpretación.*
- Una **diuresis < 0,5 mL/kg/h durante ≥ 6 h** es criterio de **AKI (KDIGO)**: ver [gasto urinario](gasto-urinario.md).
- Las **pérdidas insensibles** deben incluirse en las salidas: ver [pérdidas insensibles](perdidas-insensibles.md).

---

## 6. Ejemplos numéricos resueltos (3)

**A) Nutricional**

```
Kcal previstas 1800, administradas 1500 ; proteínas previstas 100 g, administradas 55 g
Cumplimiento calórico = 1500 / 1800 × 100 = 83,3 %  → adecuado (verde)
Cumplimiento proteico = 55 / 100 × 100    = 55 %    → bajo (rojo)
```

**B) Hídrico**

```
Entradas 3200 mL, salidas 2700 mL, diuresis 1600 mL/24 h, peso 70 kg
Balance hídrico = 3200 − 2700 = +500 mL  → positivo leve (amarillo)
Diuresis por kg = 1600 / 70 = 22,9       → etiquetado mL/kg/h (ver nota de unidades)
```

**C) Balance negativo**

```
Entradas 1500 mL, salidas 2900 mL, diuresis 2000 mL/24 h, peso 80 kg
Balance hídrico = 1500 − 2900 = −1400 mL → negativo marcado (verde, "valorar reposición")
Diuresis por kg = 2000 / 80 = 25,0
```

---

## 7. Limitaciones y errores frecuentes

| Limitación / error | Comentario |
|---|---|
| **Infrarregistro** de aportes (fármacos, lavados, nutrición, hemoderivados) | Balance falsamente negativo |
| **No incluir** las pérdidas insensibles | Balance falsamente positivo |
| **Peso no actualizado** | Diuresis/kg errónea |
| **Confundir** el campo de diuresis (mL/24 h) con mL/h | Valor ×24 |
| **Registrar por turnos sin sumar** el acumulado | Se pierde la tendencia |
| **Balance positivo leve mantenido** | Sobrecarga acumulada no detectada |
| **Cumplimiento calculado con kcal previstas erróneas** | Objetivo nutricional mal fijado |
| Interrupciones de la nutrición por pruebas/traslados | Cumplimiento bajo no atribuible a intolerancia |
| **Síndrome de realimentación** al progresar rápido | Ver [realimentación](../protocolos/realimentacion.md) |

---

## 8. Cuándo NO usarla

- **Sin datos suficientes** (ningún bloque relleno): no calcula.
- **Sin peso** cuando se quiere la diuresis por kg.
- **Como balance de referencia en TRRC**: la diálisis elimina volumen de forma no registrada como diuresis; usar el balance de la máquina.
- **Con pérdidas no cuantificables** (sudoración intensa, quemados, drenajes abundantes): usar estimaciones y no dar al balance un valor absoluto.
- **Para ajustar nutrición en el paciente con realimentación** sin seguir el protocolo específico.
- **Como sustituto del balance acumulado** de varios días: registrar también el acumulado.

---

## 9. Relación con otras escalas y parámetros

- **[Gasto urinario](gasto-urinario.md)**: diuresis en mL/kg/h y criterios KDIGO.
- **[Pérdidas insensibles](perdidas-insensibles.md)**: se incluyen en las salidas.
- **[Peso ideal](peso-ideal.md)** y **[mNUTRIC](../escalas/mnutric.md)** / **[NUTRIC](../escalas/nutric.md)**: valoración nutricional.
- **[SOFA](../escalas/sofa.md)**: la diuresis (< 500 mL/día) puntúa en el componente renal.
- **[Síndrome de realimentación](../protocolos/realimentacion.md)**: prevención al progresar el aporte.
- **[Código Sepsis](../protocolos/codigo-sepsis.md)** y **[Shock](../protocolos/shock-critico.md)**: la reanimación con fluidos y el balance.
- **[TRRC](../protocolos/trrc.md)**: ultrafiltración y balance extracorpóreo.

---

## 10. Puntos clave

- **Balance hídrico = entradas − salidas**; registrar **todos** los aportes y pérdidas.
- **Cumplimiento = administrado / previsto × 100**; objetivo ≥ 80 % en kcal y proteínas.
- Colores de la app: balance **> +1000** rojo · **0 a +1000** amarillo · **≤ 0** verde; cumplimiento **≥ 80 %** verde · **60-79 %** amarillo · **< 60 %** rojo.
- **Diuresis < 0,5 mL/kg/h** alerta de oliguria (ojo con la unidad del campo: mL/24 h).
- Pesar al paciente **a diario** y usar el **mismo peso** de forma coherente.
- Vigilar signos de **sobrecarga** (edemas, crepitantes, disnea) y de **depleción** (taquicardia, hipotensión, oliguria).

---

## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **Balance hídrico** | Ingresos, pérdidas y Balance |
| **Gasto urinario** | Diuresis y perfusión |
| **Pérdidas insensibles** | Estimación de pérdidas |
| **Peso ideal** | Peso de referencia |
