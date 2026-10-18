# CARTA PROYECTO

| | | | |
| :--- | :--- | :--- | :--- |
| **Título del Proyecto** | Sistema híbrido de alerta temprana de vulnerabilidad soberana externa y riesgo de distress | | |
| **Encargado del Proyecto** | Equipo capstone MIAD | **Asesor proyecto** | Por definir |
| **Fecha de Aprobación** | 2026-10-18 | **Última Revisión** | 2026-10-18 |

#### Necesidades de la Compañía

| | | |
| :--- | :--- | :--- |
| **Contexto** | El Banco Interamericano de Desarrollo (BID) opera en un entorno donde el monitoreo macroeconómico y soberano de países miembros es crítico para priorizar análisis, conversación con contrapartes y revisión de exposición. El seguimiento actual puede ser reactivo, heterogéneo entre equipos y poco trazable frente a episodios de presión externa. | |

#### Planteamiento del Problema

| | | |
| :--- | :--- | :--- |
| **Clientes / Stakeholders** | **Primario:** unidad de riesgo soberano / exposición país del BID. **Secundarios:** equipos país, comité de riesgo, tesorería y estrategia macro-financiera. | |

**Problema de negocio**  
La organización necesita una herramienta analítica que permita anticipar qué países presentan mayor vulnerabilidad soberana externa y mayor probabilidad de distress, para enfocar monitoreo intensivo, profundización del análisis y revisión de exposición de manera oportuna y consistente.

#### CTQ (Factores Críticos de Satisfacción)

1. **Oportunidad:** el resultado debe actualizarse con frecuencia y llegar antes del deterioro visible en comité.
2. **Interpretabilidad:** cada alerta debe mostrar qué variables explican el nivel de riesgo.
3. **Comparabilidad:** el score debe permitir comparar países y seguir su evolución.
4. **Cobertura:** la solución debe apoyarse en datos públicos con suficiente consistencia histórica.
5. **Accionabilidad:** el producto debe traducirse en una watchlist y un semáforo operativo.

#### Key Business Drivers (Variables del negocio)

- Exposición soberana y riesgo país.
- Capacidad analítica disponible para monitoreo.
- Oportunidad del escalamiento a comité.
- Vulnerabilidad de liquidez externa y refinanciamiento.
- Trazabilidad de decisiones de seguimiento y revisión.

---

### PROYECTO

| Objetivo del Proyecto | Diseñar una herramienta híbrida de alerta temprana que combine score estructural, clasificación supervisada y reglas de negocio para priorizar países con mayor vulnerabilidad soberana externa y riesgo de distress. | | | |
| :--- | :--- | :--- | :--- | :--- |
| **Métricas** | **Descripción** | **Valor Actual** | **Valor Objetivo** | |
| Captura temprana de eventos | % de eventos proxy contenidos en el 25% superior del ranking de riesgo | No medido | >= 70% | |
| Tiempo de actualización | Días hábiles para actualizar watchlist y semáforo | 20 días aprox. | <= 5 días | |
| Cobertura explicativa | % de países priorizados con drivers identificables y ficha analítica | 0% | 100% | |
| Consistencia del monitoreo | % de países revisados con criterios homogéneos | Bajo / no estandarizado | >= 90% | |

| Alcance del Proyecto | Construcción de un MVP anual para países del universo `lac14_debt`, benchmarking con `comp8`, y una capa mensual de seguimiento para países priorizados usando tipo de cambio y reservas. |
| :--- | :--- |

| Beneficios | |
| :--- | :--- |
| Operativos | Priorización objetiva del esfuerzo analítico y reducción de monitoreo reactivo. |
| Estratégicos | Mejor trazabilidad para revisión de exposición, diálogo con equipos país y preparación de comité. |
| Analíticos | Score comparable, clasificación de distress y seguimiento mensual de alertas. |

#### Planeación

| Actividades | Fechas | Nombre / Rol | Responsables Rev |
| :--- | :--- | :--- | :--- |
| **Definir** | Semanas 1-2 | Equipo capstone / líder de proyecto | Sponsor académico / stakeholder simulado |
| **Medir** | Semanas 3-4 | Científico de datos / analista económico | Líder técnico |
| **Analizar** | Semanas 5-7 | Científico de datos / modelador | Líder técnico y stakeholder |
| **Mejorar** | Semanas 8-10 | Equipo capstone | Comité de proyecto |
| **Controlar** | Semanas 11-12 | Equipo capstone / analista de negocio | Stakeholder y asesor |

| Restricciones | |
| :--- | :--- |
| Datos | No se incluyen precios de bonos, CDS ni spreads soberanos homogéneos, por lo que el proyecto no cubre pricing de mercado. |
| Etiquetas | Los eventos de distress proxy pueden ser escasos y desbalanceados. |
| Implementación | El stakeholder es simulado para fines académicos; las métricas actuales deberán validarse al contrastar con un usuario real. |
