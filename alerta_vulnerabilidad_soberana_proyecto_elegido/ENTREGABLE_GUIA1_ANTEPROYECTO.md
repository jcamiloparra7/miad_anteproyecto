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

Para un banco multilateral de desarrollo como el Banco Interamericano de Desarrollo (BID), conocer la situación económica y financiera de los países es importante para evaluar los riesgos asociados con sus operaciones de financiamiento. Sin embargo, un país puede presentar señales de vulnerabilidad mucho antes de enfrentar dificultades para cumplir con sus obligaciones de deuda. Identificar estas señales y entender cómo se relacionan con episodios históricos de dificultades de pago puede aportar información valiosa para el seguimiento del riesgo soberano.

El Banco Mundial dispone de información histórica sobre deuda externa, reservas internacionales, servicio de deuda y otros indicadores macroeconómicos. Estos datos ofrecen la posibilidad de estudiar las condiciones que caracterizan a los países más vulnerables y analizar qué variables han estado asociadas con episodios de dificultades de pago.

A partir de esta información, el proyecto propone desarrollar una herramienta que permita evaluar la vulnerabilidad soberana externa de los países y estimar el riesgo de que experimenten episodios de *distress*. La intención es que ambos análisis se complementen y ayuden a identificar qué países requieren mayor atención, cuáles son los factores que explican las alertas y dónde conviene profundizar el análisis económico.

### Retos principales

Uno de los principales retos del proyecto es la disponibilidad y calidad de la información histórica. Aunque existen indicadores económicos y financieros para distintos países, no todos tienen la misma cobertura ni se actualizan con la misma frecuencia. Esto puede limitar las comparaciones y exigir ajustes en la selección de variables y países incluidos en el análisis.

Otro desafío es la identificación de episodios de *distress* soberano. Las dificultades graves de pago no ocurren con frecuencia y, además, no todos los eventos registrados representan necesariamente un incumplimiento formal de deuda. Por esta razón, será necesario definir con precisión qué situaciones se considerarán eventos de *distress* y verificar si existen suficientes observaciones históricas para desarrollar y evaluar un modelo predictivo.

Finalmente, la herramienta debe ofrecer resultados que puedan interpretarse desde una perspectiva económica. No basta con clasificar países según su nivel de vulnerabilidad o asignarles una probabilidad de *distress*: también es importante comprender qué indicadores influyen en cada resultado y cómo esa información puede contribuir a priorizar el seguimiento del riesgo soberano.

### Prioridad de negocio

La principal prioridad del proyecto es contribuir a la identificación temprana de países que podrían enfrentar dificultades para atender sus obligaciones de deuda externa. Para ello, se propone combinar el análisis de sus condiciones macroeconómicas y financieras con modelos que permitan reconocer patrones asociados con episodios históricos de *distress*.

Esta información permitiría diferenciar países que presentan vulnerabilidades estructurales de aquellos que, además, muestran señales de un posible deterioro en el corto plazo. Con estos resultados, una entidad como el BID podría contar con elementos adicionales para decidir dónde concentrar sus esfuerzos de seguimiento, qué situaciones requieren un análisis más profundo y cuáles deberían recibir atención prioritaria.

La herramienta no pretende reemplazar el criterio de los especialistas en riesgo soberano, sino aportar evidencia que complemente sus evaluaciones y facilite decisiones de monitoreo más consistentes.

### Recursos disponibles

Para desarrollar el proyecto se han identificado los siguientes recursos:

- **Fuentes de información**: se utilizarán bases de datos públicas del Banco Mundial, principalmente los Indicadores del Desarrollo Mundial (WDI) y las Estadísticas de Deuda Internacional (IDS). Estas fuentes contienen información histórica sobre deuda externa, reservas internacionales, servicio de deuda y otras variables macroeconómicas. Durante la etapa de exploración será necesario verificar su cobertura, consistencia y utilidad para identificar episodios de distress.

- **Equipo de trabajo**: el proyecto será desarrollado por cuatro estudiantes de la Maestría en Inteligencia Analítica de Datos de la Universidad de los Andes. El equipo aplicará conocimientos de estadística, procesamiento de datos y aprendizaje automático para construir y evaluar los componentes analíticos de la solución.

- **Herramientas tecnológicas**: se contempla utilizar Python y sus librerías de análisis de datos y modelado estadístico, junto con GitHub para el control de versiones y la colaboración entre los integrantes. La solución se desarrollará inicialmente como un prototipo académico, sin requerir infraestructura empresarial.

- **Acompañamiento académico**: el proyecto contará con las orientaciones y criterios de evaluación del curso Gerencia de Proyectos de Analytics. El BID se considera una organización de referencia para definir el caso de uso, pero no se cuenta con su participación ni con acceso a sus procesos internos.

### Tiempo estimado

El desarrollo del proyecto se estima en 12 semanas, distribuidas entre la preparación de los datos, el análisis exploratorio, la construcción y evaluación de los modelos y el desarrollo de la herramienta de visualización y seguimiento.

