# Gasometría: interpretación ácido-base (y oxigenación)

> 📖 **Fuentes:** Berend K, et al. Physiological approach to assessment of acid-base disturbances. N Engl J Med 2014;371:1434-1445. · ARDS Definition Task Force. Berlin definition. JAMA 2012;307:2526-2533. · MSD Manual Professional: https://www.msdmanuals.com/professional

La pantalla `GasometriaActivity` (`feature_utilidades`) es la calculadora más completa del módulo: interpreta el **trastorno ácido-base**, calcula la **compensación esperada**, el **anión gap**, el **delta-delta**, el **PAFI** y otros parámetros, y ofrece una **explicación detallada** y un **resumen de actuación**.

---

## 1. Modos y datos que pide

La pantalla tiene dos modos: **«Básica + O₂»** y **«Completa»**.

| Grupo | Campo | Unidad | Obligatorio |
|---|---|---|---|
| **Obligatorios** | pH | — | Sí |
| | PaCO₂ | mmHg | Sí |
| | HCO₃⁻ | mmol/L | Sí |
| **Oxigenación** | PaO₂ | mmHg | No |
| | FiO₂ | % | No |
| **Modo completo** | Na⁺ | mEq/L | No |
| | Cl⁻ | mEq/L | No |
| | K⁺ | mEq/L | No |
| | Lactato | mmol/L | No |
| | BE (*base excess*) | — | No |

**Validaciones de la app**

| Situación | Mensaje |
|---|---|
| Falta pH, PaCO₂ o HCO₃⁻ | *«Rellena pH, PaCO₂ y HCO₃⁻»* |
| pH fuera de rango fisiológico | *«pH fuera de rango fisiológico (6,5 – 8,0)»* |

El resultado muestra la línea `pH X.XX · PaCO₂ X · HCO₃⁻ X` y una tarjeta de **INTERPRETACIÓN** con la opción *«Ver explicación»*.

---

## 2. Valores normales de referencia

| Parámetro | Normal |
|---|---|
| **pH** | **7,35-7,45** |
| **PaCO₂** | **35-45 mmHg** |
| **HCO₃⁻** | **22-26 mmol/L** (la app marca el alto a partir de **> 28** para evitar falsos mixtos) |
| **PaO₂** | 80-100 mmHg |
| **SaO₂** | 95-100 % |
| **BE** | −2 a +2 |
| **Anión gap** | 8-12 mEq/L |

---

## 3. Algoritmo de interpretación (lógica exacta del código)

```
acidemia  = pH < 7,35
alcalemia = pH > 7,45

PaCO₂ alta  = PaCO₂ > 45        PaCO₂ baja  = PaCO₂ < 35
HCO₃⁻ bajo  = HCO₃⁻ < 22        HCO₃⁻ alto  = HCO₃⁻ > 28
```

### Si hay acidemia (pH < 7,35)

| Condición | Diagnóstico |
|---|---|
| PaCO₂ alta **y** HCO₃⁻ bajo | **Acidosis mixta (respiratoria + metabólica)** |
| PaCO₂ alta (HCO₃ no bajo) | **Acidosis respiratoria** — **aguda** o **crónica** según la compensación esperada |
| HCO₃⁻ bajo (PaCO₂ no alta) | **Acidosis metabólica** |
| Ninguna de las anteriores | **Acidemia (mixta o compensada)** |

### Si hay alcalemia (pH > 7,45)

| Condición | Diagnóstico |
|---|---|
| PaCO₂ baja **y** HCO₃⁻ alto | **Alcalosis mixta (respiratoria + metabólica)** |
| PaCO₂ baja (HCO₃ no alto) | **Alcalosis respiratoria** — **aguda** o **crónica** según la compensación |
| HCO₃⁻ alto (PaCO₂ no baja) | **Alcalosis metabólica** |
| Ninguna de las anteriores | **Alcalemia (mixta o compensada)** |

