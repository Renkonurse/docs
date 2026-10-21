# Ventilación protectora: PBW, volumen corriente, driving pressure y compliance

> 📖 **Fuentes:** ARDSNet. Ventilation with lower tidal volumes. N Engl J Med 2000;342:1301-1308. · ARDS Definition Task Force. Berlin definition. JAMA 2012;307:2526-2533. · Marino PL. The ICU Book. 4th ed. Wolters Kluwer.

## 1. Qué calcula y para qué sirve clínicamente

La app implementa la **ventilación mecánica protectora** en dos pantallas complementarias:

| Pantalla | Clase | Contenido |
|---|---|---|
| **Volumen corriente protector** (F1) | `VolumenCorrienteProtectorActivity` | PBW, VT objetivo, driving pressure y compliance estática en un solo cálculo |
| **Calculadoras respiratorias** | `CalculadorasRespiratoriasActivity` | Pestañas: **Peso predicho**, **VC protector**, **Driving P** y **Compliance** |

Sirve para:

- Fijar el **volumen corriente (VT)** según el **peso corporal predicho (PBW)**, no el peso real.
- **Limitar las presiones** y reducir la **lesión pulmonar inducida por el ventilador** (*volutrauma*, *barotrauma*, *atelectrauma*).
- Calcular la **driving pressure (ΔP)** y la **compliance estática (Cst)**, que se asocian a la mortalidad en el SDRA.
- **Monitorizar la evolución** de la mecánica respiratoria y ajustar la PEEP.

La lógica pura está en `LogicaVolumenCorrienteProtector.kt` y `LogicaCalculadoraRespiratoria.kt`.

---

## 2. Fundamento y fórmulas (con unidades)

El pulmón sano se ventila según su tamaño real; el pulmón lesionado reduce su **zona aireada** («pulmón de bebé»), por lo que el VT debe calcularse sobre la **talla** (PBW), que estima el tamaño pulmonar, no sobre el peso real (que incluye grasa y edema).

**Fórmulas exactas implementadas:**

```
PBW hombre (kg) = 50   + 0,91 × (talla_cm − 152,4)
PBW mujer  (kg) = 45,5 + 0,91 × (talla_cm − 152,4)

VT objetivo (mL) = PBW (kg) × mL/kg          [por defecto 6 mL/kg; rango 4-8]

Driving pressure ΔP (cmH₂O) = Pmeseta − PEEP

Compliance estática Cst (mL/cmH₂O) = VT / (Pmeseta − PEEP)   [solo si ΔP > 0]
```

Constantes: incremento **0,91 kg/cm** (equivale a 2,3 kg por pulgada), talla de referencia **152,4 cm = 60 pulgadas**, bases **50 kg (hombre)** y **45,5 kg (mujer)**.

| Variable | Unidad |
|---|---|
| Talla | cm |
| PBW | kg |
| VT | mL |
| Pmeseta (Pplat) | cmH₂O |
| PEEP | cmH₂O |
| ΔP | cmH₂O |
| Cst | mL/cmH₂O |

> La app **no estima** la PEEP ni la Pmeseta: se introducen del ventilador. La compliance se calcula con el **VT objetivo**, no con el VT real medido.

---

## 3. Variables de entrada y valores normales

**Pantalla F1 (`VolumenCorrienteProtectorActivity`):**

| Campo | Unidad | Por defecto |
|---|---|---|
| Sexo | Hombre / Mujer | Hombre |
| Talla | cm | — |
| mL/kg | mL/kg (4-8) | **6** |
| Pmeseta | cmH₂O | — |
| PEEP | cmH₂O | — |

**Validación real:** talla numérica > 0; si no, *«Introduce una talla válida»*. ΔP y Cst solo se calculan si se introducen Pmeseta y PEEP.

**Valores de referencia:**

| Parámetro | Objetivo |
|---|---|
| VT | **6 mL/kg de PBW** (rango 4-8) |
| Pplat (Pmeseta) | **≤ 30 cmH₂O** |
| Driving pressure ΔP | **< 15 cmH₂O** (óptimo < 13) |
| Cst normal (sin SDRA) | **≥ 60 mL/cmH₂O** |

---

## 4. Interpretación por rangos y actuación de enfermería

### Volumen corriente

| Categoría | mL/kg de PBW | Actuación de enfermería |
|---|---|---|
| **Protector** | **6** | Configuración de referencia en SDRA; comprobar VT real |
| **Intermedio** | **7** | Valorar según evolución y presiones |
| **Convencional** | **8** | Solo fuera del SDRA o según prescripción; vigilar Pplat y ΔP |

> *«Objetivo en SDRA: 6 mL/kg de peso predicho. Valorar 4-8 mL/kg según evolución.»*

### Driving pressure (ΔP = Pplat − PEEP)

| Valor | Interpretación | Actuación |
|---|---|---|
| **< 13 cmH₂O** | **Óptimo** | Mantener; vigilar tendencia |
| **13-15 cmH₂O** | **Límite** | Optimizar PEEP, sedación y VT; revisar |
| **> 15 cmH₂O** | **Elevado** | Avisar; reducir VT/compliance-dependentes, valorar PEEP y prono |

> *«ΔP = Pplat − PEEP. Objetivo < 15 cmH₂O en SDRA.»*

### Compliance estática (Cst = VT / (Pplat − PEEP))

