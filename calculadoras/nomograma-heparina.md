---
layout: default
title: "Nomograma de heparina no fraccionada"
---
# Nomograma de heparina no fraccionada

> 📖 **Fuentes:** Raschke RA, et al. Weight-based heparin nomogram. *Ann Intern Med*. 1993;119:874-881. · Protocolo de referencia del hospital; confirmar vigencia, indicación y versión antes de aplicarlo.

## 1. Qué calcula y para qué sirve clínicamente

La pantalla `NomogramaHeparinaActivity` (`feature_cardio`) es una calculadora configurable de bolo e infusión inicial de HNF por peso y muestra el **nomograma de referencia utilizado en el hospital**. Se conserva como referencia para los centros/equipos que adopten esta pauta; no es universal ni sustituye la validación institucional ni la prescripción.

- Calcular bolo e infusión iniciales a partir del peso y los parámetros del esquema.
- Consultar el nomograma de titulación de referencia del centro.

Se usa en procesos que requieren anticoagulación sistémica: **tromboembolismo pulmonar**, **trombosis venosa profunda**, **síndrome coronario agudo** (según protocolo), **fibrilación auricular** con indicación, **prótesis valvulares** y otros (ver [ECMO: anticoagulación](../protocolos/ecmo-anticoagulacion.html) y [TRRC: anticoagulación](../protocolos/trrc-anticoagulacion.html) cuando proceda).

---

## 2. Fundamento y fórmula (con unidades)

La HNF tiene una **farmacocinética no lineal** y una respuesta interindividual muy variable, por lo que se dosifica por **peso** y se ajusta por **control del TTPa** (o anti-Xa). El nomograma ponderal clásico de Raschke es la base de los protocolos actuales.

**Fórmulas exactas implementadas** (`LogicaNomogramaHeparina.kt`):

```
Bolo (UI)        = peso (kg) × UI/kg
Infusión (UI/h)  = peso (kg) × UI/kg/h
```

| Variable | Unidad | Valor por defecto en la app |
|---|---|---|
| Peso | kg | — (obligatorio) |
| Bolo | UI/kg | **80** |
| Infusión | UI/kg/h | **18** |

**Validación real:** si el peso no es válido o ≤ 0 (o el bolo/infusión no son > 0), la app muestra *«Introduce un peso válido»* y no calcula. El resultado se presenta como **bolo con 0 decimales** y **infusión con 1 decimal**.

---

## 3. Variables de entrada y valores normales

| Variable de entrada | Rango/práctica habitual |
|---|---|
| **Peso** | Real o ajustado según protocolo (obesidad) |
| **Bolo** | 80 UI/kg (configurable según indicación/protocolo) |
| **Infusión inicial** | 18 UI/kg/h (configurable según indicación/protocolo) |
| **TTPa objetivo** | Método y objetivo dependen de indicación, reactivo/laboratorio y protocolo |
| **Anti-Xa (alternativa)** | Usar objetivo institucional validado para la indicación; no trasladar rangos entre protocolos |
| **Plaquetas** | Vigilar descenso (TIH) |
| **Hemoglobina** | Vigilar sangrado |

---

## 4. Monitorización y titulación

La app muestra el **nomograma de referencia del centro**, con TTPa objetivo 60-80 s. La relación TTPa-heparina depende del reactivo y del laboratorio; aplicar el esquema solo si coincide con la indicación y el protocolo vigente del equipo.

| TTPa | Ajuste (protocolo de referencia) | Actuación de enfermería |
|---|---|---|
| **< 35 s** | **Bolo 80 UI/kg** y **subir 4 UI/kg/h** | Administrar bolo según prescripción, subir la bomba, repetir TTPa a las 6 h |
| **35-49 s** | **Bolo 40 UI/kg** y **subir 2 UI/kg/h** | Bolo y ajuste; registrar hora y nuevo ritmo |
| **50-59 s** | **Subir 1 UI/kg/h** | Ajustar bomba, registrar, control a las 6 h |
| **60-80 s** | **Mantener** (rango terapéutico) | No cambiar; continuar controles según protocolo |
| **81-100 s** | **Bajar 1 UI/kg/h** | Reducir bomba, vigilar sangrado, control a las 6 h |
| **> 100 s** | **Parar 30-60 min** y **bajar 2-3 UI/kg/h** | Parar la infusión, avisar al médico, vigilar signos de sangrado, reanudar con el nuevo ritmo |

> El ajuste se expresa por kg. La app calcula bolo e infusión iniciales; los cambios posteriores se realizan según este protocolo de referencia y la orden vigente.

### Ejemplo de ajuste según el nomograma de referencia

Paciente de **80 kg**, infusión actual **18 UI/kg/h** (= 1 440 UI/h), TTPa **40 s**:

```
Corresponde al tramo 35-49 s:
   Bolo 40 UI/kg = 80 × 40 = 3 200 UI
   Subir 2 UI/kg/h → 18 + 2 = 20 UI/kg/h
   Nueva infusión = 80 × 20 = 1 600 UI/h
```

---

## 5. Ejemplos numéricos resueltos

**Ejemplo A — cálculo inicial con parámetros por defecto del nomograma de referencia**

```
Peso = 80 kg ; bolo 80 UI/kg ; infusión 18 UI/kg/h
Bolo     = 80 × 80 = 6 400 UI
Infusión = 80 × 18 = 1 440 UI/h
```

**Ejemplo B — parámetros configurables para otro protocolo**

```
Peso = 70 kg ; bolo 60 UI/kg ; infusión 12 UI/kg/h
Bolo     = 70 × 60 = 4 200 UI
Infusión = 70 × 12 = 840 UI/h
```

**Ejemplo C — ilustración de peso de dosificación indicado por protocolo (no recomendación)**

```
Solo si una prescripción/protocolo determina usar 70 kg como peso de dosificación:
   Bolo     = 70 × 80 = 5 600 UI
   Infusión = 70 × 18 = 1 260 UI/h
```

---

## 6. Limitaciones y errores frecuentes

| Limitación / error | Comentario |
|---|---|
| **Elegir el peso equivocado** (real vs ajustado) | Dosis fuera de rango; seguir el protocolo |
| **No repetir el control indicado** tras cada cambio | Infra o sobredosificación mantenida; frecuencia según protocolo y ensayo |
| **Redondear** el bolo o la velocidad de forma arbitraria | Desviación del objetivo |
| **HNF y HBPM confundidas** | Fármacos y unidades diferentes (UI vs mg) |
| **No controlar plaquetas** | TIH no detectada |
| **TTPa poco sensible** a niveles altos de heparina | Valorar anti-Xa si está disponible |
| Aplicar la pauta de referencia fuera de su ámbito | Confirmar indicación, protocolo y prescripción vigente |
| **No comprobar la dilución** preparada y la vía | Error de concentración |

---

## 7. Cuándo NO usarla

- **Sangrado activo grave o riesgo hemorrágico muy alto** sin indicación clara.
- **Trombocitopenia grave o sospecha/antecedente de TIH**: no reintroducir HNF; usar alternativas (argatroban, bivalirudina, fondaparinux).
- **Insuficiencia renal grave**: la HNF no se elimina por riñón (a diferencia de las HBPM), pero el protocolo y el control deben individualizarse.
- **Cuando el centro usa otro esquema** (HBPM, anti-Xa, protocolos específicos de ECMO/TRRC): seguir ese protocolo.
- **Sin posibilidad de monitorizar** TTPa/anti-Xa: no es seguro titular HNF.
- **Como sustituto de la valoración clínica**: en el tromboembolismo inestable puede requerirse trombolisis u otra estrategia.

---

## 8. Relación con otras escalas y parámetros

- **[ECMO: anticoagulación](../protocolos/ecmo-anticoagulacion.html)** y **[ECMO](../protocolos/ecmo.html)**: la HNF se usa con objetivos y controles propios.
- **[TRRC: anticoagulación](../protocolos/trrc-anticoagulacion.html)** y **[TRRC: alarmas y presiones](../guias-cuidados/trrc-alarmas.html)**: la anticoagulación del circuito puede usar HNF con objetivos distintos.
- **[TTPa y coagulación](../protocolos/transfusion.html)**: interpretación de pruebas de coagulación y manejo del sangrado.
- **[Shock: tipos y manejo](../protocolos/shock-critico.html)**: contexto del paciente crítico anticoagulado.
- **[Perfusiones](perfusiones.html)**: cálculo de velocidades de infusión de fármacos.
- **[Peso ideal](peso-ideal.html)**: elección del peso en obesidad.

---

## 9. Puntos clave

- **Bolo (UI) = peso × UI/kg**; **infusión (UI/h) = peso × UI/kg/h** (por defecto, 80 y 18).
- El objetivo de TTPa 60-80 s y la tabla corresponden al nomograma de referencia del centro; no son universales.
- **Doble comprobación** del bolo y de la velocidad; usar **bomba volumétrica** y etiquetar la línea como heparina.
- **Plaquetas seriadas**: vigilar TIH; **Hb y signos de sangrado**.
- **Protamina** como antídoto en hemorragia grave, según protocolo.
- Ajustar el **peso** (real o ajustado) y los objetivos al **protocolo del centro**.

---

## Correspondencia con la app

| Pantalla / contenido | Relación |
|---|---|
| **Nomograma de heparina** | Ajuste de dosis |
| **Anticoagulantes** | Heparina y alternativas |
| **TRRC: anticoagulación** | Citrato y heparina |
| **ECMO: anticoagulación** | ACT y TTPa |
