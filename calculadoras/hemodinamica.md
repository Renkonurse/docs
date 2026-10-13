# Monitorización hemodinámica avanzada

> 📖 **Fuentes:** Marino PL. The ICU Book. 4th ed. Wolters Kluwer. · SEEIUC: https://www.seeiuc.org · MSD Manual Professional: https://www.msdmanuals.com/professional

## 1. Qué es y para qué sirve clínicamente

La pantalla `MonitorizacionActivity` (`feature_utilidades`) es una **herramienta de referencia y registro** para la hemodinámica avanzada: se introducen los valores del monitor y la app los **clasifica** como **NORMAL / BAJO / ALTO** respecto a su rango y propone **recomendaciones** generales.

Sirve para:

- **Interpretar de forma estandarizada** los parámetros del PiCCO/catéter de arteria pulmonar/ecocardiografía.
- **Detectar patrones de shock** (hipovolémico, cardiogénico, distributivo, obstructivo).
- **Orientar el uso de inotrópicos, vasopresores y vasodilatadores** y la respuesta a volumen.
- **Registrar y comunicar** los parámetros por turnos.

> ℹ️ **Importante:** la app **no calcula** los índices a partir de otros parámetros (no deriva el GC del VS × FC ni las RVS de la PAM y el GC). Los valores se **introducen** tal como los muestra el monitor/catéter. El motor de la app compara cada valor con su rango.

---

## 2. Fundamento y parámetros

La hemodinámica integra **flujo** (GC/IC), **presiones** (PAM, PVC, PCP, PAP) y **resistencias** (RVS/IRVS, RVP), junto con la **respuesta a volumen** (PPV/SVV, VTI) y la **perfusión tisular** (SvO₂/ScvO₂). Ningún parámetro aislado define el estado hemodinámico: la interpretación es **conjunta**.

**Lógica de clasificación implementada:**

```
valor < mínimo normal  → BAJO  (naranja)
valor > máximo normal  → ALTO  (rojo)
dentro del rango       → NORMAL (verde)
```

La pantalla tiene una **pestaña General** (parámetros clave de manejo) y pestañas por categoría: **Bomba cardíaca, Contractilidad, Precarga, Postcarga, Presiones pulmonares y Perfusión tisular**.

---

## 3. Variables de entrada y valores normales

### Pestaña General

| Parámetro | Rango normal | Unidad | Descripción |
|---|---|---|---|
| **GC** — Gasto cardíaco | **4,0-8,0** | L/min | Volumen eyectado por el corazón por minuto |
| **IC** — Índice cardíaco | **2,5-4,0** | L/min/m² | GC normalizado por superficie corporal. Clave para inotrópicos |
| **IRVS** — Índice RVS | **1700-2400** | dyn·s·cm⁻⁵·m² | RVS normalizadas. Clave para vasopresores |
| **RVS** | **800-1200** | dyn·s·cm⁻⁵ | Resistencia al flujo en la circulación sistémica. Clave para vasopresores |
| **PPV** — Variación de la presión de pulso | **< 13** | % | Fluctuación de la presión del pulso entre inspiración y espiración |
| **SVV** — Variación del volumen sistólico | **< 13** | % | Variación del VS durante el ciclo respiratorio |
| **PAM** — Presión arterial media | **65-90** | mmHg | Presión de perfusión de órganos |

### Bomba cardíaca

| Parámetro | Rango normal | Unidad | Descripción |
|---|---|---|---|
| **GC** | 4,0-8,0 | L/min | Volumen eyectado por minuto |
| **IC** | 2,5-4,0 | L/min/m² | GC normalizado por superficie corporal |
| **VS** — Volumen sistólico | **60-100** | mL | Volumen eyectado en cada latido |
| **IVS** — Índice de volumen sistólico | **33-47** | mL/m² | VS normalizado por superficie corporal |
| **ITB** — Índice de trabajo cardíaco | **0,5-0,7** | W/m² | Potencia cardíaca total (flujo × presión) |

### Contractilidad

| Parámetro | Rango normal | Unidad | Descripción |
|---|---|---|---|
| **dP/dt max** | **400-1800** | mmHg/s | Contractilidad miocárdica intrínseca |
| **FEVI** — Fracción de eyección VI | **> 55** | % | Porcentaje del volumen telediastólico que se eyecta |
| **TAPSE** | **> 17** | mm | Función sistólica del ventrículo derecho |

### Precarga

