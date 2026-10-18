# Determinantes de la participación laboral femenina

**Sector sugerido:** Mercado laboral / Gobierno / Equidad de género

**Stakeholder plausible:** Ministerio de Trabajo, consejería de equidad, centro de estudios laborales o programa de empleabilidad femenina.

## Problema de negocio

Las políticas de empleabilidad femenina suelen diseñarse sin una priorización clara de los factores estructurales asociados a baja participación laboral.

## Decisión que apoyaría el proyecto

Priorizar segmentos o países y orientar políticas sobre permanencia educativa, cuidados o inclusión digital.

## Enfoque analítico sugerido

Modelado explicativo, segmentación y estimación de elasticidades sobre participación laboral femenina.

## Indicadores WBGAPI seleccionados

| Código | Indicador | Uso en el problema de negocio | Completitud | Último año con >=80% cobertura |
|---|---|---|---:|---:|
| SL.TLF.CACT.FE.ZS | Labor force participation rate, female (% of female population ages 15+) (modeled ILO estimate) | Variable objetivo del caso. | 100.0% | 2023 |
| SL.UEM.TOTL.FE.ZS | Unemployment, female (% of female labor force) (modeled ILO estimate) | Condición de inserción laboral femenina. | 100.0% | 2023 |
| SP.DYN.TFRT.IN | Fertility rate, total (births per woman) | Proxy de presiones de cuidado y fecundidad. | 100.0% | 2023 |
| SE.SEC.CMPT.LO.FE.ZS | Lower secondary completion rate, female (% of relevant age group) | Capital humano femenino acumulado. | 85.0% | 2022 |
| IT.NET.USER.ZS | Individuals using the Internet (% of population) | Inclusión digital como habilitador de acceso al empleo. | 100.0% | 2023 |
| SP.POP.1564.TO.ZS | Population ages 15-64 (% of total population) | Tamaño relativo de la población en edad de trabajar. | 100.0% | 2023 |

## Archivos de esta carpeta

- `muestra_panel.csv`: panel de muestra con 10 países de América Latina entre 2012 y 2023.
- `indicadores_seleccionados.csv`: inventario de indicadores, propósito de negocio y cobertura observada en la muestra.

## Factibilidad con datos del Banco Mundial

- **Factibilidad general:** Alta
- **Cobertura promedio del panel:** 97.5%
- **Indicador con menor cobertura:** 85.0%
- **Último año con al menos 80% de cobertura promedio:** 2023
- **Conclusión:** Tema fuerte para la carta proyecto y para un MVP del capstone usando solo WBGAPI.

## Limitaciones principales

La cobertura es suficientemente alta para formular el anteproyecto y construir un MVP analítico con datos públicos del Banco Mundial.

## Métrica de negocio / impacto esperado

Explicar mejor los determinantes de baja participación y mejorar la focalización de políticas laborales y de formación.

## Código mínimo en Python para leer la muestra desde WBGAPI

```python
import wbgapi as wb
import pandas as pd

indicators = [
    'SL.TLF.CACT.FE.ZS',
    'SL.UEM.TOTL.FE.ZS',
    'SP.DYN.TFRT.IN',
    'SE.SEC.CMPT.LO.FE.ZS',
    'IT.NET.USER.ZS',
    'SP.POP.1564.TO.ZS'
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
