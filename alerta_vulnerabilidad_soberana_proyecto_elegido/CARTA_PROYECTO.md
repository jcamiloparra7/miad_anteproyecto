# CARTA DEL PROYECTO

| Campo | Información |
|---|---|
| **Título** | Sistema híbrido de alerta temprana de vulnerabilidad soberana externa y riesgo de distress |
| **Responsables** | Equipo de estudiantes MIAD |
| **Asesor** | Por definir |
| **Fecha de elaboración** | 18 de octubre de 2026 |
| **Estado** | Propuesta académica pendiente de aprobación |

## 1. Necesidades de la organización

**Contexto:** El Banco Interamericano de Desarrollo (BID) es una institución multilateral que financia proyectos y programas en América Latina y el Caribe. El seguimiento de las condiciones económicas y financieras de los países es relevante para evaluar su vulnerabilidad externa y los riesgos asociados con el cumplimiento de sus obligaciones de deuda.

## 2. Planteamiento del problema

**Stakeholder principal:** Equipos de análisis macroeconómico y riesgo soberano de una entidad multilateral como el BID.

**Stakeholders secundarios:** Equipos país, áreas de gestión de riesgos y comités de seguimiento.

**Problema de negocio:** La evaluación del riesgo soberano requiere analizar conjuntamente indicadores de deuda externa, reservas internacionales, servicio de deuda y otras variables macroeconómicas. El proyecto busca aprovechar esta información para identificar países con mayor vulnerabilidad y reconocer patrones que puedan anticipar episodios de dificultades de pago (*distress*).

### Requisitos críticos de calidad (CTQ)

1. **Anticipación:** Identificar señales de riesgo antes de los eventos definidos como *distress*.
2. **Interpretabilidad:** Explicar los principales indicadores asociados con cada alerta.
3. **Comparabilidad:** Aplicar criterios consistentes entre países y períodos.
4. **Calidad de datos:** Documentar fuentes, cobertura y limitaciones.
5. **Utilidad:** Generar alertas que permitan priorizar el seguimiento.

### Variables de negocio

- Vulnerabilidad soberana externa.
- Riesgo de dificultades de pago.
- Exposición y servicio de deuda externa.
- Liquidez internacional y necesidades de refinanciamiento.
- Priorización del monitoreo del riesgo soberano.

## 3. Objetivo del proyecto

Desarrollar una herramienta de alerta temprana que permita evaluar la vulnerabilidad soberana externa de países emergentes y estimar el riesgo de episodios de dificultades de pago, mediante indicadores macroeconómicos y financieros y técnicas de análisis de datos, para apoyar la identificación de señales de deterioro y la priorización del seguimiento del riesgo soberano.

## 4. Métricas y metas

| Métrica | Línea base | Meta propuesta |
|---|---|---|
| Captura de eventos en el 25 % superior del ranking | Por establecer | ≥70 %, sujeto a validación |
| Desempeño predictivo (PR-AUC) | Modelo de referencia | Superar el modelo base |
| Explicación de alertas | No implementado | 100 % de países priorizados |
| Cobertura del diagnóstico | Por establecer | 100 % del universo final viable |
| Calidad de alertas | Por establecer | Evaluar precisión y falsas alarmas |

Las metas predictivas dependerán de la cantidad y calidad de eventos históricos disponibles.

## 5. Alcance

**Incluye:** Integración de datos públicos del Banco Mundial; análisis de vulnerabilidad soberana externa; construcción de un índice comparativo; evaluación de un modelo predictivo de *distress* a 12 meses, sujeto a viabilidad; y desarrollo de un sistema de alertas con visualización de resultados.

El universo inicial contempla países de América Latina y economías emergentes de referencia. Su composición definitiva se establecerá según la cobertura de los datos.

**Excluye:** Valoración de bonos soberanos, predicción garantizada de incumplimientos y automatización de decisiones de financiamiento.

## 6. Beneficios esperados

- **Analíticos:** Identificar perfiles de vulnerabilidad y patrones asociados con dificultades de pago.
- **Operativos:** Facilitar la comparación de países y la priorización de alertas.
- **Estratégicos:** Aportar evidencia para orientar análisis preventivos del riesgo soberano.

## 7. Planeación

| Fase DMAIC | Semanas | Actividad principal | Responsable |
|---|---|---|---|
| Definir | 1–2 | Delimitar el problema, los países y los criterios de *distress* | Equipo MIAD |
| Medir | 3–4 | Recopilar y evaluar datos históricos | Equipo MIAD |
| Analizar | 5–7 | Construir índice y evaluar modelos predictivos | Equipo MIAD |
| Mejorar | 8–10 | Integrar resultados y desarrollar alertas | Equipo MIAD |
| Controlar | 11–12 | Validar, documentar y entregar la herramienta | Equipo MIAD |

Las responsabilidades específicas se distribuirán entre los cuatro integrantes según las actividades del proyecto.

## 8. Restricciones y supuestos

- La disponibilidad histórica de datos varía entre países e indicadores.
- Los eventos utilizados como aproximación al *distress* no equivalen necesariamente a incumplimientos formales.
- La viabilidad del componente predictivo dependerá de contar con suficientes eventos históricos.
- El proyecto se desarrollará en 12 semanas con herramientas y datos públicos.
- El BID es una organización de referencia y no un patrocinador confirmado.
- La herramienta será un prototipo académico y no reemplazará la evaluación de especialistas.