| Valor | Interpretación | Actuación |
|---|---|---|
| **≥ 60 mL/cmH₂O** | **Normal** | Mantener |
| **40-60** | **Reducida** | Vigilar; optimizar PEEP |
| **20-40** | **Muy reducida** | Avisar; estrategia de SDRA (VT bajo, PEEP, prono) |
| **< 20** | **Grave** | Avisar de inmediato; valorar escalada de soporte |

Si `Pmeseta − PEEP ≤ 0`, la compliance **no se calcula** (evita división por un valor no válido).

---

## 5. Ejemplos numéricos resueltos (3)

**Ejemplo A — varón de 175 cm, 6 mL/kg, Pmeseta 26, PEEP 8**

```
PBW = 50 + 0,91 × (175 − 152,4) = 50 + 20,46 = 70,46 ≈ 70,5 kg
VT  = 70,46 × 6 = 422,8 ≈ 423 mL
ΔP  = 26 − 8 = 18 cmH₂O                 → elevado (> 15)
Cst = 422,8 / 18 = 23,5 mL/cmH₂O        → muy reducida (20-40)
```

**Ejemplo B — mujer de 160 cm, 6 mL/kg**

```
PBW = 45,5 + 0,91 × (160 − 152,4) = 45,5 + 6,92 = 52,4 kg
VT  = 52,4 × 6 = 314,4 ≈ 314 mL
```

**Ejemplo C — varón de 170 cm, rango 4-8 mL/kg**

```
PBW = 50 + 0,91 × (170 − 152,4) = 50 + 16,02 = 66,0 kg
VT a 4 mL/kg = 264 mL
VT a 6 mL/kg = 396 mL
VT a 8 mL/kg = 528 mL
```

---

## 6. Limitaciones y errores frecuentes

| Limitación / error | Comentario |
|---|---|
| **Usar el peso real** en vez del PBW | VT excesivo → volutrauma |
| **Introducir la altura en pulgadas** | PBW erróneo |
| Medir la Pplat **sin pausa inspiratoria** o con esfuerzo activo | ΔP y Cst falsos |
| No medir/estimar la **PEEP total** (auto-PEEP) | ΔP infravalorada |
| Calcular la Cst con el **VT real** en vez del objetivo | No reproducible (la app usa el objetivo) |
| **Formula de PBW no validada** en tallas extremas (< 152,4 cm) | Resultado orientativo |
| **Hipercapnia permisiva** mal tolerada | pH fuera del objetivo (≥ 7,20-7,25) |
| Olvidar la **presión meseta** en pacientes con respiración espontánea | Pplat no fiable |
| Confundir Pplat con **presión pico** | La pico refleja resistencia de la vía aérea |
| No registrar **FiO₂/PEEP** junto al cálculo | Interpretación incompleta |

---

## 7. Cuándo NO usarla

- **Ventilación espontánea sin oclusión** o modos con esfuerzo activo: la Pplat y la ΔP no son fiables.
- **Pacientes pediátricos/neonatales**: la fórmula es de **adulto**; usar tablas pediátricas.
- **Tallas < 152,4 cm**: el PBW es orientativo.
- **Fugas importantes** o tubo desconectado: presiones no válidas.
- **Como única guía de programación del ventilador**: integrar con gasometría, clínica y protocolo de SDRA (PEEP según tabla FiO₂-PEEP).
- **Sin medir la Pplat** con pausa: no calcular ΔP/Cst.
- **En ventilación no invasiva**: la Pplat no se mide igual.

---

## 8. Relación con otras escalas y parámetros

- **[PAFI](pafi.md)** y **[gasometría](gasometria.md)**: la oxigenación y el diagnóstico de SDRA.
- **[Criterios de Berlín]**: el VT protector forma parte del manejo del SDRA.
- **[Murray](../escalas/murray.md)** y **[SOFA](../escalas/sofa.md)**: gravedad del daño pulmonar y disfunción orgánica.
- **[ROX](../escalas/rox.md)**: índice de oxigenación en CNAF.
- **[Weaning y extubación](../protocolos/weaning-extubacion.md)**: transición del soporte.
- **[Alarmas respiratorias](../guias-cuidados/alarmas-respiratorias.md)**: presiones, VT y alarmas del ventilador.
- **[Peso ideal](peso-ideal.md)**: el PBW es la fórmula de Devine expresada en centímetros.

---

## 9. Puntos clave

- **PBW hombre = 50 + 0,91 × (talla − 152,4)**; **mujer = 45,5 + 0,91 × (talla − 152,4)**.
- **VT = PBW × mL/kg** con objetivo **6 mL/kg** (rango 4-8).
- **ΔP = Pplat − PEEP**, objetivo **< 15 cmH₂O** (< 13 óptimo).
- **Cst = VT / (Pplat − PEEP)**; normal ≥ 60, muy reducida 20-40, grave < 20.
- Medir la **Pplat con pausa inspiratoria** y usar el **PEEP total**.
- **Pplat ≤ 30 cmH₂O** y aceptar **hipercapnia permisiva** (pH ≥ 7,20-7,25) antes que presiones dañinas.
- El cálculo orienta; la programación final es del equipo prescriptor.

---

## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **Volumen corriente protector** | PBW, VT y driving pressure |
| **Modos ventilatorios** | Ajuste y monitorización |
| **SDRA** | Ventilación protectora |
| **PAFI** | Oxigenación |
