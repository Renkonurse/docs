# Sodio y agua libre

> 📖 **Fuentes:** Adrogué HJ, Madias NE. Hyponatremia. N Engl J Med 2000;342:1581-1589. · SEEIUC: https://www.seeiuc.org · MSD Manual Professional: https://www.msdmanuals.com/professional

## 1. Qué calcula y para qué sirve clínicamente

La app incluye **dos** pantallas complementarias para el manejo de la **disnatremia**:

| Pantalla | Clase | Qué hace |
|---|---|---|
| **Sodio y agua libre** (F1) | `SodioAguaLibreActivity` | Calcula el **agua libre** a partir del peso, el Na actual y el Na objetivo |
| **Sodio** (módulo Iones) | `SodioActivity` | Clasifica la natremia, calcula el **Na corregido** (Katz/Hillier) y el **agua libre** con factor por tipo de paciente |

Sirve para:

- **Cuantificar el déficit o el exceso de agua libre** y planificar la corrección.
- **Corregir la natremia medida** en presencia de hiperglucemia (Na corregido).
- **Fijar una velocidad de corrección segura** y evitar complicaciones neurológicas.
- **Clasificar la gravedad** de la hipo/hipernatremia y orientar la actuación.

---

## 2. Fundamento y fórmulas (con unidades)

El sodio sérico refleja la relación entre el **sodio corporal total** y el **agua corporal total (ACT)**. El **agua libre** expresa cuánta agua hay que añadir o retirar para alcanzar un Na objetivo, asumiendo que el ACT es una fracción del peso (0,6/0,5/0,45 según sexo y edad).

### Pantalla F1 — Sodio y agua libre

**Fórmula exacta** (`LogicaSodioAguaLibre.kt`):

```
Agua libre (L) = 0,6 × peso (kg) × (Na actual / Na objetivo − 1)
```

- Resultado con **2 decimales**, en **litros**.
- La app F1 usa un factor fijo **0,6** (agua corporal total del adulto).

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
| **< 125** | Hiponatremia GRAVE | Riesgo de edema cerebral y convulsiones; valorar suero hipertónico y monitorización estrecha | Avisar de inmediato; control neurológico; preparar NaCl 3 %; repetir iones cada 2-4 h |
| **125-129** | Hiponatremia MODERADA | Buscar causa: SIADH, diuréticos, hipovolemia, IC/hepática | Vigilar volemia y clínica; registrar balance y peso |
| **130-134** | Hiponatremia LEVE | Corregir causa; velocidad ≤ 8-10 mEq/L en 24 h | Control seriado; revisar fármacos |
| **135-145** | NORMONATREMIA | Rango normal | Mantener vigilancia |
| **146-150** | Hipernatremia LEVE | Corregir con cristaloides hipotónicos; velocidad ≤ 10-12 mEq/L en 24 h | Calcular déficit de agua; control seriado |
| **151-155** | Hipernatremia MODERADA | Valorar pérdidas renales/extrarrenales o diabetes insípida | Vigilar diuresis y glucemia |
| **> 155** | Hipernatremia GRAVE | Alto riesgo de alteración neurológica; reposición cuidadosa de agua libre | Avisar; monitorización neurológica estrecha |

### Interpretación del agua libre

**Pantalla del módulo Iones** (`describirAgua`):

| Agua libre | Lectura |
|---|---|
| **> +0,1 L** | **Déficit de agua** → reponer con sueros hipotónicos; ajustar con controles seriados de Na |
| **entre −0,1 y +0,1 L** | **Balance equilibrado** (Na próximo a 140) |
| **< −0,1 L** | **Exceso de agua** → restricción hídrica + tratar causa; en hiponatremia sintomática valorar NaCl 3 % |

> 🚩 **Aviso importante sobre el signo (discrepancia real entre pantallas).** La fórmula `factor × peso × (Na/Na objetivo − 1)` es la del **déficit de agua** clásico: con **hipernatremia** (Na > objetivo) da **positivo = déficit**, y con **hiponatremia** da **negativo = exceso de agua**. La pantalla del **módulo Iones** usa esa convención clásica, pero la pantalla **F1** rotula lo contrario (positivo = *exceso*, negativo = *déficit*). **Interpretar siempre en contexto clínico y no guiarse solo por la etiqueta de la pantalla F1.**

