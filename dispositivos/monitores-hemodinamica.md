# Monitores de hemodinámica avanzada

Documento de apoyo del submódulo **Monitorización → Hemodinámica avanzada** de RenCoNurse CriticalCare. Describe qué aporta cada monitor, qué accesos y material necesita, cómo se monta y qué límites tiene.

> **Aviso clínico.** Material orientativo para personal entrenado. La indicación, la inserción, la calibración y la interpretación corresponden al equipo responsable. El montaje concreto depende del manual del fabricante, del modelo y del protocolo del centro.

---

## 1. Para qué sirve la monitorización hemodinámica avanzada

La monitorización avanzada intenta responder preguntas que la clínica y la monitorización básica no resuelven por sí solas:

- ¿Cuál es el gasto cardíaco y cómo evoluciona?
- ¿El paciente responderá a volumen o está ya en la parte plana de la curva?
- ¿Predomina un problema de bomba, de precarga o de resistencias?
- ¿Hay edema pulmonar hidrostático o lesión alveolar con agua pulmonar aumentada?

No sustituye la exploración ni la ecografía a pie de cama; añade información cuando está indicada y siempre que la calidad de la señal sea verificable.

### Conceptos y fórmulas

| Parámetro | Qué representa | Fórmula / nota |
|---|---|---|
| GC (CO) | Volumen expulsado por minuto | GC = FC × VS |
| IC (CI) | GC indexado a superficie corporal | IC = GC / SC |
| VS (SV) | Volumen sistólico | VS = GC / FC |
| SVV | Variación del volumen sistólico con la ventilación | Requiere ritmo sinusal, ventilación controlada y ausencia de respiración espontánea significativa |
| PPV | Variación de la presión de pulso | Mismas condiciones que SVV |
| RVS (SVR) | Resistencias vasculares sistémicas | RVS = (PAM − PVC) × 80 / GC |
| IRVS | RVS indexadas | IRVS = RVS × SC |
| GEDI / ITBVI | Volumen telediastólico global indexado | Estimación volumétrica por termodilución |
| EVLWI / ELWI | Agua pulmonar extravascular indexada | Marcador de edema pulmonar; interpretar con clínica |
| PVPI | Índice de permeabilidad vascular pulmonar | Orienta el mecanismo del edema |
| ScvO₂ / SvO₂ | Saturación venosa de oxígeno | Balance entre aporte y consumo |

**Límite común:** ningún valor aislado diagnostica. La tendencia, la coherencia con la exploración y la respuesta a una intervención valen más que una cifra puntual.

---

## 2. Edwards: FloTrac / Vigileo y VolumeView

### 2.1 Qué es

- **FloTrac/Vigileo:** estima el gasto cardíaco de forma continua a partir del contorno de la onda arterial, sin calibración externa. Utiliza datos demográficos del paciente y el análisis de la morfología de la presión.
- **VolumeView:** añade termodilución transpulmonar y parámetros volumétricos (GEDI, EVLWI, PVPI) usando un catéter arterial específico con termistor.
- **PreSep:** estimación continua de ScvO₂ mediante un catéter venoso central específico, si el sistema y el catéter están disponibles.

### 2.2 Indicaciones orientativas

- Shock o inestabilidad hemodinámica con necesidad de valorar GC y respuesta a volumen.
- Perioperatorio de cirugía mayor y pacientes críticos con línea arterial.
- Seguimiento de la respuesta a fluidos, inotrópicos o vasopresores cuando existe una pregunta clínica concreta.

### 2.3 Qué necesita

| Configuración | Acceso arterial | Acceso venoso | Material |
|---|---|---|---|
| FloTrac | Catéter arterial estándar (radial o femoral) | No imprescindible | Transductor, cable de presión, cable de datos, monitor compatible |
| VolumeView | Catéter arterial específico con termistor (habitualmente femoral) | Sí, central | Además: sensor de temperatura y material de termodilución |
| PreSep | Línea arterial si se combina con GC | Catéter venoso central específico | Monitor y cable correspondientes |

La PVC aislada no es un requisito para FloTrac ni un estimador fiable de respuesta a volumen.

### 2.4 Montaje básico de líneas y cables