### Si el pH es normal

| Condición | Diagnóstico |
|---|---|
| PaCO₂ y HCO₃⁻ normales | **Gasometría en valores normales** |
| PaCO₂ alta **y** HCO₃⁻ alto | **Trastorno compensado (pH normal)** |
| PaCO₂ baja **y** HCO₃⁻ bajo | **Trastorno compensado (pH normal)** |
| Cualquier otra combinación | **Alteración ácido-base leve (pH normal)** |

### Determinación agudo vs crónico (acidosis/alcalosis respiratoria)

El código compara el HCO₃⁻ real con el esperado en la forma **aguda** y en la **crónica**, y elige la que queda **más cerca** (menor diferencia absoluta):

```
Acidosis respiratoria:
    HCO₃⁻ esperado agudo   = 24 + 0,1  × (PaCO₂ − 40)
    HCO₃⁻ esperado crónico = 24 + 0,35 × (PaCO₂ − 40)

Alcalosis respiratoria:
    HCO₃⁻ esperado agudo   = 24 − 0,2  × (40 − PaCO₂)
    HCO₃⁻ esperado crónico = 24 − 0,45 × (40 − PaCO₂)
```

---

## 4. Compensación esperada (fórmulas exactas)

### Trastornos metabólicos → PaCO₂ esperada

| Trastorno | Fórmula | Tolerancia |
|---|---|---|
| **Acidosis metabólica** | **PaCO₂ = 1,5 × HCO₃⁻ + 8** *(Winter)* | **± 2** |
| **Alcalosis metabólica** | **PaCO₂ = 0,7 × HCO₃⁻ + 21** | **± 2** |

- Si la PaCO₂ real queda **por debajo** del límite inferior (± 2 y 0,5 de margen) → **hiperventilación excesiva** (componente respiratorio añadido).
- Si queda **por encima** del límite superior → **hipoventilación** (componente respiratorio añadido).
- Dentro del rango → **compensación respiratoria adecuada**.

### Trastornos respiratorios → HCO₃⁻ esperado

| Trastorno | Fórmula | Tolerancia |
|---|---|---|
| **Acidosis respiratoria aguda** | HCO₃⁻ = 24 + 0,1 × (PaCO₂ − 40) | ± 2 |
| **Acidosis respiratoria crónica** | HCO₃⁻ = 24 + 0,35 × (PaCO₂ − 40) | ± 2 |
| **Alcalosis respiratoria aguda** | HCO₃⁻ = 24 − 0,2 × (40 − PaCO₂) | ± 2 |
| **Alcalosis respiratoria crónica** | HCO₃⁻ = 24 − 0,45 × (40 − PaCO₂) | ± 2 |

- HCO₃⁻ por debajo del rango → **compensación renal insuficiente** (componente metabólico añadido).
- Por encima → **compensación renal excesiva** (componente metabólico añadido).
- Dentro → **compensación renal adecuada**.

> En los **trastornos mixtos** la app explica que *no hay compensación fisiológica*, sino dos trastornos primarios simultáneos, y que requieren tratamiento de ambos componentes.

---

## 5. Anión gap y delta-delta (solo en modo completo, con Na⁺ y Cl⁻)

```
Anión gap (AG) = Na⁺ − (Cl⁻ + HCO₃⁻)          Normal: 8-12 mEq/L

ΔAG     = AG − 12
ΔHCO₃⁻  = 24 − HCO₃⁻
Delta-delta = ΔAG / ΔHCO₃⁻                     [solo si ΔHCO₃⁻ > 0]
```

**Interpretación del AG:**

| Situación | Lectura |
|---|---|
| **AG > 12** | Elevado: sugiere acidosis metabólica con anión gap aumentado (cetoacidosis, lactato, uremia, tóxicos) |
| **AG 8-12** | Normal |
| **AG < 8** | Disminuido: hipoalbuminemia, hipercloremia o fármacos catiónicos |