| Parámetro | Rango normal | Unidad | Descripción |
|---|---|---|---|
| **PVC** — Presión venosa central | **2-8** | mmHg | Presión en vena cava / aurícula derecha |
| **PCP** — Presión capilar pulmonar | **6-12** | mmHg | Presión de enclavamiento (precarga del VI) |
| **PPV** | < 13 | % | Predictor dinámico de respuesta a volumen |
| **SVV** | < 13 | % | Predictor dinámico de respuesta a volumen |
| **VTI** — Integral velocidad-tiempo aórtica | **> 18** | cm | Refleja volumen sistólico y precarga efectiva |

### Postcarga

| Parámetro | Rango normal | Unidad | Descripción |
|---|---|---|---|
| **PAM** | 65-90 | mmHg | Presión de perfusión de órganos |
| **RVS** | 800-1200 | dyn·s·cm⁻⁵ | Resistencia al flujo sistémico |
| **IRVS** | 1700-2400 | dyn·s·cm⁻⁵·m² | RVS normalizado por superficie corporal |
| **RVP** — Resistencias vasculares pulmonares | **< 250** | dyn·s·cm⁻⁵ | Resistencia al flujo en la circulación pulmonar |

### Presiones pulmonares

| Parámetro | Rango normal | Unidad | Descripción |
|---|---|---|---|
| **PAPs** — Presión arterial pulmonar sistólica | **15-30** | mmHg | Pico sistólico en arteria pulmonar |
| **PAPd** — Presión arterial pulmonar diastólica | **4-12** | mmHg | Presión diastólica en arteria pulmonar |
| **PAPm** — Presión arterial pulmonar media | **10-20** | mmHg | Presión media en arteria pulmonar |

### Perfusión tisular

| Parámetro | Rango normal | Unidad | Descripción |
|---|---|---|---|
| **SvO₂** — Saturación venosa mixta | **65-75** | % | O₂ residual tras la extracción tisular (arteria pulmonar) |
| **ScvO₂** — Saturación venosa central | **70-75** | % | Equivalente a SvO₂ pero en vena cava superior |

---

## 4. Interpretación por rangos y actuación de enfermería

### Recomendaciones automáticas (lógica real de la app)

La app prioriza **IC sobre GC**, **IRVS sobre RVS** y **PPV sobre SVV**:

| Parámetro | Condición | Recomendación | Actuación de enfermería |
|---|---|---|---|
| **IC / GC** | IC < 2,5 o GC < 4,0 | 🩵 *Inotrópicos (dobutamina, levosimendán, milrinona)* | Preparar/etiquetar inotrópico, vigilar PA y arritmias |
| | IC > 4,0 o GC > 8,0 | ⚡ *Gasto elevado: descartar shock distributivo/sepsis* | Vigilar fiebre, lactato, vasoplejía |
| | En rango | ✅ *Gasto adecuado* | Mantener |
| **IRVS / RVS** | IRVS < 1700 o RVS < 800 | 💉 *Considerar vasopresores (noradrenalina)* | Preparar vasopresor por vía central, vigilar perfusión distal |
| | IRVS > 2400 o RVS > 1200 | 🌊 *Vasodilatadores o reducir vasopresores* | Vigilar PA y respuesta |
| | En rango | ✅ *Resistencias adecuadas* | Mantener |
| **PPV / SVV** | **> 13 %** | 💧 *RESPONDE A VOLUMEN: valorar carga* | Preparar volumen según prescripción; reevaluar tras la carga |
| | ≤ 13 % | ✅ *Probablemente no precisa volumen* | No cargar de forma indiscriminada |
| **PAM** | **< 65 mmHg** | 🚨 *PAM baja: riesgo de hipoperfusión* | Avisar; preparar vasopresor; vigilar perfusión |
| | **> 90 mmHg** | ⚠️ *PAM elevada: valorar reducir vasopresores* | Revisar dosis de vasoactivos |
| | 65-90 mmHg | ✅ *PAM en rango* | Mantener |

> *«Orientativo. Correlaciona con la clínica y los protocolos de tu unidad.»*

### Patrones hemodinámicos (diálogo de la app)

| Patrón | Interpretación |
|---|---|
| **IC bajo + RVS altas** | Bajo gasto con vasoconstricción compensadora → **shock cardiogénico o hipovolémico** |
| **IC alto + RVS bajas** | **Shock distributivo**: séptico, anafiláctico o neurogénico |
| **IC bajo + PCP alta + PVC normal** | **Fallo cardíaco izquierdo** con congestión pulmonar |
| **IC bajo + PVC alta + PCP normal** | **Fallo cardíaco derecho** con congestión sistémica |
| **IC bajo + PVC baja + PCP baja** | **Hipovolemia**: valorar respuesta a volumen |
| **PPV o SVV > 13 %** | Predictor positivo de respuesta a volumen (*fluid responder*) |
| **SvO₂ < 65 % o ScvO₂ < 70 %** | Aumento de la extracción tisular de O₂ → gasto cardíaco insuficiente |
| **PAM < 65 mmHg** | Riesgo de hipoperfusión de órganos |
| **VTI > 18 cm + PPV/SVV bajos** | Precarga y función sistólica adecuadas → no precisa volumen |