1. Canalizar la arteria con técnica aséptica y conectar el transductor de presión.
2. Purgar el sistema, comprobar que no hay burbujas y verificar la onda con un *fast-flush*.
3. Nivelar el transductor en el eje flebostático (línea axilar media) y ponerlo a cero.
4. Conectar el cable de presión al monitor y el cable de datos del sistema Edwards.
5. Introducir peso, talla, edad y sexo; comprobar la configuración del modo (FloTrac o VolumeView).
6. Verificar la calidad de la onda y la coherencia del GC con la clínica antes de usar los valores.
7. VolumeView: comprobar el catéter con termistor y el acceso venoso central, y realizar las inyecciones térmicas según el manual del equipo.
8. Registrar el montaje, la hora, la calibración y los valores basales.

### 2.5 Interpretación y límites

- El contorno de pulso pierde fiabilidad con arritmias, bomba de balón, flujo pulsátil bajo, cambios bruscos de resistencias o mala perfusión periférica.
- En FloTrac, la recalibración automática no elimina el error en situaciones de vasoplejía extrema o cambios rápidos de tono vascular.
- SVV/PPV solo orientan respuesta a volumen en condiciones de ventilación controlada, ritmo sinusal y ausencia de respiración espontánea relevante.
- VolumeView aporta volúmenes, pero la termodilución requiere inyecciones correctas y un catéter bien posicionado.

---

## 3. MostCare (Vygon)

### 3.1 Qué es

Monitor basado en el análisis de la onda de presión arterial (método PRAM, *Pressure Recording Analytical Method*). Estima el gasto cardíaco latido a latido sin calibración externa ni termodilución.

### 3.2 Indicaciones orientativas

- Monitorización hemodinámica mínimamente invasiva en shock, sepsis, perioperatorio y UCI.
- Optimización de volumen y valoración de la contractilidad cuando ya existe una línea arterial.

### 3.3 Qué necesita

- Catéter arterial estándar (radial o femoral).
- Transductor de presión y cable de presión.
- Monitor MostCare compatible y cable de conexión.
- No precisa catéter arterial específico ni acceso venoso central para el cálculo.

### 3.4 Montaje básico

1. Canalizar la arteria y conectar el transductor.
2. Purgar y comprobar la onda con *fast-flush*.
3. Nivelar y poner a cero en el eje flebostático.
4. Conectar la señal de presión al MostCare e introducir los datos del paciente.
5. Verificar la calidad de la onda y la coherencia de los valores antes de interpretarlos.

### 3.5 Límites

Puede verse afectado por arritmias, bomba de balón, amortiguamiento de la línea, hipotermia o flujo no pulsátil. No sustituye la valoración clínica ni la medición directa cuando esta está indicada.

---

## 4. PiCCO (Getinge)

### 4.1 Qué es

Combina termodilución transpulmonar con análisis del contorno de pulso calibrado. Permite medir GC/IC y parámetros volumétricos (GEDI/ITBVI, EVLWI/ELWI, PVPI).

### 4.2 Indicaciones orientativas

- Shock complejo, sepsis, SDRA o inestabilidad que requiera valorar precarga, agua pulmonar y respuesta a volumen.
- Cuando se dispone de los accesos adecuados y de personal entrenado.

### 4.3 Qué necesita

- Catéter arterial específico con termistor, habitualmente femoral.
- Acceso venoso central para la inyección térmica.
- Monitor PiCCO compatible, transductores, cable de presión y sensor de temperatura.

### 4.4 Montaje básico

1. Comprobar el catéter arterial con termistor y el acceso venoso central.
2. Purgar y conectar los transductores.
3. Nivelar y poner a cero; verificar la onda arterial y la temperatura.
4. Conectar los cables al monitor e introducir los datos del paciente.
5. Realizar las inyecciones térmicas según el manual y comprobar la coherencia de los valores.

### 4.5 Límites

Requiere accesos específicos y calibración; no es un sistema sin calibración. Los valores pueden variar con arritmias, fugas, inyecciones incorrectas o cambios bruscos de temperatura.

---

## 5. Swan-Ganz (catéter de arteria pulmonar)

### 5.1 Qué es

Catéter flotante con termistor que mide presiones derechas (AD, VD, AP), presión de oclusión (PCP) y gasto cardíaco por termodilución. Algunos modelos permiten GC continuo y SvO₂.

### 5.2 Indicaciones orientativas

- Shock de causa no aclarada.
- Hipertensión pulmonar, fracaso ventricular derecho, evaluación pretrasplante o dispositivos de asistencia.
- Cuando la información no se puede obtener de forma fiable con métodos menos invasivos.

No es un monitor de uso rutinario.

### 5.3 Qué necesita

- Acceso venoso central con introductor.
- Catéter Swan-Ganz y monitor compatible.
- Transductores de presión, bolsa de purga presurizada y material de termodilución.

