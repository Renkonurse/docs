# PAFI (PaO₂/FiO₂) — índice de oxigenación

> 📖 **Fuentes:** ARDS Definition Task Force. Berlin definition. JAMA 2012;307:2526-2533. · ARDSNet. Ventilation with lower tidal volumes. N Engl J Med 2000;342:1301-1308. · MSD Manual Professional: https://www.msdmanuals.com/professional

## 1. Qué calcula y para qué sirve clínicamente

El **PAFI** (índice de oxigenación, *PaO₂/FiO₂*) relaciona la **presión parcial de oxígeno arterial** con la **fracción inspirada de oxígeno**. Es el parámetro central para:

- **Clasificar la gravedad del SDRA** según los criterios de Berlín (leve, moderado, grave).
- **Monitorizar la evolución** de la oxigenación y la respuesta a la PEEP, la ventilación protectora o el decúbito prono.
- **Orientar decisiones** de escalada o desescalada del soporte respiratorio.
- **Comunicar** de forma estandarizada la gravedad del fallo respiratorio entre profesionales.

Un PAFI alto indica buena oxigenación para la FiO₂ administrada; un PAFI bajo indica que se necesita mucho oxígeno para mantener una PaO₂ aceptable.

---

## 2. Fundamento y fórmula (con unidades)

El PAFI normaliza la PaO₂ por la concentración de oxígeno inspirado: así, un mismo valor puede compararse aunque cambie la FiO₂. La lógica asume que la PaO₂ es proporcional a la FiO₂ (aproximación válida en rangos fisiológicos, menos exacta con FiO₂ muy altas o shunts extremos).

**Fórmula exacta implementada** (`PafiActivity.kt` y `GasometriaActivity.kt`):

```
FiO₂ (fracción) = FiO₂ (%) / 100

PAFI (mmHg) = PaO₂ (mmHg) / FiO₂ (fracción)
```

Equivalentemente: `PAFI = PaO₂ × 100 / FiO₂(%)`.

| Variable | Unidad | Descripción |
|---|---|---|
| **PaO₂** | mmHg | Presión parcial de oxígeno en sangre arterial (gasometría) |
| **FiO₂** | % (1-100) | Fracción inspirada de oxígeno del ventilador/dispositivo |
| **PAFI** | mmHg (adimensional en la práctica) | Índice de oxigenación |

> La app pide la FiO₂ **en porcentaje** y la convierte internamente a fracción. La PaO₂ se mide en la gasometría arterial.

---

## 3. Variables de entrada y valores normales

**Entradas (validaciones reales de la app):**

| Campo | Validación |
|---|---|
| PaO₂ (mmHg) | Debe ser **> 0**; si no: *«La PaO₂ debe ser mayor que 0»* |
| FiO₂ (%) | Debe estar **entre 1 y 100**; si no: *«FiO₂ debe estar entre 1 y 100 (%)»* |
| Campos vacíos/no numéricos | *«Rellena ambos campos con números válidos»* |

**Valores de referencia:**

| Parámetro | Normal |
|---|---|
| **PaO₂** (aire ambiente, FiO₂ 0,21) | 80-100 mmHg |
| **FiO₂** ambiente | 21 % |
| **PAFI** en pulmón sano | > 400-500 mmHg |
| **PAFI** umbral de SDRA | ≤ 300 mmHg **con PEEP/CPAP ≥ 5 cmH₂O** |

---

## 4. Interpretación por rangos y actuación de enfermería

| PAFI (mmHg) | Categoría (Berlín) | Actuación de enfermería |
|---|---|---|
| **> 300** | No cumple criterios de SDRA | Mantener el soporte, vigilar tendencia, comprobar que la FiO₂ es la real |
| **201-300** | SDRA **leve** | Ventilación protectora (VT 6 mL/kg de PBW), vigilar Pplat ≤ 30 y ΔP ≤ 15; registrar PEEP y FiO₂ |
| **101-200** | SDRA **moderado** | Optimizar PEEP y sedación; valorar prono si persiste; control estricto de presiones y balance |
| **≤ 100** | SDRA **grave** | Avisar al equipo de inmediato; valorar PEEP alta, prono, bloqueo neuromuscular y traslado a centro de referencia |

**Actuación transversal:** repetir la medición **con la misma FiO₂ y PEEP** para poder comparar; registrar siempre junto al PAFI la **PEEP**, la **FiO₂**, el **VT** y la **Pplat** del momento; comunicar cualquier descenso mantenido.

---

## 5. Ejemplos numéricos resueltos (2-3)

**Ejemplo A — SDRA moderado**

```
PaO₂ = 80 mmHg ; FiO₂ = 40 %
FiO₂ (fracción) = 0,40
PAFI = 80 / 0,40 = 200 mmHg  → SDRA moderado
```

**Ejemplo B — SDRA grave**

```
PaO₂ = 60 mmHg ; FiO₂ = 60 %
FiO₂ (fracción) = 0,60
PAFI = 60 / 0,60 = 100 mmHg  → SDRA grave
```

**Ejemplo C — sin criterios de SDRA**