---

## 5. Ejemplos numéricos resueltos (3)

**Ejemplo A — shock cardiogénico**

```
GC 3,2 L/min (BAJO) ; IC 1,8 L/min/m² (BAJO) ; RVS 1800 dyn·s·cm⁻⁵ (ALTO) ; PAM 60 mmHg
Lectura: IC bajo + RVS altas → shock cardiogénico o hipovolémico
Recomendaciones de la app: inotrópicos (IC bajo) + PAM < 65 (avisar, valorar vasopresor)
```

**Ejemplo B — shock distributivo (séptico)**

```
GC 9,5 L/min (ALTO) ; IC 5,2 L/min/m² (ALTO) ; RVS 600 dyn·s·cm⁻⁵ (BAJO) ; PAM 58 mmHg
Lectura: IC alto + RVS bajas → shock distributivo
Recomendaciones: descartar sepsis + vasopresores + PAM baja (avisar)
```

**Ejemplo C — respuesta a volumen**

```
PPV 18 % ; SVV 16 % ; PAM 72 mmHg
Lectura: PPV/SVV > 13 % → responde a volumen
Recomendación: valorar carga de volumen y reevaluar tras la expansión
```

---

## 6. Limitaciones y errores frecuentes

| Limitación / error | Comentario |
|---|---|
| **Interpretar un único parámetro aislado** | Diagnóstico hemodinámico erróneo |
| **Medir PPV/SVV con arritmia** o respiración espontánea | Falso positivo/negativo de respuesta a volumen |
| **Transductor desnivelado** | Presiones falsamente altas o bajas |
| **No registrar** el soporte ventilatorio ni las dosis de vasoactivos | Tendencia no interpretable |
| **Confundir RVS e IRVS** | Umbral de actuación equivocado |
| **Atribuir un GC bajo a hipovolemia** sin valorar PCP/PVC | Carga de volumen en un fallo cardíaco |
| **La app no calcula** los índices | Hay que introducirlos del monitor |
| Valores **introducidos mal** (unidades o decimales) | Clasificación incorrecta |
| **Fiabilidad limitada** de la PVC/PCP como precarga | Usar predictores dinámicos y ecografía |

---

## 7. Cuándo NO usarla

- **Sin monitor hemodinámico fiable** o con catéter mal posicionado/calibrado.
- **Como sustituto de la ecocardiografía** o de la valoración clínica.
- **PPV/SVV** en arritmias, ventilación espontánea, VT bajo (< 8 mL/kg) o frecuencia respiratoria alta.
- **En respiración espontánea** para decidir volumen con PPV/SVV.
- **Para programar dosis** de vasoactivos: la app solo orienta.
- **En el paciente pediátrico** sin rangos específicos.
- **Sin registrar las condiciones de medida** (posición, PEEP, momento del ciclo).

---

## 8. Relación con otras escalas y parámetros

- **[Shock: tipos y manejo](../protocolos/shock-critico.md)**: clasificación y tratamiento del shock.
- **[Código Sepsis](../protocolos/codigo-sepsis.md)**: el shock distributivo y la reanimación.
- **[SOFA](../escalas/sofa.md)** y **[qSOFA](../escalas/qsofa.md)**: disfunción orgánica y cribado.
- **[Gasto urinario](gasto-urinario.md)**: la diuresis como marcador de perfusión.
- **[Gasometría](gasometria.md)**: lactato, PAFI y oxigenación.
- **[PAFI](pafi.md)**: oxigenación en el paciente crítico.
- **[Perfusiones](perfusiones.md)**: cálculo de dosis de vasoactivos.
- **[Balance hídrico](balance-hidrico.md)**: la respuesta a volumen y el balance.

---

## 9. Puntos clave

- La app **clasifica e interpreta**: no calcula los índices; se introducen del monitor.
- **GC 4-8 L/min · IC 2,5-4 · RVS 800-1200 · IRVS 1700-2400 · PPV/SVV < 13 % · PAM 65-90**.
- Recomendaciones: IC bajo → inotrópicos; RVS bajas → vasopresores; RVS altas → vasodilatadores; PPV/SVV > 13 % → volumen; **PAM < 65 → avisar**.
- Patrones: **IC bajo + RVS altas** (cardiogénico/hipovolémico) · **IC alto + RVS bajas** (distributivo) · **congestión** según PCP/PVC.
- **Calibrar y nivelar** el sistema; registrar condiciones de medida y dosis de vasoactivos.
- Interpretación **conjunta** con la clínica, la diuresis y el lactato.
