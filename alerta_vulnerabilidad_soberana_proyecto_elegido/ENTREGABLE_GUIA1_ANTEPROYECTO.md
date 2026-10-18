# Entregable Guía 1 - Anteproyecto

## Sistema híbrido de alerta temprana de vulnerabilidad soberana externa y riesgo de distress

**Programa:** Maestría en Inteligencia Analítica de Datos  
**Curso:** Gerencia de Proyectos de Analytics  
**Tipo de documento:** Borrador de entregable en Markdown con extensión estimada de 8 páginas al exportarse a PDF  
**Stakeholder principal asignado:** **Banco Interamericano de Desarrollo (BID)**, unidad de riesgo soberano / exposición país

## Resumen ejecutivo

Este anteproyecto propone desarrollar una herramienta analítica para **priorizar países emergentes con mayor vulnerabilidad soberana externa y mayor probabilidad de distress**, de forma que un banco multilateral con exposición país pueda focalizar su monitoreo, profundizar análisis y escalar tempranamente casos que ameriten revisión. La formulación parte de una revisión de datos disponibles en WBGAPI y de la necesidad de refinar el caso original de “alerta macroeconómica” hacia un problema más concreto, más accionable y mejor soportado por datos.

La solución recomendada no se plantea como un modelo de *right pricing* de bonos, porque las fuentes exploradas del Banco Mundial no incluyen de forma homogénea precios de mercado, spreads o CDS soberanos. En cambio, el proyecto sí puede formularse de manera sólida como un **sistema híbrido de alerta temprana de vulnerabilidad soberana externa**, apoyado en indicadores de liquidez externa, servicio de deuda, costo financiero, refinanciamiento y señales proxy de distress.

El proyecto integra tres componentes. Primero, una capa **no supervisada** que resume la vulnerabilidad estructural y segmenta países por perfiles de riesgo. Segundo, una capa **supervisada** que estima la probabilidad de observar un evento de distress proxy en el horizonte de 12 meses. Tercero, una capa de **decisión** que traduce score, probabilidad y señales mensuales en un semáforo ampliado y una watchlist de seguimiento. Esta formulación resulta adecuada para la guía porque alinea claramente stakeholder, problema, recursos, limitantes, beneficios esperados y criterios de éxito.

---

## Parte I. Idealización de problemáticas

La exploración inicial partió del sector financiero / gobierno y se enfocó en oportunidades de negocio donde los datos públicos del Banco Mundial ofrecieran una base razonable para construir una solución analítica. Se consideraron tres ideas principales.

### Idea 1. Alerta macroeconómica general para países emergentes

La primera idea buscaba detectar deterioro macroeconómico usando crecimiento, inflación, desempleo, reservas y cuenta corriente. Esta opción cumple bien con las características de recurrencia, alineación con monitoreo económico y posibilidad de medición; sin embargo, es relativamente amplia y corre el riesgo de quedarse en un diagnóstico general difícil de traducir en una acción concreta de negocio.

### Idea 2. Sistema de alerta de vulnerabilidad soberana externa y riesgo de distress

La segunda idea refina la oportunidad hacia un problema más específico: identificar países con presión creciente sobre su liquidez externa, su capacidad de servicio de deuda y su riesgo de refinanciamiento. Esta opción cumple mejor las siete características planteadas en la guía:

1. **Enfoque en usuario / cliente:** responde a la necesidad concreta de priorizar países.
2. **Métricas disponibles:** existen indicadores anuales y mensuales en WBGAPI.
3. **Champion identificable:** una unidad de riesgo soberano o exposición país.
4. **Evento recurrente:** el monitoreo se repite cada ciclo anual y mensual.
5. **Alineación estratégica:** apoya gestión de riesgo, asignación de esfuerzo analítico y revisión de exposición.
6. **Beneficio trazable:** mejora tiempos de reacción y estandarización de decisiones.
7. **Solución no trivial:** requiere combinar modelación, priorización y reglas operativas.

### Idea 3. Mispricing o *right pricing* de deuda soberana

La tercera idea resultó atractiva desde el punto de vista financiero, pero fue descartada como alcance principal porque exige precios de mercado, yields, spreads o CDS comparables, elementos que no están disponibles de manera robusta dentro del set explorado de WBGAPI. Por lo tanto, aunque puede ser una extensión futura, no cumple hoy con el criterio de accesibilidad suficiente para esta primera entrega.

### Selección de la oportunidad