**Interpretación del delta-delta:**

| Ratio | Lectura |
|---|---|
| **< 0,4** | Acidosis metabólica hiperclorémica añadida |
| **0,4-1,0** | Acidosis metabólica pura (AG elevado) |
| **1,0-2,0** | Acidosis metabólica + alcalosis metabólica |
| **> 2,0** | Alcalosis metabólica predominante |

> La app muestra el cálculo desarrollado: `X − (Y + Z) = W mEq/L` y `ΔAG / ΔHCO₃⁻ = ratio`.

---

## 6. Oxigenación: PAFI (si hay PaO₂ y FiO₂)

```
FiO₂ (fracción) = FiO₂ (%) / 100
PAFI = PaO₂ / FiO₂ (fracción)
```

| PAFI | Categoría |
|---|---|
| **> 300** | No cumple criterios de SDRA |
| **201-300** | SDRA leve |
| **101-200** | SDRA moderado |
| **≤ 100** | SDRA grave |

> *«Recuerda: requiere PEEP ≥ 5 cmH₂O y descartar origen cardiogénico para diagnóstico de SDRA.»* (Ver [PAFI](pafi.md) y los criterios de Berlín.)

---

## 7. Otros parámetros (modo completo)

| Parámetro | Interpretación de la app |
|---|---|
| **Lactato > 2 mmol/L** | Elevado: sugiere hipoperfusión tisular o metabolismo anaerobio |
| **Lactato ≤ 2 mmol/L** | Normal |
| **K⁺ > 5,5 mEq/L** | Hiperpotasemia |
| **K⁺ < 3,5 mEq/L** | Hipopotasemia |
| **BE < −2** | Déficit de bases (acidosis metabólica) |
| **BE > +2** | Exceso de bases (alcalosis metabólica) |

---

## 8. Resumen de actuación (mensajes de la app)

| Situación | Mensaje |
|---|---|
| Normal | *«Gasometría sin alteraciones. No requiere intervención específica.»* |
| Mixto | *«Trastorno mixto: requiere corrección simultánea de los dos componentes. Vigilar respuesta con gasometrías seriadas.»* |
| Compensado con pH normal | *«pH en rango normal gracias a la compensación fisiológica. El trastorno de base sigue presente.»* |
| Bien compensado | *«El trastorno primario está bien compensado. Tratar la causa subyacente.»* |
| Componente adicional | *«Existe un componente adicional no compensado. Revisar causas mixtas.»* |

> *«Esta interpretación es orientativa. Valora siempre el contexto clínico completo del paciente.»*

---

## 9. Ejemplos numéricos resueltos

### A) Acidosis metabólica con gap elevado

**pH 7,20 · PaCO₂ 28 · HCO₃⁻ 10 · Na⁺ 140 · Cl⁻ 100 · lactato 4,5**

```
pH 7,20 < 7,35 → acidemia
HCO₃⁻ 10 < 22 (bajo) y PaCO₂ 28 no es alta → ACIDOSIS METABÓLICA

Compensación (Winter): PaCO₂ esperada = 1,5 × 10 + 8 = 23 ± 2 → 21-25
PaCO₂ real = 28 > 25 → hipoventilación (componente respiratorio añadido)

AG = 140 − (100 + 10) = 30 mEq/L → ELEVADO (> 12)
ΔAG = 30 − 12 = 18 ;  ΔHCO₃⁻ = 24 − 10 = 14
Delta-delta = 18 / 14 = 1,29 → acidosis metabólica + alcalosis metabólica

Lactato 4,5 > 2 → elevado (hipoperfusión)
```

### B) Alcalosis respiratoria aguda

**pH 7,52 · PaCO₂ 28 · HCO₃⁻ 22**

