# Conversor de unidades de uso frecuente en UCI

> 📖 **Fuentes:** MSD Manual Professional: https://www.msdmanuals.com/professional · SEEIUC: https://www.seeiuc.org · AACN: https://www.aacn.org

## 1. Qué calcula y para qué sirve clínicamente

La pantalla `ConversorUnidadesActivity` (`feature_utilidades`) convierte las magnitudes de uso diario en UCI: **masa**, **velocidad de infusión**, **concentración** y **peso**. La lógica pura está en `ConversorLogica.kt` (objeto testable).

Sirve para:

- **Preparar y comprobar diluciones** antes de administrar fármacos.
- **Pasar de ml/h a gotas/min** para perfusiones sin bomba o para verificar el equipo.
- **Convertir dosis entre unidades de masa** (mg, µg, g) y evitar errores ×1000.
- **Calcular la concentración** de una disolución (mg/mL).

Es una herramienta de apoyo al **cálculo de enfermería**; no decide la prescripción.

---

## 2. Fundamento y fórmulas (con unidades)

**Fórmulas exactas implementadas** (`ConversorLogica.kt`):

```
— MASA (conversión interna a mg) —
a mg:     mg × 1   ·   mcg (µg) × 0,001   ·   g × 1000
desde mg: mg × 1   ·   mcg × 1000         ·   g ÷ 1000

— VELOCIDAD —
gotas/min = ml/h × gotasPorMl / 60          [gotasPorMl por defecto = 20]
ml/h      = gotas/min × 60 / gotasPorMl

— CONCENTRACIÓN —
mg/ml = mg de fármaco / ml de volumen        [0,0 si ml ≤ 0, evita división por cero]

— PESO —
kg → g: × 1000          g → kg: ÷ 1000

— TIEMPO (disponible en la lógica, no en esta pantalla) —
h → min: × 60           min → h: ÷ 60
```

| Magnitud | Unidad |
|---|---|
| Masa | mg · µg (mcg) · g |
| Velocidad | ml/h · gotas/min |
| Concentración | mg/mL |
| Peso | kg · g |
| Tiempo | h · min |

---

## 3. Variables de entrada y valores normales (equivalencias)

| Bloque | Campos | Resultado |
|---|---|---|
| **Masa (mg ↔ mcg ↔ g)** | Miligramos (mg) | `= X mcg (µg)` y `= X g` |
| **Velocidad (ml/h ↔ gotas/min)** | ml/h | `= X gotas/min (20 gotas/ml)` |
| **Concentración (mg/ml)** | mg de fármaco + ml de volumen | `= X mg/mL` (botón **CALCULAR**) |
| **Peso (kg ↔ g)** | Kilogramos (kg) | `= X g` |

**Equivalencias de referencia:**

| Concepto | Equivalencia |
|---|---|
| 1 kg | 1000 g |
| 1 g | 1000 mg |
| 1 mg | 1000 µg (mcg) |
| 1 L | 1000 mL |
| 1 mL | 1 cm³ |
| 1 kg | 2,2 lb |
| Velocidad estándar | **20 gotas/mL** |
| Microgotero | **60 microgotas/mL** |

El formateo usa hasta **3 decimales** y muestra `0` si el valor es cero.

---

## 4. Interpretación y actuación de enfermería

| Resultado | Lectura y actuación |
|---|---|
| Masa convertida | Comprobar la **unidad del campo** antes de introducir (mg vs µg es el error ×1000 más frecuente) |
| gotas/min | Ajustar la **llave de perfusión** al número entero más cercano; si el equipo es microgotero, usar factor 60 |
| mg/mL | Verificar que la concentración coincide con la preparada y **etiquetar** la disolución |
| kg ↔ g | Comprobar el peso del paciente y su coherencia con el resto de cálculos del turno |

**Tabla de velocidad con equipo de 20 gotas/mL:**

| ml/h | gotas/min |
|---|---|
| 30 | 10 |
| 60 | 20 |
| 100 | 33,3 |
| 120 | 40 |
| 250 | 83,3 |

---

## 5. Ejemplos numéricos resueltos (3)

**Ejemplo A — masa**

```
0,25 g × 1000 = 250 mg
250 mg × 1000 = 250 000 µg
```

**Ejemplo B — velocidad**

```
90 ml/h con equipo de 20 gotas/mL:
gotas/min = 90 × 20 / 60 = 30 gotas/min
```

**Ejemplo C — concentración y peso**

```
400 mg en 250 mL → 400 / 250 = 1,6 mg/mL
72 kg × 1000 = 72 000 g
```

---

## 6. Limitaciones y errores frecuentes

| Limitación / error | Comentario |
|---|---|
| **Asume 20 gotas/mL** | En microgotero (60 gotas/mL) el resultado es erróneo |
| **UI ↔ mg** | No existe conversión; la actividad biológica no se convierte por peso |
| **No convierte** temperatura, presión ni osmolaridad | Usar tablas específicas |
| **Redondear antes de terminar** el cálculo | Error acumulado; redondear solo al final |
| **Confundir mg y µg** | Error ×1000 |
| **No verificar el tipo de equipo** | Gotas/min incorrectas |
| **No etiquetar** la disolución | Riesgo de error de administración |
| **Sobrecarga de decimales** en la pantalla | La app limita a 3 decimales |

---

## 7. Cuándo NO usarla

- **Fármacos en UI** (heparina, insulina) o **dosis biológicas**: no se convierten por peso.
- **Cálculo de dosis por kg** o de velocidad de perfusión: usar [perfusiones](perfusiones.md).
- **Conversiones de temperatura, presión u osmolaridad**: no están implementadas aquí.
- **Diluciones con más de un soluto** o mezclas: verificar con farmacia.
- **Como sustituto de la doble comprobación** en fármacos de alto riesgo.
- **Con equipos de goteo no estándar** sin comprobar el factor real.

---

## 8. Relación con otras escalas y parámetros

- **[Perfusiones](perfusiones.md)**: velocidades, factores de goteo y diluciones.
- **[Corrección de iones](correccion-iones.md)**: conversiones mmol/L ↔ mg/dL (Mg 2,43; P 3,10; Ca 4,008).
- **[Balance hídrico](balance-hidrico.md)** y **[gasto urinario](gasto-urinario.md)**: unidades de volumen y peso.
- **[Peso ideal](peso-ideal.md)**: elección del peso para los cálculos.
- **[MSD Manual Professional](https://www.msdmanuals.com/professional)**: tablas de conversión y dosis de referencia.

---

## 9. Puntos clave

- **mg ↔ µg ↔ g** con factor 1000; **kg ↔ g** con factor 1000.
- **gotas/min = ml/h × factor / 60**; el conversor asume **20 gotas/mL**.
- **mg/mL = mg / mL**; el resultado orienta la preparación y el etiquetado.
- **UI no se convierte** a mg: mantener 1:1 y comprobar la dilución.
- Comprobar **siempre** la unidad del campo y el tipo de equipo.
- Redondear **solo al final** y verificar con doble comprobación los fármacos de alto riesgo.
