---
layout: default
title: "Cálculo de perfusiones y dosis"
---
# Cálculo de perfusiones y dosis

> 📖 **Fuentes:** Marino PL. The ICU Book. 4th ed. Wolters Kluwer. · SEEIUC: https://www.seeiuc.org · MSD Manual Professional: https://www.msdmanuals.com/professional

## 1. Qué calcula y para qué sirve clínicamente

El módulo incluye cuatro pantallas de cálculo (`feature_app3`):

| Pantalla | Clase | Para qué sirve |
|---|---|---|
| **Por peso** | `PorPesoActivity` | De una **dosis por kg/hora** a **mL/hora** (modo directo) y de mL/hora a dosis (inverso) |
| **Concentración** | `ConcentracionActivity` | **Volumen (mL)** para administrar una dosis concreta |
| **Velocidad de infusión** | `VelocidadActivity` | Velocidad ↔ tiempo de infusión y **gotas/min** según el factor de goteo |
| **Perfusiones** | `PerfusionesActivity` | Lista de perfusiones guardadas y **matriz de compatibilidad** |

Sirve para:

- **Preparar y verificar** perfusiones de fármacos de alto riesgo (vasoactivos, sedantes, insulina…).
- **Calcular la velocidad de la bomba** a partir de la prescripción por kg.
- **Comprobar la dosis real** que recibe el paciente.
- **Ajustar el goteo** cuando no hay bomba o para verificar el equipo.
- **Evitar incompatibilidades** al compartir una misma vía.

> ⚠️ Aviso de la app: *«Dosis orientativas: verifica con el protocolo de tu unidad y la ficha técnica antes de administrar»*.

---

## 2. Fundamento y fórmulas (con unidades)

Concepto central: **concentración = masa / volumen**. A partir de ella se pasa de dosis a velocidad y viceversa. La magnitud interna de todos los cálculos es **mg** (y mg/kg/h).

### Modo directo — Velocidad (dosis → mL/h) (`calcularVelocidadPorPeso`)

```
concentración (mg/mL) = masa de la disolución (convertida a mg) / mL de disolución
dosis total (mg/h)    = dosis (convertida a mg/kg/h) × peso (kg)
mL/hora               = dosis total (mg/h) / concentración (mg/mL)
mL/minuto             = mL/hora / 60
```

Forma clásica si la dosis es **por minuto**: `mL/h = (dosis × peso × 60) / concentración (mismas unidades)`.

Condiciones: peso > 0, mL de disolución > 0, masa > 0 y dosis ≥ 0 (`pf_error_valores` / `pf_error_campos`).

### Modo inverso — Dosis (mL/h → dosis) (`calcularDosisInversa`)

```
concentración (mg/mL)    = masa (mg) / mL de disolución
masa administrada (mg/h) = velocidad (mL/h) × concentración (mg/mL)
dosis (mg/kg/h)          = masa administrada (mg/h) / peso (kg)
dosis mostrada           = conversión real de mg/kg/h a la unidad elegida
dosis por minuto         = dosis por hora / 60
```

### Concentración (`calcularVolumenConcentracion`)

```
mL a administrar = (dosis × mL de disolución) / masa de la disolución
```

(dosis y masa convertidas a mg).

### Velocidad de infusión (`VelocidadActivity`)

```
Modo Velocidad:
   minutos totales = (horas × 60) + minutos
   mL/min = volumen / minutos totales
   mL/h   = mL/min × 60
   gotas/min = mL/min × factor de goteo

Modo Tiempo:
   minutos totales = (volumen / velocidad) × 60
   horas = minutos totales / 60 (parte entera) ; minutos = resto
```

### Conversión de unidades de masa (núcleo del cálculo)

| Unidad | Hacia mg (`aMg`) | Desde mg (`desdeMg`) |
|---|---|---|
| **mg** | × 1 | × 1 |
| **µg** | × 0,001 | × 1000 |
| **g** | × 1000 | ÷ 1000 |
| **UI** | × 1 (sin conversión real) | × 1 (sin conversión real) |

> ⚠️ **UI:** no existe conversión automática UI ↔ mg; la app mantiene 1:1 y avisa: *«Unidad UI: no existe conversión automática UI↔mg. Se mantiene 1:1; comprueba la dilución preparada.»*

---

## 3. Variables de entrada y valores normales

| Pantalla | Campos |
|---|---|
| Por peso | Peso (kg), mL de disolución, masa + unidad (mg/µg/g/UI), dosis (por kg/hora) + unidad, ver resultado en hora/minuto |
| Concentración | mL de disolución, masa + unidad, dosis necesaria + unidad |
| Velocidad | Volumen (mL), horas + minutos (modo Velocidad) o velocidad mL/h (modo Tiempo), factor de goteo |
| Perfusiones | Nombre, masa, volumen, diluyente, notas, rango clínico (rango habitual, indicación, depende del peso, máximo autorizado, fuente) |

**Factores de goteo disponibles:** **10 · 15 · 20 · 60 gtt/mL** (60 = microgotero).

**Rangos de dosis:** cada perfusión puede tener un **rango de dosis opcional** (misma unidad que la dosis por kg/h); si se rellena, la app avisa cuando el resultado queda fuera:

> ⚠️ *«Dosis fuera del rango habitual para \<fármaco\> (\<rango\>). Comprueba la prescripción antes de administrar.»*

---

## 4. Interpretación por rangos y actuación de enfermería