La oportunidad seleccionada fue la **Idea 2**, ya que ofrece un mejor equilibrio entre valor de negocio, factibilidad de datos y claridad metodológica. Además, permite conectar el resultado analítico con una decisión concreta: **qué países deben escalarse para monitoreo intensivo, revisión de exposición o análisis económico profundo**.

---

## Parte II. Jerarquización, selección y descripción

### Descripción de la oportunidad

Un banco multilateral de desarrollo monitorea de manera continua el entorno macroeconómico y soberano de los países con los que trabaja. Cuando aparecen señales de presión externa, deterioro de reservas, encarecimiento de la deuda o eventos de atrasos, el costo de reaccionar tarde es alto: el análisis se vuelve más reactivo, la priorización entre países se vuelve discrecional y los comités reciben información menos comparable. La oportunidad consiste en crear una herramienta que organice el monitoreo con un criterio homogéneo y anticipatorio.

### Retos principales

Los retos más importantes son cuatro. El primero es que el distress soberano formal es poco frecuente, por lo que las etiquetas supervisadas son escasas y desbalanceadas. El segundo es que no todas las variables fiscales tienen buena cobertura, lo que obliga a centrar el alcance en vulnerabilidad externa y no en una visión fiscal exhaustiva. El tercero es que el stakeholder debe recibir una herramienta interpretable, no una caja negra. El cuarto es que la solución debe ser útil incluso cuando no se materializa un evento extremo, pues gran parte del valor radica en la priorización de vigilancia.

### Prioridad de negocio

La prioridad más importante de esta oportunidad es **mejorar la anticipación y la consistencia del monitoreo soberano**. El proyecto no pretende reemplazar al analista país, sino darle una capa sistemática de priorización y una narrativa comparable entre países.

### Recursos disponibles

El proyecto cuenta con cuatro tipos de recursos razonables:

- **Datos públicos** del Banco Mundial accesibles por WBGAPI.
- **Capacidad analítica** del equipo para construir modelos de series panel, clasificación y segmentación.
- **Infraestructura técnica ligera**, suficiente para construir un MVP reproducible.
- **Contexto académico** que permite trabajar con un stakeholder simulado, aun si no se tiene acceso directo a un usuario real.

### Tiempo estimado

La propuesta es factible como capstone porque puede organizarse en un MVP con horizonte de 10 a 12 semanas: definición, carga y limpieza, análisis exploratorio, construcción de score, clasificación supervisada, diseño del semáforo y documentación final.

### Autoridad final

En el contexto del proyecto académico, la autoridad final se asimila al patrocinio de una **unidad de riesgo soberano / exposición país del BID**, apoyada por el asesor del proyecto y validada por los criterios de la guía.

### Dinámica de las 5W

| Pregunta | Respuesta |
|---|---|
| **Who** | El stakeholder primario es la unidad de riesgo soberano / exposición país del BID. También participan equipos país, comité de riesgo y tesorería. |
| **What** | Se busca resolver la falta de una herramienta integrada, comparable y temprana para priorizar países con mayor vulnerabilidad soberana externa. |
| **Where** | El problema ocurre en el proceso de monitoreo y revisión de exposición país de una entidad multilateral con foco en América Latina y benchmarking frente a otros emergentes. |
| **When** | El problema aparece cada vez que se debe asignar capacidad analítica, preparar comités, revisar cupos o responder a señales macrofinancieras cambiantes. |
| **Why** | Porque el monitoreo reactivo genera tardanza, heterogeneidad y menor trazabilidad en decisiones que afectan exposición, seguimiento y diálogo con países. |

### Enunciado del problema de negocio

**Mejoraremos** la priorización del monitoreo soberano externo y la identificación temprana de países con señales de vulnerabilidad y distress.  
**Para** una unidad de riesgo soberano / exposición país de un banco multilateral de desarrollo.  
**El usuario o cliente lidia hoy** con señales dispersas, comparabilidad limitada entre países y escalamiento reactivo frente a episodios de presión externa.  
**Al resolver esto, se impactará positivamente el negocio** porque se reducirá la discrecionalidad del monitoreo, se optimizará el uso del esfuerzo analítico y se mejorará la oportunidad de revisión de exposición.

---

## Parte III. Accesibilidad

### Existencia y ubicación de los datos

Sí existen datos suficientes para formular una primera versión del problema. La exploración previa mostró que las siguientes fuentes de WBGAPI son las más relevantes:

