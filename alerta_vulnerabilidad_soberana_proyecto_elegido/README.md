# Alerta temprana de vulnerabilidad soberana externa

**Sector sugerido:** Financiero / Gobierno / Riesgo soberano

**Stakeholder principal recomendado:** **Banco Interamericano de Desarrollo (BID)**, específicamente una unidad de **riesgo soberano / exposición país / análisis macroeconómico regional**.

## Problema de negocio

Un banco multilateral que mantiene exposición soberana y opera con equipos país necesita decidir **qué países requieren monitoreo intensivo, escalamiento a comité o revisión de exposición**. Sin una señal analítica integrada, el seguimiento suele ser reactivo, heterogéneo entre analistas y tardío frente a episodios de estrés externo.

## Solución propuesta

Construir una **herramienta híbrida de alerta temprana** que combine:

1. **Capa no supervisada** para generar un score interpretable de vulnerabilidad soberana.
2. **Capa supervisada** para estimar la probabilidad de distress soberano proxy a 12 meses.
3. **Motor de decisión** para traducir ambas señales en un semáforo ampliado y una watchlist operativa.

## Objetivo del proyecto

Priorizar países emergentes con mayor vulnerabilidad soberana externa y mayor probabilidad de distress, con el fin de orientar monitoreo, revisión de exposición y profundización del análisis.

## Alcance recomendado

- **Universo principal:** `lac14_debt`, por su alta cobertura en variables de deuda externa y liquidez.
- **Comparadores externos:** `comp8`, para benchmarking frente a otros emergentes.
- **Ventana anual base:** 2012-2023.
- **Capa mensual de seguimiento:** países priorizados con `DPANUSLCU` y `TOTRESV`.

## Stakeholders sugeridos

| Tipo | Stakeholder | Rol esperado |
|---|---|---|
| Primario | Unidad de riesgo soberano / exposición país del BID | Usuario directo del ranking, semáforo y watchlist |
| Secundario | Equipos país del BID | Profundizar análisis económico de países en alerta |
| Secundario | Comité de riesgo / crédito | Usar señales para revisión de exposición o escalamiento |
| Secundario | Tesorería / estrategia | Coordinar decisiones de seguimiento macro-financiero |

## Fuentes de datos a usar

| Fuente | ID WBGAPI | Aporte al proyecto | Ejemplos |
|---|---:|---|---|
| World Development Indicators (WDI) | 2 | Núcleo macro, sector externo y liquidez | `NY.GDP.MKTP.KD.ZG`, `FP.CPI.TOTL.ZG`, `BN.CAB.XOKA.GD.ZS`, `FI.RES.TOTL.MO` |
| Worldwide Governance Indicators (WGI) | 3 | Capacidad institucional para gestionar choques | `GOV_WGI_GE.SC` |
| International Debt Statistics (IDS) | 6 / 81 | Carga de deuda, rollover, costo financiero y distress proxy | `DT.TDS.DECT.EX.ZS`, `DT.INT.DECT.EX.ZS`, `DT.DOD.DSTC.ZS`, `DT.AXA.DLXF.CD` |
| Global Economic Monitor (GEM) | 15 | Seguimiento mensual de presión cambiaria y reservas | `DPANUSLCU`, `TOTRESV` |

> El catálogo inicial propuesto quedó documentado en `catalogo_fuentes_indicadores.csv`.

## Métodos propuestos

| Módulo | Método | Propósito | Salida |
|---|---|---|---|
| Score estructural | PCA, normalización robusta, percentiles, clustering | Resumir vulnerabilidad externa y segmentar países | Score continuo y clusters |
| Clasificador de distress | Regresión logística regularizada y/o gradient boosting | Estimar `P(distress_{t+1})` | Probabilidad anual por país |
| Reglas de negocio | Umbrales sobre score, probabilidad y triggers mensuales | Traducir señales a decisiones operativas | Semáforo y watchlist |
| Seguimiento mensual | Reglas de variación de reservas y tipo de cambio | Confirmar deterioro reciente en países priorizados | Alertas mensuales |

## Etiquetas sugeridas del semáforo

- **Verde:** estabilidad relativa.
- **Amarillo:** vigilancia preventiva.
- **Naranja:** alerta preventiva.
- **Rojo:** alta vulnerabilidad / alta probabilidad de distress.
- **Negro:** distress observado o activación de evento proxy.

## Cómo se evaluaría la herramienta

### Validación no supervisada

- estabilidad de clusters en ventanas temporales;
- coherencia económica de los factores principales;
- concentración posterior de eventos proxy en clusters de mayor riesgo.

### Validación supervisada

- **PR-AUC** y **ROC-AUC**;
- **recall@top-k** del ranking de países;
- porcentaje de eventos capturados en el top 20%-30% del score final;
- validación temporal tipo **expanding window** para evitar leakage.

### Validación de negocio

- reducción del universo a monitorear sin perder demasiados eventos;
- disminución del tiempo de reacción analítica;
- trazabilidad de drivers para discusión en comité.

## Archivos de esta carpeta

- `ENTREGABLE_GUIA1_ANTEPROYECTO.md`: borrador del documento entregable de la guía.
- `CARTA_PROYECTO.md`: carta proyecto en formato cercano al solicitado por la guía.
- `catalogo_fuentes_indicadores.csv`: inventario inicial de fuentes e indicadores propuestos.

## Notas de alcance

- El proyecto **no** se presenta como modelo de *right pricing* de bonos soberanos, porque WBGAPI no aporta precios, yields ni spreads de mercado de manera homogénea.
- Sí se presenta como **herramienta de priorización de vulnerabilidad soberana externa**, con posible extensión futura a mispricing si luego se incorpora una fuente de mercado.
