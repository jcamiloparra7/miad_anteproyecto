# Proyecto reforzado: alerta temprana de deterioro macroeconómico soberano

## Posicionamiento recomendado del proyecto

En lugar de formular el caso como “predicción de default”, el proyecto queda más sólido si se presenta como un **sistema de alerta temprana de vulnerabilidad macroeconómica y distress soberano** para apoyar decisiones de:

- priorización de monitoreo país,
- profundización de análisis económico,
- revisión de exposición o cupos,
- y focalización de asistencia técnica o financiera.

Esta formulación usa mejor la evidencia realmente disponible en WBGAPI y encaja mejor con una **Carta Proyecto** orientada a negocio.

## Definición operativa de deterioro macroeconómico

Para este proyecto, el **deterioro macroeconómico** no es una sola variable sino un estado de estrés observado en cuatro frentes:

1. **Actividad real y empleo:** bajo crecimiento, recesión o deterioro laboral.
2. **Estabilidad nominal y financiera:** inflación alta, condiciones monetarias restrictivas o menor profundidad financiera.
3. **Sector externo:** menor generación de divisas, presión sobre reservas y mayor carga de deuda externa.
4. **Distress de deuda:** aparición de atrasos, reprogramaciones o alivios sobre obligaciones externas.

Con esto el proyecto puede producir dos salidas:

- un **score continuo** de vulnerabilidad macro,
- y un **semáforo de distress** basado en proxies de tensión de deuda.

## Qué pasa cuando hay deterioro

Desde la lógica de negocio, el deterioro suele traducirse en:

- mayor incertidumbre sobre capacidad de pago,
- aumento de presión sobre reservas y financiamiento externo,
- menor espacio para sostener inversión y gasto,
- necesidad de monitoreo más frecuente,
- y mayor probabilidad de reestructuración o tensiones de servicio de deuda.

Eso vuelve accionable el caso para una entidad financiera pública, un organismo multilateral o un equipo de riesgo país.

## Variables que ya fortalecen el proyecto

### 1. Núcleo macro de alta cobertura

Estas variables ya mostraron buena cobertura en la exploración ampliada:

| Código | Variable | Rol en el caso |
|---|---|---|
| `NY.GDP.MKTP.KD.ZG` | GDP growth (annual %) | Señal principal de desaceleración o contracción |
| `FP.CPI.TOTL.ZG` | Inflation, consumer prices (annual %) | Estrés nominal y pérdida de estabilidad |
| `BN.CAB.XOKA.GD.ZS` | Current account balance (% of GDP) | Fragilidad externa |
| `FI.RES.TOTL.CD` | Total reserves | Colchón externo |
| `SL.UEM.TOTL.ZS` | Unemployment, total (%) | Transmisión del deterioro al mercado laboral |
| `BX.KLT.DINV.WD.GD.ZS` | FDI net inflows (% of GDP) | Calidad y disponibilidad de financiamiento externo |
| `FM.LBL.BMNY.GD.ZS` | Broad money (% of GDP) | Profundidad monetaria y liquidez |
| `GOV_WGI_GE.SC` | Government Effectiveness score | Capacidad institucional de respuesta |

### 2. Variables de deuda externa y costo financiero

Estas hacen que el caso deje de ser solo macro general y se acerque a riesgo soberano:

| Código | Variable | Uso |
|---|---|---|
| `DT.DOD.DECT.GN.ZS` | External debt stocks (% of GNI) | Carga agregada de deuda externa |
| `DT.TDS.DECT.EX.ZS` | Total debt service (% of exports) | Presión de pagos sobre divisas |
| `DT.INT.DECT.EX.ZS` | Interest payments on external debt (% of exports) | Carga de intereses externos |
| `DT.INT.DECT.GN.ZS` | Interest payments on external debt (% of GNI) | Presión de intereses sobre la economía |
| `DT.INR.DPPG` | Average interest on new external debt commitments (%) | Costo promedio de nueva deuda externa |

### 3. Proxies de distress / default operativo

No apareció una variable limpia de **default soberano** en WBGAPI, pero sí proxies valiosos para construir una etiqueta de tensión:

| Código | Variable | Interpretación |
|---|---|---|
| `DT.AXA.DLXF.CD` | Principal arrears, long-term DOD | Atrasos en principal |
| `DT.IXA.DLXF.CD` | Interest arrears, long-term DOD | Atrasos en intereses |
| `DT.IXR.DPPG.CD` | Interest rescheduled (capitalized) | Reprogramación / reestructuración |
| `DT.IXF.DPPG.CD` | Interest forgiven | Alivio o evento severo de distress |

Estas variables **no equivalen** a una base oficial de default, pero sí permiten construir una señal razonable de **distress soberano**.

### 4. Proxies de tasas de interés domésticas

