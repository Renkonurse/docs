---
layout: default
title: "Sodio y agua libre"
---
# Sodio y agua libre

> 📖 **Fuentes:** Adrogué HJ, Madias NE. Hyponatremia. *N Engl J Med*. 2000;342:1581-1589 (predicción del cambio de Na tras infundir solución; no es la fórmula de déficit de agua libre) · Sterns RH, et al. Treatment Guidelines for Hyponatremia: Stay the Course. *Clin J Am Soc Nephrol*. 2024;19:129-135. · Society for Endocrinology. Emergency management of severe symptomatic hyponatraemia in adult patients. 2016.

## 1. Qué calcula y para qué sirve clínicamente

La app incluye **dos** pantallas complementarias para el manejo de la **disnatremia**:

| Pantalla | Clase | Qué hace |
|---|---|---|
| **Sodio y agua libre** (F1) | `SodioAguaLibreActivity` | Calcula el **agua libre** a partir del peso, el Na actual y el Na objetivo |
| **Sodio** (módulo Iones) | `SodioActivity` | Clasifica la natremia, calcula el **Na corregido** (Katz/Hillier) y el **agua libre** con factor por tipo de paciente |

Sirve para:

- Obtener una **estimación matemática** del déficit/exceso relativo de agua en escenarios seleccionados; no equivale al volumen que debe administrarse o restringirse.
- **Corregir la natremia medida** en presencia de hiperglucemia (Na corregido).
- Recordar que el objetivo, la velocidad y la monitorización dependen de síntomas, duración, causa, volemia y riesgo de desmielinización; la calculadora no los determina.
- **Clasificar la gravedad** de la hipo/hipernatremia y orientar la actuación.

---

## 2. Fundamento y fórmulas (con unidades)

El sodio sérico refleja la relación entre los solutos intercambiables y el **agua corporal total (ACT)**. La ecuación de déficit de agua libre estima un cambio teórico usando una fracción del peso; no incorpora pérdidas en curso, ingesta, función renal, sodio/potasio administrados ni cambios de volumen. No debe interpretarse como una prescripción ni como fórmula de Adrogué-Madias.

### Pantalla F1 — Sodio y agua libre

**Ecuación implementada** (`LogicaSodioAguaLibre.kt`):

```
Agua libre (L) = 0,6 × peso (kg) × (Na actual / Na objetivo − 1)
```

- Resultado con **2 decimales**, en **litros**; factor fijo **0,6**, que puede sobrestimar el ACT en personas mayores, mujeres, obesidad o enfermedad crítica.
- Con esta convención matemática, signo **positivo = déficit estimado** (Na actual > objetivo) y signo **negativo = exceso relativo estimado** (Na actual < objetivo). El módulo no sustituye la evaluación de volemia ni calcula una pauta de fluidos.

### Pantalla Sodio (módulo Iones)

**Fórmulas exactas** (`SodioActivity.kt`):

```
Na corregido (Katz)    = Na + 0,016 × (glucemia − 100)      [glucemia en mg/dL]
Na corregido (Hillier) = Na + 0,024 × (glucemia − 100)

Agua libre (L)         = factor × peso × (Na / 140 − 1)
      factor = 0,60 (Varón) · 0,50 (Mujer) · 0,45 (Anciano)
```

| Variable | Unidad |
|---|---|
| Sodio sérico | mEq/L |
| Glucemia | mg/dL |
| Peso | kg |
| Agua libre | L |

Si la **glucemia ≤ 100 mg/dL o está vacía**, el Na corregido **es igual al Na actual**.

---

## 3. Variables de entrada y valores normales

**Pantalla F1:**

| Campo | Unidad | Validación |
|---|---|---|
| Peso | kg | > 0 |
| Na actual | mEq/L | > 0 |
| Na objetivo | mEq/L | > 0 |

Error real: *«Introduce peso, Na actual y Na objetivo válidos»*.

**Pantalla Sodio:** Na sérico (obligatorio), glucemia (opcional), peso (para agua libre), tipo de paciente (Varón/Mujer/Anciano) y fórmula (Katz/Hillier). Error real: incluye el aviso de que el peso es necesario para el agua libre.

**Valores de referencia:**

| Parámetro | Normal |
|---|---|
| **Sodio sérico** | **135-145 mEq/L** |
| Sodio crítico | < 120 o > 160 mEq/L |
| Glucemia en ayunas | 70-100 mg/dL |

---

## 4. Interpretación por rangos y actuación de enfermería

### Clasificación de la natremia