| Resultado | Lectura | Actuación de enfermería |
|---|---|---|
| **mL/h dentro del rango** | Dosis correcta | Programar bomba, etiquetar y registrar |
| **mL/h fuera de rango** | Dosis fuera de lo habitual | **Parar y verificar** prescripción, dilución y peso antes de administrar |
| **gotas/min** | Velocidad de goteo | Ajustar la llave; comprobar el factor del equipo (macro/micro) |
| **mg/mL** | Concentración de la disolución | Verificar contra la preparación real y **etiquetar** |
| **UI** | Sin conversión a mg | Comprobar la dilución preparada y la unidad correcta |

**Buenas prácticas de verificación:**

- **Doble comprobación** independiente de cálculo, dilución y velocidad.
- Comprobar la **unidad del campo** antes de introducir el número (mg vs µg = error ×1000).
- Recalcular y **reetiquetar** tras cualquier cambio de dilución o prescripción.
- Repasar la **compatibilidad** antes de compartir vía; ante duda, vías separadas o purga.

---

## 5. Ejemplos numéricos resueltos (3)

**Ejemplo A — modo directo (dopamina)**

```
200 mg en 250 mL, 70 kg, dosis 300 µg/kg/h (equivale a 5 µg/kg/min)
Concentración = 200 / 250 = 0,8 mg/mL
Dosis = 300 µg/kg/h = 0,3 mg/kg/h
Dosis total = 0,3 × 70 = 21 mg/h
mL/h = 21 / 0,8 = 26,25 ≈ 26 mL/h
```

**Ejemplo B — modo inverso**

```
De la disolución anterior, si se administran 26,25 mL/h a 70 kg:
Masa/h = 26,25 × 0,8 = 21 mg/h
Dosis = 21 / 70 = 0,3 mg/kg/h = 300 µg/kg/h
```

**Ejemplo C — goteo y concentración**

```
500 mL en 8 h con equipo de 20 gotas/mL:
minutos = 480 ; mL/min = 500/480 = 1,042 ; mL/h = 62,5 ; gotas/min = 1,042 × 20 ≈ 21

Concentración: 5 mg de un fármaco preparado como 100 mg en 50 mL
mL = (5 × 50) / 100 = 2,5 mL
```

---

## 6. Lista de perfusiones y compatibilidad

Cada perfusión guarda **nombre, masa, volumen, diluyente, notas y rango clínico**. Se puede crear, editar, eliminar, buscar y restaurar la lista de fábrica.

- El chip **«Depende del peso»** se activa si la unidad del rango contiene `/kg`.
- Los rangos sin respaldo en ficha se marcan con chip naranja (**práctica clínica, no estándar**).
- La **matriz de compatibilidad** devuelve: COMPATIBLE · INCOMPATIBLE · COMPATIBLE EN SITUACIONES ESPECIALES · SOLO COMPATIBLE EN SUERO GLUCOSADO · SOLO COMPATIBLE EN SUERO FISIOLÓGICO · SIN DATOS (consultar otra fuente).

---

## 7. Limitaciones y errores frecuentes

| Limitación / error | Consecuencia |
|---|---|
| Confundir **µg y mg** (×1000) | Sobredosis o infradosificación grave |
| Introducir la dosis «por minuto» cuando el campo es «por hora» | Error ×60 |
| Usar el **peso real** en obesidad sin criterio | Sobredosis → ver [peso ideal](peso-ideal.html) |
| Mezclar fármacos **incompatibles** | Precipitación, pérdida de efecto |
| No recalcular tras cambiar la dilución | Velocidad errónea |
| **UI tratadas como mg** | Dosis biológica incorrecta |
| Redondear demasiado pronto | Error acumulado |
| Goteo calculado con el **factor de equipo equivocado** | Velocidad incorrecta |
| No etiquetar la bomba o la línea | Riesgo de error en el relevo |

---

## 8. Cuándo NO usarla

- **Sin prescripción clara** de dosis, dilución y vía: no calcular «a ciegas».
- **Fármacos en UI** sin comprobar la dilución (no hay conversión real).
- **Como sustituto de la doble comprobación** de fármacos de alto riesgo.
- **Con pesos o diluciones desconocidos**: obtener los datos primero.
- **Para nutrición parenteral o mezclas complejas**: usar protocolo/farmacia.
- **Para quimioterapia u otras perfusiones específicas**: protocolo propio.
- **Si el resultado queda fuera del rango** sin poder confirmarlo con prescriptor/ficha.

---

## 9. Relación con otras escalas y parámetros

- **[Conversor de unidades](conversor-unidades.html)**: masa, velocidad, concentración y peso.
- **[Peso ideal](peso-ideal.html)**: elección del peso para la dosis.
- **[Hemodinámica](hemodinamica.html)**: los vasoactivos calculados aquí se titulan según IC/RVS/PAM.
- **[Nomograma de heparina](nomograma-heparina.html)**: perfusión de HNF con ajuste por TTPa.
- **[Gasometría](gasometria.html)** y **[gasto urinario](gasto-urinario.html)**: monitorización de la respuesta.
- **[Corrección de iones](correccion-iones.html)**: velocidades máximas de reposición.

---

## 10. Puntos clave / seguridad

- **mL/h = dosis total (mg/h) / concentración (mg/mL)**; **mL/min = mL/h / 60**.
- **gotas/min = mL/min × factor**; factores 10/15/20/60 gtt/mL.
- Conversión interna siempre en **mg**; **UI nunca se convierte**.
- **Doble comprobación**, etiquetado de bomba y línea, y recalculo tras cada cambio.
- Comprobar la **compatibilidad** antes de compartir vía; fotoprotección si procede.
- Las dosis son orientativas: **manda la prescripción y el protocolo del centro**.

---

## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **Perfusiones** | Dosis y velocidad |
| **Conversor de unidades** | mg, µg y gotas/min |
| **Incompatibilidades** | Mezclas y diluyentes |
| **Vasopresores** | Fármacos de alto riesgo |