---

## 5. Velocidad de corrección (seguridad)

- **Hiponatremia:** corrección máxima **8-10 mEq/L en 24 h**. Aviso real de la pantalla F1: *«Corregir la natremia a un máximo de 8 mEq/L cada 24 horas para evitar complicaciones como la mielinolisis osmótica.»*
- **Hiponatremia sintomática** (convulsiones, coma): **bolo de NaCl 3 % 100-150 mL en 20 min**, con control estricto.
- **Hipernatremia:** corrección máxima **10-12 mEq/L en 24 h**; calcular el **déficit de agua libre** y reponerlo en **48 h** con sueros hipotónicos.
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
→ La app F1 lo etiqueta como «déficit de agua», pero fisiológicamente es EXCESO de agua
  (hiponatremia). Interpretar con la clínica (ver aviso de signo).
```

**Ejemplo C — módulo Iones, Na corregido por glucemia**

```
Mujer 60 kg, Na 128 mEq/L, glucemia 400 mg/dL, fórmula Katz
Na corregido = 128 + 0,016 × (400 − 100) = 128 + 4,8 = 132,8 mEq/L
Agua libre   = 0,50 × 60 × (128/140 − 1) = 30 × (−0,08571) = −2,57 L
→ Exceso de agua libre (restricción hídrica + tratar causa)
```

---

## 7. Limitaciones y errores frecuentes

| Limitación / error | Comentario |
|---|---|
| **Discrepancia de signo** entre pantallas | Comprobar el resultado con la clínica (ver aviso) |
| **Factor de ACT fijo 0,6** en la pantalla F1 | No distingue sexo ni edad (usar el módulo Iones) |
| **No corregir el Na por glucemia** | En hiperglucemia el Na medido subestima el real |
| **Corregir > 8-10 mEq/L/24 h** en hiponatremia | Mielinólisis central pontina |
| **Corregir > 10-12 mEq/L/24 h** en hipernatremia | Edema cerebral |
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

- **[Corrección de iones](correccion-iones.md)**: el módulo Iones incluye la pantalla de sodio y las fórmulas de Na corregido.
- **[Gasometría](gasometria.md)**: el Na participa en el anión gap y en la osmolaridad.
- **[Balance hídrico](balance-hidrico.md)** y **[gasto urinario](gasto-urinario.md)**: la volemia y la diuresis condicionan la corrección.
- **[SOFA](../escalas/sofa.md)**: el sodio y la osmolaridad no puntúan, pero contextualizan la gravedad.
- **[Glasgow](../escalas/glasgow.md)** y **[FOUR](../escalas/four.md)**: la vigilancia neurológica durante la corrección.
- **[Código Sepsis](../protocolos/codigo-sepsis.md)** y **[Shock](../protocolos/shock-critico.md)**: la reanimación y los fluidos.
- **[RCP y soporte vital](../protocolos/rcp-sva.md)**: la corrección de iones en la parada.

---

## 10. Puntos clave

- **Agua libre = factor × peso × (Na/Na objetivo − 1)**; factor **0,6** (F1) o **0,6/0,5/0,45** (Iones).
- **Na corregido = Na + 0,016 × (gluc − 100)** (Katz) o **+ 0,024 × (gluc − 100)** (Hillier).
- **Hiponatremia < 125 grave · 125-129 moderada · 130-134 leve · 135-145 normal · 146-150 leve · 151-155 moderada · > 155 grave**.
- Corregir **≤ 8-10 mEq/L/24 h** (hipo) y **≤ 10-12 mEq/L/24 h** (hiper).
- **Repetir iones cada 2-4 h** y vigilar la **clínica neurológica**.
- Ojo con la **discrepancia de signo** entre la pantalla F1 y el módulo Iones: prevalece la interpretación clínica.