Durante las primeras semanas se revisará la disponibilidad de información y se definirá la metodología para identificar los eventos históricos de *distress*. Posteriormente, se construirá el índice de vulnerabilidad soberana externa y, dependiendo de la cantidad y calidad de los eventos identificados, se desarrollará el componente predictivo. Finalmente, se integrarán los resultados en una herramienta que permita comparar países, consultar sus principales indicadores y visualizar las alertas generadas.

El alcance definitivo del componente predictivo dependerá de los resultados de la exploración inicial de los datos.

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

**Mejoraremos:** la identificación y el seguimiento de países con vulnerabilidad soberana externa, incorporando herramientas analíticas que permitan reconocer señales de deterioro y estimar el riesgo de episodios de dificultades de pago (*distress*).

**Para:** equipos encargados del análisis macroeconómico y la evaluación del riesgo soberano en organismos multilaterales de desarrollo, tomando como referencia al Banco Interamericano de Desarrollo (BID).

**El usuario o cliente enfrenta:** la necesidad de analizar múltiples indicadores económicos y financieros para evaluar la situación de los países. Aunque esta información está disponible en diferentes fuentes, identificar patrones de vulnerabilidad y relacionarlos con episodios históricos de dificultades de pago requiere un análisis integrado.

**Al resolver este problema, se espera:** aportar evidencia que permita distinguir los países con mayores vulnerabilidades, identificar factores asociados con posibles dificultades de pago y establecer prioridades de seguimiento. Esto facilitaría un análisis preventivo del riesgo soberano, sin reemplazar las evaluaciones realizadas por especialistas.

---

## Parte III. Accesibilidad

### Existencia y ubicación de los datos

El proyecto utilizará principalmente información pública del Banco Mundial, disponible a través de sus bases de datos económicas y financieras. Entre las fuentes identificadas se encuentran los Indicadores del Desarrollo Mundial (WDI), las Estadísticas de Deuda Internacional (IDS), los Indicadores Mundiales de Gobernanza (WGI) y la base Global Economic Monitor (GEM).

Estas fuentes contienen información sobre deuda externa, servicio de deuda, reservas internacionales, crecimiento económico, condiciones institucionales y otras variables que pueden contribuir al análisis de la vulnerabilidad soberana externa. Algunas también incluyen registros de atrasos, reprogramaciones y alivios de deuda, que se evaluarán como posibles aproximaciones a episodios de *distress*.

La disponibilidad de estas fuentes permite plantear una primera versión de la herramienta. Sin embargo, será necesario revisar la cobertura histórica por país, la frecuencia de actualización, los datos faltantes y la cantidad de eventos registrados antes de definir el conjunto final de variables y el alcance del modelo predictivo.

El análisis de precios de mercado de la deuda soberana no forma parte del alcance inicial, debido a que las fuentes seleccionadas no ofrecen una cobertura homogénea de rendimientos, diferenciales de crédito o CDS.
Sí existen datos suficientes para formular una primera versión del problema. La exploración previa mostró que las siguientes fuentes de WBGAPI son las más relevantes:

### Modelabilidad del problema

El problema se abordará mediante dos componentes analíticos complementarios. El primero permitirá evaluar la vulnerabilidad soberana externa de los países a partir de indicadores económicos y financieros. Para ello, se explorarán técnicas de análisis multivariado, construcción de índices y segmentación que permitan identificar diferentes perfiles de vulnerabilidad.

El segundo componente buscará estimar la probabilidad de que un país experimente un episodio de *distress* durante los siguientes 12 meses. Se utilizarán modelos de clasificación supervisada, siempre que los datos históricos permitan definir los eventos de manera consistente y se cuente con suficientes observaciones para entrenar y evaluar los modelos.

Los resultados de ambos componentes se integrarán en un sistema de alertas que permita identificar países prioritarios y consultar los principales factores asociados con su clasificación. La evaluación incluirá comparaciones con modelos de referencia y pruebas sobre períodos históricos no utilizados durante el entrenamiento, para reducir el riesgo de obtener resultados artificialmente optimistas.

### Posibilidad de apoyo e implementación

La herramienta se plantea como un prototipo académico orientado al seguimiento del riesgo soberano. Su desarrollo utilizará fuentes públicas y herramientas de análisis de datos, por lo que no requiere inicialmente acceso a sistemas internos de una organización.

El BID se considera una entidad de referencia por su relación con el financiamiento y el desarrollo económico de América Latina. No obstante, la utilidad de la herramienta para sus procesos específicos tendría que evaluarse posteriormente con especialistas de la institución.

La implementación inicial se concentrará en demostrar que es posible integrar los indicadores, evaluar la vulnerabilidad de los países y generar alertas comprensibles. El componente predictivo estará sujeto a la disponibilidad de información histórica suficiente y a los resultados de su validación. Por tanto, el proyecto no contempla automatizar decisiones de financiamiento ni reemplazar las evaluaciones de riesgo realizadas por expertos.

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