- **WDI (2):** crecimiento, inflación, cuenta corriente, reservas, reservas en meses de importación, reservas como porcentaje de deuda externa y deuda de corto plazo.
- **WGI (3):** efectividad del gobierno como control institucional.
- **IDS (6 / 81):** deuda externa, servicio de deuda, intereses externos, costo promedio de nueva deuda, madurez promedio de nueva deuda y variables proxy de distress como atrasos, reprogramación o condonación.
- **GEM (15):** tipo de cambio oficial y reservas para seguimiento mensual.

La revisión también permitió identificar qué no conviene usar en el MVP: algunas variables fiscales, como pagos de intereses sobre ingresos o recaudo tributario sobre PIB, tienen una cobertura más débil; y la capa de precios de mercado no está disponible con suficiente homogeneidad para formular un caso de mispricing soberano.

### Modelabilidad del problema

El problema sí se puede modelar. Existe suficiente estructura para proponer un enfoque híbrido:

1. **No supervisado:** construir un score de vulnerabilidad soberana externa y segmentar países por perfiles de riesgo.
2. **Supervisado:** estimar la probabilidad de un evento de distress proxy a 12 meses.
3. **Reglas de negocio:** traducir ambos resultados a un semáforo y una watchlist operativa.

Este enfoque es preferible a un único modelo porque aprovecha el valor de los datos incluso cuando los eventos extremos son escasos.

### Posibilidad de apoyo e implementación

La solución sería apoyable por una organización como el BID porque su salida es interpretable, actualizable y accionable. La herramienta no exige integración costosa ni bases propietarias para un MVP. Sin embargo, hay limitantes visibles:

- el stakeholder real no está disponible durante el curso y debe simularse;
- las etiquetas de distress pueden ser raras;
- la utilidad final dependerá de la capacidad del producto para explicar por qué un país fue clasificado en cierto nivel de riesgo.

En síntesis, la accesibilidad de datos y métodos es suficiente para continuar, siempre que el problema se reformule de manera realista.

---

## Parte IV. Replanteamiento y limitantes

### Replanteamiento del problema

El problema se replantea desde una versión demasiado amplia o financieramente ambiciosa hacia una formulación más factible:

> **Desarrollar una herramienta híbrida de alerta temprana que combine técnicas no supervisadas y supervisadas para clasificar países según su vulnerabilidad soberana externa y estimar su probabilidad de distress, generando un semáforo ampliado para priorizar monitoreo y revisión de exposición.**

Esta reformulación mejora la factibilidad porque:

- usa indicadores con mejor cobertura histórica;
- evita prometer pricing de mercado sin datos de mercado;
- permite una validación empírica más clara;
- y mantiene una conexión directa con decisiones reales de seguimiento.

### Limitantes del proyecto

1. **Sin pricing de mercado:** no se puede afirmar mispricing de bonos soberanos sin yields, spreads o CDS.
2. **Etiquetas proxy:** distress no equivale a default formal; se aproxima mediante atrasos, reprogramaciones y alivios.
3. **Desbalance de clases:** los eventos severos serán menos frecuentes que los años sin distress.
4. **Heterogeneidad entre países:** incluso entre emergentes comparables, siempre existirán diferencias institucionales y estructurales.
5. **Implementación parcial:** el MVP puede apoyar priorización, pero no reemplaza el juicio experto.

### Decisión metodológica derivada de los limitantes

Como consecuencia, el semáforo final no debe depender exclusivamente del clasificador supervisado. Debe salir de una lógica híbrida donde el score estructural, la probabilidad de distress y las señales mensuales se combinen en una regla de decisión transparente.

---

## Parte V. Beneficios esperados

### Métrica de negocio

La principal métrica de negocio es la capacidad de la herramienta para **capturar tempranamente los países que luego exhiben señales de distress dentro del grupo priorizado para seguimiento**. En términos operativos, esto puede expresarse como el porcentaje de eventos contenidos en el 25% superior del ranking de riesgo.

### Beneficios cualitativos

- estandarización del monitoreo entre analistas y equipos país;
- trazabilidad de por qué un país fue escalado;
- mejor preparación de discusiones en comité;
- reducción del sesgo puramente discrecional.

### Beneficios cuantitativos propuestos

| Beneficio | Métrica propuesta | Situación actual estimada | Meta inicial |
|---|---|---:|---:|
| Captura temprana de señales | % de eventos proxy capturados en top 25% del ranking | No medido | >= 70% |
| Rapidez operativa | Días hábiles para actualizar watchlist | 20 | <= 5 |
| Cobertura analítica | % de países priorizados con explicación de drivers | 0% | 100% |
| Eficiencia de monitoreo | % del universo total que requiere monitoreo intensivo | 100% manual / no priorizado | 20%-30% priorizado |