```
PaO₂ = 95 mmHg ; FiO₂ = 28 %
FiO₂ (fracción) = 0,28
PAFI = 95 / 0,28 ≈ 339 mmHg  → no cumple criterios de SDRA
```

---

## 6. Criterios de Berlín (2012): las 4 condiciones

Para diagnosticar SDRA deben cumplirse **las 4**:

| # | Condición | Detalle |
|---|---|---|
| 1 | **Inicio agudo** | Dentro de la primera semana desde el evento desencadenante o la aparición/empeoramiento de los síntomas respiratorios |
| 2 | **Hipoxemia** | **PAFI ≤ 300 mmHg con PEEP o CPAP ≥ 5 cmH₂O** |
| 3 | **Origen pulmonar** | **Opacidades bilaterales** en radiografía o TC no explicables por derrame, atelectasia o nódulos |
| 4 | **Exclusión de edema cardiogénico** | Fallo respiratorio no atribuible completamente a insuficiencia cardíaca o sobrecarga hídrica; valorar ecocardiografía si hay duda |

> ⚠️ El PAFI aislado **no diagnostica** el SDRA. La app lo recuerda en el diálogo de criterios: *«requiere PEEP ≥ 5 cmH₂O y descartar origen cardiogénico»*.

---

## 7. Limitaciones y errores frecuentes

| Limitación / error | Comentario |
|---|---|
| **FiO₂ introducida como fracción** (0,4 en vez de 40) | El PAFI sale falsamente muy alto (error ×100) |
| **FiO₂ estimada** y no la real del dispositivo | Resultado no comparable |
| **No registrar la PEEP** | El PAFI no interpretable según Berlín (requiere PEEP ≥ 5) |
| **Agitación, desconexión o fuga** antes de la muestra | PaO₂ falsamente baja |
| **Muestra con burbujas o demorada** | PaO₂ falsamente alta o baja según el caso |
| **Cambiar la FiO₂** justo antes de la gasometría sin registrarlo | Comparaciones inválidas |
| El PAFI **no distingue** el mecanismo de la hipoxemia (shunt, V/Q, hipoventilación) | Complementar con gasometría completa |
| **Poca sensibilidad** con FiO₂ altas | A FiO₂ 1,0 el PAFI refleja sobre todo el shunt |
| No valora el **trabajo respiratorio** ni el confort | Valorar clínica y mecanica ventilatoria |

---

## 8. Cuándo NO usarla

- **Sin gasometría arterial fiable**: no estimar la PaO₂ a partir de la SpO₂ para el PAFI (la relación no es lineal).
- **Sin conocer la FiO₂ real** (paciente en aire ambiente con aporte no medido): usar FiO₂ 0,21 solo si realmente respira aire.
- **Como único criterio de SDRA**: se precisan las otras 3 condiciones de Berlín.
- **Para decidir intubación o extubación por sí solo**: valorar clínica, mecánica y evolución conjunta (ver [weaning](../protocolos/weaning-extubacion.md)).
- **En insuficiencia respiratoria crónica hipercápnica** sin agudización: interpretar con la situación basal del paciente.
- **Con cambios rápidos de FiO₂**: el índice no es comparable entre medidas con distinta FiO₂/PEEP.

---

## 9. Relación con otras escalas y parámetros

- **Criterios de Berlín (SDRA)**: el PAFI es el criterio de hipoxemia.
- **[Murray](../escalas/murray.md)**: puntuación de lesión pulmonar que también usa la oxigenación y la PEEP.
- **[SOFA](../escalas/sofa.md)**: incluye la oxigenación (PaO₂/FiO₂ con soporte respiratorio) en la puntuación respiratoria.
- **[ROX](../escalas/rox.md)**: SpO₂/FiO₂/FR, útil en la insuficiencia respiratoria con CNAF.
- **[Gasometría](gasometria.md)**: la app calcula el PAFI también dentro de la interpretación gasométrica.
- **[Volumen corriente protector](volumen-corriente-protector.md)**: la estrategia protectora (VT 6 mL/kg de PBW, Pplat ≤ 30, ΔP ≤ 15) es la base del manejo del SDRA.
- **[Weaning y extubación](../protocolos/weaning-extubacion.md)** y **[alarmas respiratorias](../guias-cuidados/alarmas-respiratorias.md)**: contexto del soporte y de la retirada.

---

## 10. Puntos clave

- `PAFI = PaO₂ / FiO₂(fracción)`; la app pide **FiO₂ en %**.
- **> 300** sin criterios · **201-300** leve · **101-200** moderado · **≤ 100** grave.
- El diagnóstico de SDRA exige además **inicio agudo**, **opacidades bilaterales**, **exclusión de causa cardiogénica** y **PEEP ≥ 5 cmH₂O**.
- Repetir con la **misma FiO₂ y PEEP**; registrar siempre PEEP, VT y Pplat.
- Tomar la muestra en condiciones adecuadas (jeringa heparinizada, sin burbujas, procesado precoz).
- El PAFI orienta, pero la decisión clínica es del equipo.
