# Temas de capstone explorados con WBGAPI

Este artefacto reúne **seis temas de proyecto** que pueden formularse como **Carta Proyecto / anteproyecto MIAD** usando datos públicos del Banco Mundial consultados vía **WBGAPI**. Para cada tema se creó una carpeta con:

- una **muestra de datos** (`muestra_panel.csv`),
- un **inventario de indicadores** (`indicadores_seleccionados.csv`),
- y un **README** con el problema de negocio, la lectura de factibilidad y un ejemplo corto en Python.

## Cómo se evaluó la factibilidad

La factibilidad se estimó con una muestra homogénea de **10 países de América Latina** (`ARG`, `BOL`, `BRA`, `CHL`, `COL`, `DOM`, `ECU`, `GTM`, `MEX`, `PER`) y la ventana **2012-2023**. Se revisó:

1. **Cobertura promedio del panel** por tema.
2. **Cobertura del indicador más débil** dentro de cada set.
3. **Último año** en que el tema mantiene al menos **80% de cobertura promedio**.

> Lectura práctica: un tema con factibilidad **Alta** permite formular bien el anteproyecto y montar un MVP con WBGAPI casi sin fuentes adicionales. Un tema **Media** sigue sirviendo para la Carta Proyecto, pero conviene acotar el caso o complementar datos.

## Resumen de temas

| Tema | Sector | Factibilidad | Cobertura promedio | Último año útil | Carpeta |
|---|---|---|---:|---:|---|
| Priorización de inversión en acceso a energía y cocina limpia | Energía / Sector público / Desarrollo | Alta | 97.2% | 2023 | `01_acceso_energia_limpia` |
| Alerta temprana de deterioro macroeconómico | Financiero / Gobierno / Riesgo soberano | Media | 88.2% | 2023 | `02_alerta_riesgo_macroeconomico` |
| Priorización de intervenciones para reducir mortalidad infantil | Salud / Sector público / Desarrollo social | Alta | 98.1% | 2023 | `03_mortalidad_infantil` |
| Monitoreo de rezago educativo y riesgo de bajo desempeño estructural | Educación / Gobierno | Media | 87.4% | 2020 | `04_rezago_educativo` |
| Índice de preparación para la transición energética | Energía / Sostenibilidad / Inversión pública | Media-Alta | 92.4% | 2021 | `05_transicion_energetica` |
| Determinantes de la participación laboral femenina | Mercado laboral / Gobierno / Equidad de género | Alta | 97.5% | 2023 | `06_participacion_laboral_femenina` |

## Recomendación ejecutiva

Los temas **más sólidos** para avanzar al anteproyecto usando solo datos del Banco Mundial son:

1. **Priorización de inversión en acceso a energía y cocina limpia**
2. **Priorización de intervenciones para reducir mortalidad infantil**
3. **Determinantes de la participación laboral femenina**

Los temas **viables pero con más cuidado de alcance** son:

- **Alerta temprana de deterioro macroeconómico**, porque el indicador de deuda pública tiene cobertura desigual en la muestra.
- **Monitoreo de rezago educativo**, porque algunos proxys de capacidad docente tienen huecos y el último año bien cubierto cae antes.
- **Índice de preparación para la transición energética**, porque funciona mejor como benchmarking histórico que como monitoreo casi en tiempo real.

## Estructura creada

- `01_acceso_energia_limpia/`
- `02_alerta_riesgo_macroeconomico/`
- `03_mortalidad_infantil/`
- `04_rezago_educativo/`
- `05_transicion_energetica/`
- `06_participacion_laboral_femenina/`
