# Alerta temprana de deterioro macroeconómico

**Sector sugerido:** Financiero / Gobierno / Riesgo soberano

**Stakeholder plausible:** Banco de desarrollo, ministerio de hacienda, unidad de estudios económicos o comité de riesgo país.

## Problema de negocio

Las decisiones de seguimiento y exposición país pueden reaccionar tarde cuando no existe una señal analítica integrada de estrés macroeconómico.

## Decisión que apoyaría el proyecto

Generar una alerta o semáforo de riesgo para priorizar monitoreo, revisión de cupos o análisis más profundo por país.

## Enfoque analítico sugerido

Índice compuesto de estabilidad, clustering y modelos de clasificación/forecasting para señales tempranas.

## Indicadores WBGAPI seleccionados

| Código | Indicador | Uso en el problema de negocio | Completitud | Último año con >=80% cobertura |
|---|---|---|---:|---:|
| NY.GDP.MKTP.KD.ZG | GDP growth (annual %) | Captura desaceleración o contracción económica. | 100.0% | 2023 |
| FP.CPI.TOTL.ZG | Inflation, consumer prices (annual %) | Mide presión inflacionaria y pérdida de estabilidad de precios. | 95.0% | 2023 |
| GC.DOD.TOTL.GD.ZS | Central government debt, total (% of GDP) | Proxy de espacio fiscal y sostenibilidad de deuda. | 34.2% |  |
| BN.CAB.XOKA.GD.ZS | Current account balance (% of GDP) | Resume desequilibrios externos. | 100.0% | 2023 |
| FI.RES.TOTL.CD | Total reserves (includes gold, current US$) | Señal de colchón externo para enfrentar choques. | 100.0% | 2023 |
| SL.UEM.TOTL.ZS | Unemployment, total (% of total labor force) (modeled ILO estimate) | Mide deterioro del mercado laboral. | 100.0% | 2023 |

## Archivos de esta carpeta

- `muestra_panel.csv`: panel de muestra con 10 países de América Latina entre 2012 y 2023.
- `indicadores_seleccionados.csv`: inventario de indicadores, propósito de negocio y cobertura observada en la muestra.

## Factibilidad con datos del Banco Mundial

- **Factibilidad general:** Media
- **Cobertura promedio del panel:** 88.2%
- **Indicador con menor cobertura:** 34.2%
- **Último año con al menos 80% de cobertura promedio:** 2023
- **Conclusión:** Tema útil para la carta proyecto, pero el MVP debería diseñarse con una pregunta más acotada o con una fuente complementaria.

## Limitaciones principales

La principal limitación del set en WBGAPI es la cobertura de GC.DOD.TOTL.GD.ZS, por lo que conviene prever una fuente complementaria o ajustar el alcance temporal.

## Métrica de negocio / impacto esperado

Incrementar la anticipación del monitoreo de países con deterioro macro y reducir decisiones reactivas.

## Código mínimo en Python para leer la muestra desde WBGAPI

```python
import wbgapi as wb
import pandas as pd

indicators = [
    'NY.GDP.MKTP.KD.ZG',
    'FP.CPI.TOTL.ZG',
    'GC.DOD.TOTL.GD.ZS',
    'BN.CAB.XOKA.GD.ZS',
    'FI.RES.TOTL.CD',
    'SL.UEM.TOTL.ZS'
]

df = wb.data.DataFrame(
    indicators,
    economy=['ARG', 'BOL', 'BRA', 'CHL', 'COL', 'DOM', 'ECU', 'GTM', 'MEX', 'PER'],
    time=range(2012, 2024),
    labels=True,
    columns='series'
).reset_index(drop=True)

df.rename(columns={'Country': 'country', 'Time': 'year'}).to_csv('muestra_panel.csv', index=False)
print(df.head())
```