```
pH 7,52 > 7,45 → alcalemia
PaCO₂ 28 < 35 y HCO₃⁻ 22 no es alto → ALCALOSIS RESPIRATORIA

HCO₃⁻ esperado agudo   = 24 − 0,2 × (40 − 28)  = 21,6
HCO₃⁻ esperado crónico = 24 − 0,45 × (40 − 28) = 18,6
Real 22 → más cerca del agudo (|22−21,6| = 0,4) → ALCALOSIS RESPIRATORIA AGUDA
```

### C) Acidosis respiratoria crónica con compensación renal adecuada

**pH 7,33 · PaCO₂ 60 · HCO₃⁻ 31**

```
pH 7,33 < 7,35 → acidemia
PaCO₂ 60 > 45 (alta) y HCO₃⁻ 31 no es bajo → ACIDOSIS RESPIRATORIA

HCO₃⁻ esperado agudo   = 24 + 0,1  × (60 − 40) = 26
HCO₃⁻ esperado crónico = 24 + 0,35 × (60 − 40) = 31
Real 31 → más cerca del crónico (|31−31| = 0) → ACIDOSIS RESPIRATORIA CRÓNICA

Compensación esperada: HCO₃⁻ = 24 + 0,35 × (60 − 40) = 31 ± 2 → 29-33
Real 31 → dentro del rango → compensación renal ADECUADA
```

### D) pH normal con trastorno compensado

**pH 7,36 · PaCO₂ 60 · HCO₃⁻ 33**

```
pH en rango normal, PaCO₂ alta y HCO₃⁻ alto → TRASTORNO COMPENSADO (pH normal)
Resumen de la app: «pH en rango normal gracias a la compensación fisiológica.
El trastorno de base sigue presente, pero el organismo lo ha compensado.»
```

(En el caso de pH normal la app **no** aplica las fórmulas de compensación esperada: solo clasifica el patrón y ofrece el resumen.)

---

## 10. Toma de muestra y cuidados de enfermería

- **Jeringa heparinizada**, sin burbujas, y **análisis precoz** (o en frío según el gasómetro): las burbujas y la demora elevan falsamente la PaO₂ y alteran el pH.
- Anotar la **FiO₂, la PEEP y la temperatura** del paciente en el momento de la extracción.
- Evitar la punción en zonas con **infiltración o edema**; comprimir bien el punto de punción arterial.
- **Prueba de Allen** (o evaluación del flujo colateral) antes de la punción radial cuando proceda.
- Correlacionar con la **clínica**: nivel de conciencia, patrón respiratorio, hemodinámica, perfusión.
- Comprobar que el valor de **HCO₃⁻** es el del gasómetro y no el del laboratorio (pueden diferir), y que las unidades son correctas.
- Repetir la gasometría tras **cambios de ventilación** (habitualmente a los 20-30 min) y tras intervenciones relevantes.
- Vigilar las **alarmas del ventilador** y la saturación de forma continuada.

---

## 11. Integración con Monitorización

La pantalla permite **guardar la gasometría en Monitorización** (en el paciente más reciente), mapeando los valores a los sistemas correspondientes: **Cardiovascular, Respiratorio, Neurológico, Renal y metabólico, Temperatura/infección, Balance hídrico y Monitorización avanzada (índices)**. También permite **copiar el resultado**.

---

## 12. Actuación de enfermería por tipo de trastorno

| Diagnóstico | Actuación de enfermería |
|---|---|
| **Acidosis metabólica** | Vigilar perfusión, lactato y glucemia; revisar causas (cetoacidosis, láctica, renal, tóxicos); control de iones; avisar si el AG está elevado |
| **Alcalosis metabólica** | Revisar vómitos, aspiración gástrica y diuréticos; vigilar K⁺ y Cl⁻; control de la volemia |
| **Acidosis respiratoria** | Comprobar la ventilación (frecuencia, fugas, secreciones); en VM revisar parámetros y alarmas; vigilar nivel de conciencia |
| **Alcalosis respiratoria** | Valorar dolor, ansiedad, fiebre, sepsis o hipoxemia; ajustar analgesia y soporte |
| **Trastorno mixto** | Tratamiento simultáneo de ambos componentes; gasometrías seriadas; avisar al equipo |
| **Trastorno compensado (pH normal)** | Tratar la causa de base; no interpretar el pH normal como ausencia de enfermedad |
| **Normal** | Sin intervención específica; mantener vigilancia |