No se encontró una tasa homogénea de política monetaria del banco central, pero sí proxys útiles:

| Código | Variable | Uso |
|---|---|---|
| `FR.INR.RINR` | Real interest rate (%) | Proxy de postura monetaria y condiciones financieras |
| `FR.INR.LEND` | Lending interest rate (%) | Costo del crédito doméstico |
| `FR.INR.DPST` | Deposit interest rate (%) | Remuneración del ahorro / condiciones bancarias |

### 5. Capa mensual opcional

Para pasar de diagnóstico anual a seguimiento operativo:

| Código | Variable | Uso |
|---|---|---|
| `DPANUSLCU` | Official exchange rate, LCU per USD | Presión cambiaria |
| `TOTRESV` | Total reserves | Seguimiento de liquidez externa |

## Universo recomendado

Con base en la exploración previa, el universo más sólido para el proyecto es:

### Universo principal: `lac14`

`BLZ, BOL, BRA, COL, DOM, ECU, GTM, HND, HTI, MEX, NIC, PER, PRY, SLV`

**Por qué conviene este universo:**

- conserva buena cobertura del núcleo macro,
- mantiene bien la capa de deuda externa,
- soporta mejor el caso de vulnerabilidad soberana,
- evita perder demasiada muestra por indicadores fiscales más débiles.

### Comparadores externos: `comp8`

`EGY, IDN, MAR, PHL, THA, TUR, VNM, ZAF`

Sirven para benchmarking y hacen más fuerte la historia de negocio: no solo comparas países entre sí en la región, sino frente a otros emergentes.

## Pregunta de negocio refinada

> ¿Cómo priorizar los países con mayor riesgo de deterioro macroeconómico y distress soberano en el corto y mediano plazo, para orientar monitoreo, profundización del análisis y decisiones de exposición o asistencia?

## Hipótesis del proyecto

1. Países con bajo crecimiento, alta inflación, mayor carga de servicio de deuda y menor colchón externo presentan mayor vulnerabilidad macro.
2. Los episodios de distress proxy aparecen con más frecuencia en contextos de deterioro externo y financiero.
3. Un score anual de vulnerabilidad puede anticipar países que después muestran señales de tensión en deuda, tipo de cambio o reservas.

## Formulación metodológica recomendada

### Opción 1: score de vulnerabilidad macro

Construir un índice compuesto con:

- normalización por percentiles o z-scores,
- ponderación experta o PCA,
- y segmentación de países por niveles de riesgo.

Es la vía más robusta para el capstone si quieres minimizar dependencia de etiquetas raras.

### Opción 2: clasificación de distress proxy

Definir una etiqueta de evento:

`distress_event = 1` si en un año se observa cualquiera de estos casos:

- `DT.AXA.DLXF.CD > 0`
- `DT.IXA.DLXF.CD > 0`
- `DT.IXR.DPPG.CD > 0`
- `DT.IXF.DPPG.CD > 0`

Eso permite un problema supervisado, pero con menor densidad de eventos.

### Opción 3: arquitectura en dos capas

1. **Modelo anual** para vulnerabilidad macro estructural.
2. **Monitoreo mensual** para países priorizados, usando tipo de cambio y reservas.

Esta es probablemente la formulación más fuerte para la carta proyecto porque conecta diagnóstico, seguimiento y decisión.

## Qué sí y qué no prometer

### Sí prometer

- priorización de riesgo macro país,
- score interpretable de vulnerabilidad,
- benchmarking regional e internacional,
- señal temprana de distress soberano con proxies observables.

### No prometer de entrada

- predicción exacta de default soberano formal,
- estimación causal fuerte de política monetaria con tasa de banco central homogénea,
- monitoreo en tiempo real completo de todo el universo.

## Factibilidad final

| Componente | Factibilidad |
|---|---|
| Score anual de vulnerabilidad macro | **Muy alta** |
| Inclusión de deuda externa y costo financiero | **Alta** |
| Clasificación de distress con proxies | **Media** |
| Predicción de default soberano formal solo con WBGAPI | **Media-baja** |

## Recomendación final de título

**Sistema de alerta temprana de vulnerabilidad macroeconómica y distress soberano para priorizar monitoreo y gestión de riesgo país en economías emergentes de América Latina**

## Recomendación final de alcance para la Carta Proyecto

Si quieres que el proyecto se vea serio, factible y alineado con la guía, el mejor encuadre es:

- **stakeholder:** banca de desarrollo / organismo multilateral / unidad de riesgo país,
- **problema:** monitoreo reactivo y disperso del deterioro macro,
- **objetivo:** anticipar y priorizar países con mayor vulnerabilidad,
- **métrica de negocio:** mejorar oportunidad y trazabilidad del monitoreo,
- **producto mínimo:** score anual + tablero de semáforo + capa mensual para países críticos.