### Beneficio para el stakeholder

El valor para el BID no estaría solo en “predecir” eventos extremos, sino en **usar mejor la capacidad analítica y reducir monitoreo reactivo**. Esto es importante porque, incluso si los eventos severos son escasos, la organización sigue necesitando una lógica consistente para decidir dónde profundizar análisis.

---

## Parte VI. Criterios de éxito

El proyecto se considerará exitoso si cumple simultáneamente criterios de negocio, analíticos y de ejecución.

### Criterios de éxito del producto

1. El score y el semáforo permiten distinguir grupos de países con diferente nivel de vulnerabilidad.
2. La capa supervisada mejora el ranking de riesgo frente a un baseline simple.
3. El resultado es interpretable y cada alerta puede explicarse con drivers concretos.
4. La watchlist mensual permite seguimiento posterior en países ya priorizados.

### Criterios de éxito analítico

- **PR-AUC** superior al baseline.
- **Recall@top-k** suficiente para concentrar eventos en el tramo alto del ranking.
- estabilidad de clusters o perfiles de riesgo a través del tiempo.
- coherencia económica de factores y coeficientes.

### Criterios de éxito del proyecto

- cumplimiento del cronograma del MVP;
- repositorio organizado y reproducible;
- documentación suficiente para explicar decisiones de alcance, métodos y limitantes;
- correspondencia clara entre problema, stakeholder, métricas y producto final.

### Métricas de seguimiento durante la ejecución

| Dimensión | Métrica |
|---|---|
| Datos | % de indicadores cargados y validados según catálogo |
| Desarrollo | avance semanal por entregable del cronograma |
| Modelado | número de versiones de score y clasificador comparadas |
| Calidad | consistencia de variables, nulos, trazabilidad y documentación |

---

## Parte VII. Contexto

El Banco Interamericano de Desarrollo es un buen stakeholder para este caso porque su misión de desarrollo convive con la necesidad de monitorear sostenibilidad macroeconómica y capacidad de ejecución de los países miembros. A diferencia de un inversionista de mercado puro, una entidad como el BID obtiene valor de una herramienta que prioriza monitoreo y apoyo técnico, no solamente de una señal de compra o venta. Además, el foco regional en América Latina combina naturalmente con el universo principal propuesto, mientras que los comparadores emergentes externos aportan contexto sin desdibujar el usuario principal.

Dentro de ese contexto, la unidad de riesgo soberano o exposición país necesita información comparable, oportuna y defendible para discutir con equipos sectoriales, equipos país y comités internos. El proyecto se inserta precisamente en ese punto: no reemplaza la evaluación cualitativa, pero sí organiza el monitoreo con una capa objetiva y trazable.

---

## Propuesta concreta de solución y herramienta

La solución final del capstone se concibe como una **herramienta de priorización soberana** con tres salidas integradas:

1. **Score anual de vulnerabilidad soberana externa**, construido con componentes de liquidez, servicio de deuda, costo financiero, refinanciamiento, estabilidad macro y capacidad institucional.
2. **Probabilidad anual de distress a 12 meses**, generada por un clasificador supervisado entrenado con etiquetas proxy.
3. **Semáforo ampliado y watchlist mensual**, que combine score, probabilidad y señales recientes de tipo de cambio / reservas.

### Etiquetas sugeridas del semáforo

| Etiqueta | Interpretación |
|---|---|
| Verde | Estabilidad relativa y baja prioridad |
| Amarillo | Vigilancia preventiva |
| Naranja | Deterioro relevante y seguimiento reforzado |
| Rojo | Alta vulnerabilidad o alta probabilidad de distress |
| Negro | Distress observado o activación de evento proxy |

Esta estructura permite responder dos preguntas distintas pero complementarias: **qué países están estructuralmente más frágiles** y **qué países muestran mayor probabilidad de deterioro severo en el siguiente año**.

---

## Cierre

Con base en la guía y en la exploración de datos disponible, el caso de **alerta temprana de vulnerabilidad soberana externa** representa una oportunidad de negocio mejor formulada y más viable que un proyecto de pricing de deuda soberana. La combinación de una capa no supervisada, una capa supervisada y un semáforo expandido permite construir una solución analítica sólida, interpretable y alineada con un stakeholder claro. Por ello, se recomienda avanzar con este alcance como base del capstone y dejar como extensión futura la integración de datos de mercado para estudiar mispricing o relative value.