---

## 13. Limitaciones y errores frecuentes

| Limitación / error | Comentario |
|---|---|
| **Burbujas o demora** en la muestra | Altera la PaO₂ y el pH |
| **No registrar FiO₂/PEEP/temperatura** del momento | Interpretación incompleta |
| **HCO₃⁻ del gasómetro vs laboratorio** | Pueden diferir; comprobar la fuente |
| **Umbral alto de HCO₃⁻ (28)** | Evita falsos mixtos, pero puede infradiagnosticar alcalosis leves |
| **Compensación con tolerancia ± 2** | Aproximación; no sustituye al juicio clínico |
| **AG sin albúmina** | En hipoalbuminemia infravalora el AG real |
| **Delta-delta solo si AG elevado y HCO₃ < 24** | No se calcula en otras situaciones |
| **PAFI sin PEEP** | No interpretable según Berlín |
| **Interpretar un solo parámetro** | Error diagnóstico |
| **pH fuera de 6,5-8,0** | La app avisa y no interpreta (valor no fisiológico) |

---

## 14. Cuándo NO usarla

- **Sin muestra arterial fiable** o con datos incompletos (pH, PaCO₂ o HCO₃⁻).
- **Como único criterio diagnóstico**: integrar con la clínica y otras pruebas.
- **En sangre venosa/ capilar** para interpretar la oxigenación (la PaO₂ no es comparable).
- **Con FiO₂ desconocida** para el PAFI.
- **Para sustituir la valoración del ventilador** o de la perfusión.
- **En trastornos crónicos estables** sin contexto basal: el pH «normal» puede ser compensación crónica.

---

## 15. Relación con otras escalas y parámetros

- **[PAFI](pafi.md)**: índice de oxigenación y criterios de Berlín.
- **[Corrección de iones](correccion-iones.md)**: anión gap, delta-delta, osmolaridad y electrolitos.
- **[Volumen corriente protector](volumen-corriente-protector.md)**: estrategia ventilatoria y mecánica.
- **[SOFA](../escalas/sofa.md)**: oxigenación y disfunción orgánica.
- **[ROX](../escalas/rox.md)**: oxigenación en CNAF.
- **[Hemodinámica](hemodinamica.md)**: lactato y perfusión.
- **[Alarmas respiratorias](../guias-cuidados/alarmas-respiratorias.md)** y **[weaning](../protocolos/weaning-extubacion.md)**: soporte y retirada.

---

## 16. Puntos clave

- **pH 7,35-7,45 · PaCO₂ 35-45 · HCO₃⁻ 22-26**; el alto de HCO₃⁻ se marca a **> 28**.
- Algoritmo: pH → PaCO₂/HCO₃⁻ → **agudo vs crónico** → **compensación esperada**.
- **Winter:** PaCO₂ = 1,5 × HCO₃⁻ + 8 ± 2; **alcalosis metabólica:** 0,7 × HCO₃⁻ + 21 ± 2.
- Respiratorias: **24 + 0,1/0,35 × (PaCO₂ − 40)** (acidosis) y **24 − 0,2/0,45 × (40 − PaCO₂)** (alcalosis).
- **AG = Na − (Cl + HCO₃)**, normal 8-12; **delta-delta = (AG − 12)/(24 − HCO₃⁻)**.
- La interpretación es **orientativa**: valorar siempre el contexto clínico completo.

---

## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **Gasometría** | Interpretación ácido-base |
| **PAFI** | Oxigenación |
| **Corrección de iones** | Electrolitos |
| **Valores de referencia** | Rangos y unidades |
