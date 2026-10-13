# Nomograma de heparina no fraccionada

> 📖 **Fuentes:** Raschke RA, et al. Weight-based heparin nomogram. Ann Intern Med 1993;119:874-881. · SEEIUC: https://www.seeiuc.org · MSD Manual Professional: https://www.msdmanuals.com/professional

## 1. Qué calcula y para qué sirve clínicamente

La pantalla `NomogramaHeparinaActivity` (`feature_cardio`) es una **calculadora configurable** de **bolo** e **infusión inicial** de **heparina no fraccionada (HNF)** ajustada al peso, e incluye la **tabla de ajuste según el TTPa**. Sirve para:

- Iniciar la anticoagulación con HNF de forma **estandarizada y reproducible**.
- **Ajustar la velocidad** de infusión según el control analítico (TTPa).
- Reducir la variabilidad y los errores de dosificación en un fármaco de **alto riesgo**.

Se usa en procesos que requieren anticoagulación sistémica: **tromboembolismo pulmonar**, **trombosis venosa profunda**, **síndrome coronario agudo** (según protocolo), **fibrilación auricular** con indicación, **prótesis valvulares** y otros (ver [ECMO: anticoagulación](../protocolos/ecmo-anticoagulacion.md) y [TRRC: anticoagulación](../protocolos/trrc-anticoagulacion.md) cuando proceda).

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
| **Bolo** | 80 UI/kg (configurable, p. ej. 60-80 UI/kg) |
| **Infusión inicial** | 18 UI/kg/h (configurable, p. ej. 12-18 UI/kg/h) |
| **TTPa objetivo** | **60-80 s** (equivalente a 1,5-2,5 × control) |
| **Anti-Xa (alternativa)** | 0,3-0,7 UI/mL |
| **Plaquetas** | Vigilar descenso (TIH) |
| **Hemoglobina** | Vigilar sangrado |

---

## 4. Tabla de ajuste según TTPa

Es la tabla que muestra la app (`f1_hep_tabla_p1`). **TTPa objetivo: 60-80 s.**

| TTPa | Ajuste (protocolo de la app) | Actuación de enfermería |
|---|---|---|
| **< 35 s** | **Bolo 80 UI/kg** y **subir 4 UI/kg/h** | Administrar bolo según prescripción, subir la bomba, repetir TTPa a las 6 h |
| **35-49 s** | **Bolo 40 UI/kg** y **subir 2 UI/kg/h** | Bolo y ajuste; registrar hora y nuevo ritmo |
| **50-59 s** | **Subir 1 UI/kg/h** | Ajustar bomba, registrar, control a las 6 h |
| **60-80 s** | **Mantener** (rango terapéutico) | No cambiar; continuar controles según protocolo |
| **81-100 s** | **Bajar 1 UI/kg/h** | Reducir bomba, vigilar sangrado, control a las 6 h |
| **> 100 s** | **Parar 30-60 min** y **bajar 2-3 UI/kg/h** | Parar la infusión, avisar al médico, vigilar signos de sangrado, reanudar con el nuevo ritmo |

> El ajuste se expresa **por kg**: pasar de 18 a 20 UI/kg/h en un paciente de 80 kg equivale a subir de 1 440 a 1 600 UI/h. La app **calcula el bolo y la infusión iniciales**; la aplicación de los incrementos de la tabla se hace sobre la velocidad de la bomba.

### Ejemplo de ajuste manual (interpretación de la tabla)

Paciente de **80 kg**, infusión actual **18 UI/kg/h** (= 1 440 UI/h), TTPa **40 s**:

```
Corresponde al tramo "35-49 s":
   Bolo 40 UI/kg = 80 × 40 = 3 200 UI
   Subir 2 UI/kg/h → 18 + 2 = 20 UI/kg/h
   Nueva infusión = 80 × 20 = 1 600 UI/h
```

---

## 5. Ejemplos numéricos resueltos

**Ejemplo A — cálculo inicial (nomograma por defecto)**

```
Peso = 80 kg ; bolo 80 UI/kg ; infusión 18 UI/kg/h
Bolo     = 80 × 80 = 6 400 UI
Infusión = 80 × 18 = 1 440 UI/h
```

**Ejemplo B — nomograma modificado**

```
Peso = 70 kg ; bolo 60 UI/kg ; infusión 12 UI/kg/h
Bolo     = 70 × 60 = 4 200 UI
Infusión = 70 × 12 = 840 UI/h
```

**Ejemplo C — paciente obeso (100 kg), protocolo con peso ajustado**

```
Si el protocolo indica ajustar a 70 kg de peso ajustado:
   Bolo     = 70 × 80 = 5 600 UI
   Infusión = 70 × 18 = 1 260 UI/h
```

---

## 6. Limitaciones y errores frecuentes

| Limitación / error | Comentario |
|---|---|
| **Elegir el peso equivocado** (real vs ajustado) | Dosis fuera de rango; seguir el protocolo |
| **No repetir el TTPa** tras cada cambio | Infra o sobredosificación mantenida |
| **Redondear** el bolo o la velocidad de forma arbitraria | Desviación del objetivo |
| **HNF y HBPM confundidas** | Fármacos y unidades diferentes (UI vs mg) |
| **No controlar plaquetas** | TIH no detectada |
| **TTPa poco sensible** a niveles altos de heparina | Valorar anti-Xa si está disponible |
| La app **solo calcula bolo e infusión iniciales** | La titulación posterior es manual según tabla/protocolo |
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

- **[ECMO: anticoagulación](../protocolos/ecmo-anticoagulacion.md)** y **[ECMO](../protocolos/ecmo.md)**: la HNF se usa con objetivos y controles propios.
- **[TRRC: anticoagulación](../protocolos/trrc-anticoagulacion.md)** y **[TRRC: alarmas y presiones](../guias-cuidados/trrc-alarmas.md)**: la anticoagulación del circuito puede usar HNF con objetivos distintos.
- **[TTPa y coagulación](../protocolos/transfusion.md)**: interpretación de pruebas de coagulación y manejo del sangrado.
- **[Shock: tipos y manejo](../protocolos/shock-critico.md)**: contexto del paciente crítico anticoagulado.
- **[Perfusiones](perfusiones.md)**: cálculo de velocidades de infusión de fármacos.
- **[Peso ideal](peso-ideal.md)**: elección del peso en obesidad.

---

## 9. Puntos clave

- **Bolo (UI) = peso × UI/kg**; **infusión (UI/h) = peso × UI/kg/h** (por defecto 80 y 18).
- **TTPa objetivo 60-80 s**; ajustar con la tabla de 6 tramos (< 35 / 35-49 / 50-59 / 60-80 / 81-100 / > 100 s).
- **Doble comprobación** del bolo y de la velocidad; usar **bomba volumétrica** y etiquetar la línea como heparina.
- **Plaquetas seriadas**: vigilar TIH; **Hb y signos de sangrado**.
- **Protamina** como antídoto en hemorragia grave, según protocolo.
- Ajustar el **peso** (real o ajustado) y los objetivos al **protocolo del centro**.
