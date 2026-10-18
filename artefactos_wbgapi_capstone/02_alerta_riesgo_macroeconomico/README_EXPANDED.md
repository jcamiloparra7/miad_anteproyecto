# Exploración ampliada del tema macroeconómico

Este complemento amplía el caso de **alerta temprana de deterioro macroeconómico** con tres decisiones de alcance:

1. **Ampliar el universo de países** para que el caso no quede limitado a 10 economías.
2. **Separar el modelo en capas de datos** según cobertura: núcleo anual, vulnerabilidad externa, profundidad financiera/fiscal y monitoreo mensual.
3. **Agregar comparadores fuera de América Latina** para benchmarking de riesgo macro.

## Recomendación de alcance

### Opción A: universo regional amplio para modelo anual base

- **Archivo:** `muestra_panel_lac20_anual.csv`
- **Universo:** 20 países de América Latina y el Caribe
- **Uso recomendado:** cuando quieras un modelo de clasificación/segmentación macro con buena diversidad regional y cobertura robusta del set base.

Países: `ARG, BOL, BRA, CHL, COL, CRI, DOM, ECU, GTM, HND, HTI, JAM, MEX, NIC, PAN, PER, PRY, SLV, URY, GUY`

### Opción B: universo robusto para variables de deuda externa

- **Archivo:** `muestra_panel_lac14_deuda.csv`
- **Universo:** 14 países con mejor cobertura para deuda externa y servicio de deuda
- **Uso recomendado:** si el problema de negocio enfatiza sostenibilidad externa o vulnerabilidad de balanza de pagos.

Países: `BLZ, BOL, BRA, COL, DOM, ECU, GTM, HND, HTI, MEX, NIC, PER, PRY, SLV`

### Opción C: comparadores emergentes internacionales

- **Archivo:** `muestra_panel_comparadores8_anual.csv`
- **Universo:** 8 economías emergentes extra-regionales
- **Uso recomendado:** para benchmarking y validación externa del score de riesgo.

Países: `EGY, IDN, MAR, PHL, THA, TUR, VNM, ZAF`

## Cobertura promedio por universo

| Universo | # países | Cobertura set core | Cobertura con capa externa | Cobertura full anual |
|---|---:|---:|---:|---:|
| lac20 | 20 | 99.0% | 94.7% | 88.7% |
| lac14_debt | 14 | 99.9% | 99.9% | 93.5% |
| comp8 | 8 | 99.8% | 99.8% | 93.7% |


> Lectura sugerida: usa el **set core** para un primer MVP estable; agrega la **capa externa** si el caso enfatiza crisis de balanza de pagos; agrega la **capa fiscal** solo si aceptas menor cobertura o un subuniverso más pequeño.

## Capas de datos recomendadas

### 1) Núcleo anual de monitoreo macro

Indicadores de alta utilidad y muy buena cobertura para el primer modelo:

- PIB real (`NY.GDP.MKTP.KD.ZG`)
- Inflación (`FP.CPI.TOTL.ZG`)
- Cuenta corriente / PIB (`BN.CAB.XOKA.GD.ZS`)
- Reservas (`FI.RES.TOTL.CD`)
- Desempleo (`SL.UEM.TOTL.ZS`)
- IED neta / PIB (`BX.KLT.DINV.WD.GD.ZS`)
- Dinero amplio / PIB (`FM.LBL.BMNY.GD.ZS`)
- Government effectiveness (`GOV_WGI_GE.SC`)

**Uso de negocio:** construir un semáforo de riesgo macro, clusterizar economías y explicar deterioros con variables reales, externas, financieras e institucionales.

### 2) Extensión de vulnerabilidad externa

- Exportaciones / PIB (`NE.EXP.GNFS.ZS`)
- Deuda externa / GNI (`DT.DOD.DECT.GN.ZS`)
- Servicio de deuda / exportaciones (`DT.TDS.DECT.EX.ZS`)

**Uso de negocio:** fortalecer el caso para entidades que vigilan exposición soberana, riesgo externo o capacidad de pago.

### 3) Extensión financiera/fiscal

- Crédito privado / PIB (`GFDD.DI.01`)
- Deuda del gobierno central / PIB (`GC.DOD.TOTL.GD.ZS`)

**Uso de negocio:** enriquecer un score integral, pero con la advertencia de que `GC.DOD.TOTL.GD.ZS` es la variable más restrictiva en cobertura.

### 4) Capa opcional de monitoreo mensual

- **Archivo:** `muestra_panel_mensual_gem.csv`
- **Fuente:** Global Economic Monitor (GEM)
- **Indicadores:**
  - Tipo de cambio oficial (`DPANUSLCU`)
  - Reservas totales (`TOTRESV`)
- **Cobertura observada en la muestra mensual:** ~99.5% para `BRA`, `CHL`, `COL`, `DOM`, `ECU`, `MEX`, `PER`, `PRY` entre 2019M01 y 2026M08.

**Uso de negocio:** pasar de un score anual de diagnóstico a una lógica de seguimiento mensual y alerta temprana operativa.

## Hallazgos clave

1. **Sí se puede ampliar el número de países** sin romper la factibilidad, pero conviene hacerlo por capas de cobertura y no con un único universo rígido.
2. **La deuda externa y el servicio de deuda sí son utilizables** en WBGAPI vía WDI; el indicador más problemático sigue siendo **deuda del gobierno central / PIB**.
3. **Agregar comparadores emergentes** mejora mucho la historia de negocio, porque permite responder no solo “quién está mal en la región”, sino “qué tan mal está frente a pares internacionales”.
4. **La capa mensual GEM** abre una versión más ejecutiva del proyecto: seguimiento cambiario y de reservas después de entrenar un score anual.

## Archivos creados

- `muestra_panel_lac20_anual.csv`
- `muestra_panel_lac14_deuda.csv`
- `muestra_panel_comparadores8_anual.csv`
- `muestra_panel_mensual_gem.csv`
- `catalogo_datasets_expandido.csv`
- `cobertura_paises_lac20.csv`
- `cobertura_paises_lac14_debt.csv`
- `cobertura_paises_comp8.csv`
- `resumen_universos.csv`

## Código mínimo en Python

```python
import wbgapi as wb
import pandas as pd

indicators = [
    'NY.GDP.MKTP.KD.ZG', 'FP.CPI.TOTL.ZG', 'BN.CAB.XOKA.GD.ZS',
    'FI.RES.TOTL.CD', 'SL.UEM.TOTL.ZS', 'BX.KLT.DINV.WD.GD.ZS',
    'FM.LBL.BMNY.GD.ZS', 'GOV_WGI_GE.SC', 'NE.EXP.GNFS.ZS',
    'DT.DOD.DECT.GN.ZS', 'DT.TDS.DECT.EX.ZS', 'GFDD.DI.01'
]

lac14_debt = ['BLZ','BOL','BRA','COL','DOM','ECU','GTM','HND','HTI','MEX','NIC','PER','PRY','SLV']

frames = []
for code in indicators:
    db = 3 if code.startswith('GOV_WGI') else 32 if code.startswith('GFDD') else 2
    frames.append(
        wb.data.DataFrame([code], db=db, economy=lac14_debt, time=range(2012, 2024), columns='series').reset_index()
    )

panel = frames[0]
for df in frames[1:]:
    panel = panel.merge(df, on=['economy', 'time'], how='outer')

print(panel.head())
```
