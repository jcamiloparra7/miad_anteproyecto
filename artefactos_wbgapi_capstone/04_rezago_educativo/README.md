# Monitoreo de rezago educativo y riesgo de bajo desempeño estructural

**Sector sugerido:** Educación / Gobierno

**Stakeholder plausible:** Ministerio de Educación, secretaría de planeación educativa o fundación enfocada en permanencia escolar.

## Problema de negocio

Las autoridades necesitan detectar contextos con riesgo persistente de rezago educativo para orientar acompañamiento, conectividad y gasto, pero la información suele estar fragmentada.

## Decisión que apoyaría el proyecto

Clasificar países o territorios en niveles de riesgo educativo para orientar intervenciones y seguimiento.

## Enfoque analítico sugerido

Segmentación, modelos de riesgo y tableros de alerta sobre culminación y acceso.

## Indicadores WBGAPI seleccionados

| Código | Indicador | Uso en el problema de negocio | Completitud | Último año con >=80% cobertura |
|---|---|---|---:|---:|
| SE.SEC.CMPT.LO.ZS | Lower secondary completion rate, total (% of relevant age group) | Resultado clave de permanencia/culminación. | 85.0% | 2022 |
| SE.SEC.ENRR | School enrollment, secondary (% gross) | Acceso y cobertura en secundaria. | 98.3% | 2023 |
| SE.PRM.ENRL.TC.ZS | Pupil-teacher ratio, primary | Proxy de capacidad docente del sistema. | 48.3% | 2017 |
| IT.NET.USER.ZS | Individuals using the Internet (% of population) | Acceso digital como habilitador del aprendizaje. | 100.0% | 2023 |
| SE.XPD.TOTL.GD.ZS | Government expenditure on education, total (% of GDP) | Esfuerzo público en educación. | 92.5% | 2022 |
| NY.GDP.PCAP.CD | GDP per capita (current US$) | Contexto socioeconómico para segmentación. | 100.0% | 2023 |

## Archivos de esta carpeta

- `muestra_panel.csv`: panel de muestra con 10 países de América Latina entre 2012 y 2023.
- `indicadores_seleccionados.csv`: inventario de indicadores, propósito de negocio y cobertura observada en la muestra.

## Factibilidad con datos del Banco Mundial

- **Factibilidad general:** Media
- **Cobertura promedio del panel:** 87.4%
- **Indicador con menor cobertura:** 48.3%
- **Último año con al menos 80% de cobertura promedio:** 2020
- **Conclusión:** Tema útil para la carta proyecto, pero el MVP debería diseñarse con una pregunta más acotada o con una fuente complementaria.

## Limitaciones principales

La principal limitación del set en WBGAPI es la cobertura de SE.PRM.ENRL.TC.ZS, por lo que conviene prever una fuente complementaria o ajustar el alcance temporal.

## Métrica de negocio / impacto esperado

Detectar con anticipación contextos rezagados y apoyar una asignación más focalizada del acompañamiento institucional.

## Código mínimo en Python para leer la muestra desde WBGAPI

```python
import wbgapi as wb
import pandas as pd

indicators = [
    'SE.SEC.CMPT.LO.ZS',
    'SE.SEC.ENRR',
    'SE.PRM.ENRL.TC.ZS',
    'IT.NET.USER.ZS',
    'SE.XPD.TOTL.GD.ZS',
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