| Na (mEq/L) | Categoría | Detalle de la app | Actuación de enfermería |
|---|---|---|---|
| **< 125** | Hiponatremia marcada | La urgencia depende sobre todo de síntomas, rapidez de descenso y contexto; no indica automáticamente un bolo hipertónico | Avisar con urgencia y valorar estado neurológico, duración, volemia y causa con el equipo responsable; monitorizar Na con la frecuencia del tratamiento elegido |
| **125-129** | Hiponatremia MODERADA | Buscar causa: SIADH, diuréticos, hipovolemia, IC/hepática | Vigilar volemia y clínica; registrar balance y peso |
| **130-134** | Hiponatremia leve | Interpretar según síntomas, duración y causa | Revisar contexto, medicación y tendencia; el objetivo de corrección se individualiza |
| **135-145** | NORMONATREMIA | Rango normal | Mantener vigilancia |
| **146-150** | Hipernatremia | Valorar duración, volemia, pérdidas en curso y causa | Definir tipo y vía de reposición con el equipo; evitar fijar una velocidad universal |
| **151-155** | Hipernatremia MODERADA | Valorar pérdidas renales/extrarrenales o diabetes insípida | Vigilar diuresis y glucemia |
| **> 155** | Hipernatremia GRAVE | Alto riesgo de alteración neurológica; reposición cuidadosa de agua libre | Avisar; monitorización neurológica estrecha |

### Interpretación del agua libre

**Pantalla del módulo Iones** (`describirAgua`):

| Agua libre | Lectura |
|---|---|
| **> +0,1 L** | **Déficit de agua** → reponer con sueros hipotónicos; ajustar con controles seriados de Na |
| **entre −0,1 y +0,1 L** | **Balance equilibrado** (Na próximo a 140) |
| **< −0,1 L** | **Exceso de agua** → restricción hídrica + tratar causa; en hiponatremia sintomática valorar NaCl 3 % |

> 🚩 **Seguridad:** se corrigió la etiqueta de signo de F1: positivo se muestra como **déficit estimado** y negativo como **exceso relativo estimado**, coherente con la ecuación. Esto no prescribe aporte/restricción ni tiene en cuenta pérdidas, electrolitos administrados, volemia o tolerancia; comprobar evolución con controles analíticos y protocolo clínico.

---

## 5. Velocidad de corrección (seguridad)

- **Hiponatremia:** no existe un límite único aplicable a todos. En cuadros crónicos o de duración desconocida se suele limitar la corrección (a menudo ≤8 mEq/L/24 h si alto riesgo de desmielinización; objetivos y límites dependen de guía/protocolo). Medir Na con frecuencia durante tratamiento activo.
- **Hiponatremia grave sintomática:** emergencia; bolos de NaCl hipertónico según guía y protocolo vigentes, con reevaluación clínica y analítica tras cada intervención. No aplicar una pauta de bolo por el valor de Na aislado.
- **Hipernatremia:** definir si es aguda o crónica, valorar volemia y pérdidas activas, y monitorizar estrechamente. La velocidad no se deduce del cálculo de agua libre ni debe fijarse como regla uniforme; seguir protocolo especializado.
- **Complicaciones de la corrección rápida:**
  - **Mielinólisis central pontina** (hiponatremia corregida demasiado rápido).
  - **Edema cerebral** (hipernatremia corregida demasiado rápido).

**Sueros de referencia:**

| Suero | Na⁺ aproximado |
|---|---|
| Salino 0,9 % | 154 mEq/L |
| Salino 0,45 % | 77 mEq/L |
| Salino 3 % | 513 mEq/L |
| Glucosado 5 % | ~0 mEq/L de Na (agua libre) |

---

## 6. Ejemplos numéricos resueltos (3)

**Ejemplo A — F1, hipernatremia**

```
Paciente 60 kg, Na actual 155 mEq/L, Na objetivo 145 mEq/L
Agua libre = 0,6 × 60 × (155/145 − 1) = 36 × 0,06897 = +2,48 L
→ Déficit de agua: reponer con sueros hipotónicos (aprox. 2,5 L) con controles seriados
```

**Ejemplo B — F1, hiponatremia**

```
Paciente 70 kg, Na actual 125 mEq/L, Na objetivo 140 mEq/L
Agua libre = 0,6 × 70 × (125/140 − 1) = 42 × (−0,10714) = −4,50 L
→ Resultado negativo: exceso relativo estimado por la ecuación. No prescribe restricción hídrica; valorar síntomas, volemia, causa y duración de la hiponatremia.
```

