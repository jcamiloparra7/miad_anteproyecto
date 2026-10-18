# Priorización de intervenciones para reducir mortalidad infantil

**Sector sugerido:** Salud / Sector público / Desarrollo social

**Stakeholder plausible:** Ministerio de Salud, secretaría de planeación social, ONG de salud pública u organismo multilateral.

## Problema de negocio

Los recursos de salud pública son limitados y la priorización de intervenciones preventivas no siempre usa una combinación consistente de riesgo sanitario y acceso a servicios básicos.

## Decisión que apoyaría el proyecto

Priorizar territorios o países para intervenciones preventivas y seguimiento reforzado.

## Enfoque analítico sugerido

Modelos explicativos y predictivos sobre mortalidad infantil/menor de 5 años, con segmentación de contextos sanitarios.

## Indicadores WBGAPI seleccionados

| Código | Indicador | Uso en el problema de negocio | Completitud | Último año con >=80% cobertura |
|---|---|---|---:|---:|
| SH.DYN.MORT | Mortality rate, under-5 (per 1,000 live births) | Variable objetivo central del problema. | 100.0% | 2023 |
| SH.IMM.MEAS | Immunization, measles (% of children ages 12-23 months) | Proxy de cobertura preventiva del sistema de salud. | 100.0% | 2023 |
| SH.XPD.CHEX.GD.ZS | Current health expenditure (% of GDP) | Esfuerzo financiero en salud. | 100.0% | 2023 |
| SH.STA.BASS.ZS | People using at least basic sanitation services (% of population) | Condiciones de saneamiento ligadas a enfermedad prevenible. | 94.2% | 2023 |
| SH.H2O.BASW.ZS | People using at least basic drinking water services (% of population) | Acceso a agua segura como determinante estructural. | 94.2% | 2023 |
| SN.ITK.DEFC.ZS | Prevalence of undernourishment (% of population) | Señal de vulnerabilidad nutricional. | 100.0% | 2023 |

## Archivos de esta carpeta

- `muestra_panel.csv`: panel de muestra con 10 países de América Latina entre 2012 y 2023.
- `indicadores_seleccionados.csv`: inventario de indicadores, propósito de negocio y cobertura observada en la muestra.

## Factibilidad con datos del Banco Mundial

- **Factibilidad general:** Alta
- **Cobertura promedio del panel:** 98.1%
- **Indicador con menor cobertura:** 94.2%
- **Último año con al menos 80% de cobertura promedio:** 2023
- **Conclusión:** Tema fuerte para la carta proyecto y para un MVP del capstone usando solo WBGAPI.

## Limitaciones principales

La cobertura es suficientemente alta para formular el anteproyecto y construir un MVP analítico con datos públicos del Banco Mundial.

## Métrica de negocio / impacto esperado

Mejorar la focalización de intervenciones y explicar qué variables anteceden mayores tasas de mortalidad.

## Código mínimo en Python para leer la muestra desde WBGAPI

```python
import wbgapi as wb
import pandas as pd

indicators = [
    'SH.DYN.MORT',
    'SH.IMM.MEAS',
    'SH.XPD.CHEX.GD.ZS',
    'SH.STA.BASS.ZS',
    'SH.H2O.BASW.ZS',
    'SN.ITK.DEFC.ZS'
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
