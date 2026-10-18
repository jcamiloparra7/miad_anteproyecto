# Priorización de inversión en acceso a energía y cocina limpia

**Sector sugerido:** Energía / Sector público / Desarrollo

**Stakeholder plausible:** Ministerio de Minas o Energía, agencia de planeación, banca de desarrollo o programa de electrificación rural.

## Problema de negocio

La entidad necesita priorizar territorios o países comparables para focalizar inversión en electrificación y adopción de tecnologías limpias de cocción, pero hoy la decisión puede depender de criterios dispersos y poca evidencia homogénea.

## Decisión que apoyaría el proyecto

Construir un ranking o score de priorización para asignar recursos a territorios con mayor brecha de acceso y mayor factibilidad de intervención.

## Enfoque analítico sugerido

Segmentación de países/territorios, scoring multicriterio y pronóstico básico de cierre de brechas.

## Indicadores WBGAPI seleccionados

| Código | Indicador | Uso en el problema de negocio | Completitud | Último año con >=80% cobertura |
|---|---|---|---:|---:|
| EG.ELC.ACCS.ZS | Access to electricity (% of population) | Cobertura base del servicio eléctrico. | 100.0% | 2023 |
| EG.CFT.ACCS.ZS | Access to clean fuels and technologies for cooking (% of population) | Acceso a tecnologías limpias de cocción; aproxima pobreza energética doméstica. | 100.0% | 2023 |
| EG.ELC.ACCS.RU.ZS | Access to electricity, rural (% of rural population) | Permite aislar la brecha rural, crítica para focalización. | 100.0% | 2023 |
| SP.RUR.TOTL.ZS | Rural population (% of total population) | Contexto demográfico de ruralidad. | 100.0% | 2023 |
| NY.GDP.PCAP.CD | GDP per capita (current US$) | Proxy de capacidad económica y asequibilidad. | 100.0% | 2023 |
| EG.FEC.RNEW.ZS | Renewable energy consumption (% of total final energy consumption) | Complementa la viabilidad desde la matriz energética y sostenibilidad. | 83.3% | 2021 |

## Archivos de esta carpeta

- `muestra_panel.csv`: panel de muestra con 10 países de América Latina entre 2012 y 2023.
- `indicadores_seleccionados.csv`: inventario de indicadores, propósito de negocio y cobertura observada en la muestra.

## Factibilidad con datos del Banco Mundial

- **Factibilidad general:** Alta
- **Cobertura promedio del panel:** 97.2%
- **Indicador con menor cobertura:** 83.3%
- **Último año con al menos 80% de cobertura promedio:** 2023
- **Conclusión:** Tema fuerte para la carta proyecto y para un MVP del capstone usando solo WBGAPI.

## Limitaciones principales

La cobertura es suficientemente alta para formular el anteproyecto y construir un MVP analítico con datos públicos del Banco Mundial.

## Métrica de negocio / impacto esperado

Reducir la brecha de acceso en los territorios priorizados y mejorar la trazabilidad de la asignación de inversión.

## Código mínimo en Python para leer la muestra desde WBGAPI

```python
import wbgapi as wb
import pandas as pd

indicators = [
    'EG.ELC.ACCS.ZS',
    'EG.CFT.ACCS.ZS',
    'EG.ELC.ACCS.RU.ZS',
    'SP.RUR.TOTL.ZS',
    'NY.GDP.PCAP.CD',
    'EG.FEC.RNEW.ZS'
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