**Ejemplo C — módulo Iones, Na corregido por glucemia**

```
Mujer 60 kg, Na 128 mEq/L, glucemia 400 mg/dL, fórmula Katz
Na corregido = 128 + 0,016 × (400 − 100) = 128 + 4,8 = 132,8 mEq/L
Agua libre   = 0,50 × 60 × (128/140 − 1) = 30 × (−0,08571) = −2,57 L
→ Exceso relativo estimado; no indica por sí solo restricción hídrica. Interpretar junto con síntomas, volemia y causa.
```

---

## 7. Limitaciones y errores frecuentes

| Limitación / error | Comentario |
|---|---|
| **Signo del resultado** | F1 ya usa positivo = déficit estimado y negativo = exceso relativo; confirmar entradas y no usarlo como pauta de fluidos |
| **Factor de ACT fijo 0,6** en la pantalla F1 | No distingue sexo ni edad (usar el módulo Iones) |
| **No corregir el Na por glucemia** | En hiperglucemia el Na medido subestima el real |
| **Aplicar un límite fijo de corrección sin valorar riesgo** | Riesgo de desmielinización en hiponatremia; el objetivo/límite depende de contexto y protocolo |
| **Usar una velocidad universal en hipernatremia** | Riesgo de infratratamiento o corrección inadecuada; considerar duración, causa, volemia y respuesta |
| **No repetir iones** durante la corrección | Corrección fuera de rango no detectada |
| **Olvidar la volemia** | La hiponatremia hipovolémica se corrige primero con volumen |
| **Usar Na objetivo irreal** (p. ej. 140 en hiponatremia crónica) | Corrección excesiva |
| Peso desactualizado | Agua libre proporcionalmente errónea |
| **No vigilar la clínica neurológica** | Complicaciones no detectadas |

---

## 8. Cuándo NO usarla

- **Disnatremia crónica asintomática**: corregir de forma muy gradual; la fórmula orienta, pero no fija la pauta.
- **Sin peso fiable**: el agua libre no es calculable.
- **Como única guía de reposición**: integrar con iones seriados, diuresis, balance y clínica.
- **Hiperglucemia no corregida**: usar siempre el **Na corregido**.
- **En situaciones con pérdidas/ganancias activas** (diuresis osmótica, TRRC): la fórmula es una foto fija.
- **Poblaciones con ACT alterado** (edemas, ascitis, obesidad mórbida): el factor es aproximado.
- **Como sustituto del protocolo de disnatremias** del centro.

---

## 9. Relación con otras escalas y parámetros

- **[Corrección de iones](correccion-iones.html)**: el módulo Iones incluye la pantalla de sodio y las fórmulas de Na corregido.
- **[Gasometría](gasometria.html)**: el Na participa en el anión gap y en la osmolaridad.
- **[Balance hídrico](balance-hidrico.html)** y **[gasto urinario](gasto-urinario.html)**: la volemia y la diuresis condicionan la corrección.
- **[SOFA](../escalas/sofa.html)**: el sodio y la osmolaridad no puntúan, pero contextualizan la gravedad.
- **[Glasgow](../escalas/glasgow.html)** y **[FOUR](../escalas/four.html)**: la vigilancia neurológica durante la corrección.
- **[Código Sepsis](../protocolos/codigo-sepsis.html)** y **[Shock](../protocolos/shock-critico.html)**: la reanimación y los fluidos.
- **[RCP y soporte vital](../protocolos/rcp-sva.html)**: la corrección de iones en la parada.

---

## 10. Puntos clave

- **Agua libre = factor × peso × (Na/Na objetivo − 1)**; factor **0,6** (F1) o **0,6/0,5/0,45** (Iones).
- **Na corregido = Na + 0,016 × (gluc − 100)** (Katz) o **+ 0,024 × (gluc − 100)** (Hillier).
- **Hiponatremia < 125 grave · 125-129 moderada · 130-134 leve · 135-145 normal · 146-150 leve · 151-155 moderada · > 155 grave**.
- Individualizar objetivos y velocidad de corrección; el cálculo de agua libre no los determina.
- Repetir iones y vigilar el estado neurológico con la frecuencia exigida por la situación y el tratamiento.
- El signo de F1 fue corregido: positivo = déficit estimado y negativo = exceso relativo estimado. Ninguno constituye por sí solo una prescripción.

---

## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **Sodio y agua libre** | Déficit y corrección |
| **Corrección de iones** | Sodio y potasio |
| **Gasometría** | Osmolaridad y equilibrio |
| **Valores de referencia** | Rangos |
