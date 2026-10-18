# Índice de preparación para la transición energética

**Sector sugerido:** Energía / Sostenibilidad / Inversión pública

**Stakeholder plausible:** Regulador, ministerio de energía, fondo de inversión sostenible o agencia de transición energética.

## Problema de negocio

No existe una herramienta simple y comparable para priorizar dónde la transición energética es más urgente y al mismo tiempo más viable.

## Decisión que apoyaría el proyecto

Construir un índice de readiness para priorizar cooperación técnica, inversión o acompañamiento regulatorio.

## Enfoque analítico sugerido

Índice compuesto, clustering y benchmarking internacional.

## Indicadores WBGAPI seleccionados

| Código | Indicador | Uso en el problema de negocio | Completitud | Último año con >=80% cobertura |
|---|---|---|---:|---:|
| EG.FEC.RNEW.ZS | Renewable energy consumption (% of total final energy consumption) | Participación renovable en consumo final. | 83.3% | 2021 |
| EN.GHG.CO2.PC.CE.AR5 | Carbon dioxide (CO2) emissions excluding LULUCF per capita (t CO2e/capita) | Huella per cápita de CO2 asociada a la estructura energética. | 100.0% | 2023 |
| EG.EGY.PRIM.PP.KD | Energy intensity level of primary energy (MJ/$2021 PPP GDP) | Eficiencia energética agregada. | 87.5% | 2021 |
| EG.ELC.RNEW.ZS | Renewable electricity output (% of total electricity output) | Participación renovable en la generación eléctrica. | 83.3% | 2021 |
| EG.USE.PCAP.KG.OE | Energy use (kg of oil equivalent per capita) | Intensidad de uso energético por habitante. | 100.0% | 2023 |
| NY.GDP.PCAP.CD | GDP per capita (current US$) | Capacidad económica para financiar transición. | 100.0% | 2023 |

## Archivos de esta carpeta

- `muestra_panel.csv`: panel de muestra con 10 países de América Latina entre 2012 y 2023.
- `indicadores_seleccionados.csv`: inventario de indicadores, propósito de negocio y cobertura observada en la muestra.

## Factibilidad con datos del Banco Mundial

- **Factibilidad general:** Media-Alta
- **Cobertura promedio del panel:** 92.4%
- **Indicador con menor cobertura:** 83.3%
- **Último año con al menos 80% de cobertura promedio:** 2021
- **Conclusión:** Tema viable para el capstone; probablemente requiera afinar la ventana temporal o complementar uno o dos indicadores.

## Limitaciones principales

La cobertura es utilizable, pero la última ventana con al menos 80% de cobertura promedio llega hasta 2021; conviene diseñar el caso como benchmarking/seguimiento histórico y no como monitoreo casi en tiempo real.

## Métrica de negocio / impacto esperado

Priorizar mejor la asistencia e inversión para acelerar transición con criterios comparables y transparentes.

## Código mínimo en Python para leer la muestra desde WBGAPI

```python
import wbgapi as wb
import pandas as pd

indicators = [
    'EG.FEC.RNEW.ZS',
    'EN.GHG.CO2.PC.CE.AR5',
    'EG.EGY.PRIM.PP.KD',
    'EG.ELC.RNEW.ZS',
    'EG.USE.PCAP.KG.OE',
    'NY.GDP.PCAP.CD'
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