### 5.4 Montaje básico

1. Canalizar el acceso venoso central y colocar el introductor según técnica.
2. Conectar los transductores, purgar y poner a cero antes de avanzar el catéter.
3. Avanzar el catéter guiado por las curvas de presión hasta la arteria pulmonar; inflar el balón solo lo indicado.
4. Comprobar PCP, GC y SvO₂ según protocolo y registrar la posición.

### 5.5 Límites y riesgos

Arritmias, perforación, infección, trombosis, malposición e interpretación errónea de la PCP. Solo personal entrenado y con indicación clara.

---

## 6. Comprobaciones comunes a todos los sistemas

### 6.1 Calidad de la onda arterial

- **Fast-flush:** la onda debe recuperarse en 1–2 latidos, sin sobreoscilación ni amortiguamiento excesivo.
- **Nivelación:** transductor en el eje flebostático; recalibrar tras cambios de posición relevantes.
- **Cero:** comprobar antes de iniciar y tras manipulaciones del sistema.
- **Burbujas y acodaduras:** purgar y revisar el circuito.

### 6.2 Condiciones que invalidan SVV/PPV

- Arritmia (fibrilación auricular, extrasístoles frecuentes).
- Ventilación espontánea significativa o esfuerzo inspiratorio.
- Volumen tidal bajo, frecuencia muy alta o pulmón abierto.
- Bomba de balón intraaórtico o asistencia circulatoria.
- Presión intraabdominal muy elevada.

### 6.3 Asepsia y seguridad

- Técnica aséptica en la inserción y en cada manipulación.
- Fijación segura, apósito transparente y vigilancia del punto de inserción.
- Registro de accesos, fecha, calibraciones y complicaciones.
- Retirada precoz cuando la información deja de cambiar la actuación.

---

## 7. Evidencia y referencias

- Evans L, et al. **Surviving Sepsis Campaign: International Guidelines for Management of Sepsis and Septic Shock 2021.** *Intensive Care Med.* 2021.
- Cecconi M, et al. **Consensus on circulatory shock and hemodynamic monitoring.** *Intensive Care Med.* 2014.
- Monnet X, Marik PE, Teboul JL. **Prediction of fluid responsiveness: an update.** *Ann Intensive Care.* 2016.
- Marik PE, Cavallazzi R. **Does the central venous pressure predict fluid responsiveness?** *Crit Care Med.* 2013.
- Teboul JL, et al. **Less invasive hemodynamic monitoring in critically ill patients.** *Intensive Care Med.* 2016.
- Harvey S, et al. **PAC-Man trial: pulmonary artery catheters in general intensive care.** *Lancet.* 2005.
- Hadian M, Pinsky MR. **Evidence-based review of the use of the pulmonary artery catheter.** *Crit Care Clin.* 2007.
- Romano SM, et al. **PRAM: pressure recording analytical method.** *Minerva Anestesiol.* (revisión del método y validaciones posteriores).
- Scolletta S, et al. **Comparison of arterial pressure waveform analysis (MostCare) with thermodilution.** Estudios de validación del método PRAM.
- Goedje O, et al. **Transpulmonary thermodilution (PiCCO).** *Intensive Care Med.* 1999 y validaciones posteriores.
- Slagt C, et al. **Meta-analysis of FloTrac/Vigileo.** *Br J Anaesth.* 2014.
- Humbert M, et al. **2022 ESC/ERS Guidelines for the diagnosis and treatment of pulmonary hypertension.** *Eur Heart J.* 2022.

> Las referencias se citan como apoyo docente. Los umbrales y las indicaciones concretas deben adaptarse a la versión del equipo, a la población y al protocolo local.

---

## 8. Correspondencia con la app

| Pantalla / campo | Contenido de este documento |
|---|---|
| Monitorización → Hemodinámica avanzada | Parámetros de GC/IC, RVS/IRVS, PPV/SVV, precarga y contractilidad |
| Pestaña Edwards | FloTrac, VolumeView, PreSep, accesos y montaje |
| Pestaña MostCare | PRAM, línea arterial estándar y montaje |
| Pestaña PiCCO | Termodilución, volúmenes y calibración |
| Pestaña Swan-Ganz | Presiones derechas, PCP, GC y riesgos |
| Valoración integral | Solo los campos que existen en la valoración; el resto queda en el módulo |

**Privacidad:** las fotografías de monitores se procesan en el dispositivo y se borran tras la lectura; no se adjuntan a la historia ni se envían a servidores.
