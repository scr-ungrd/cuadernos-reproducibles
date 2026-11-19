---
title: Requisitos para modelos
subtitle: Requisitos para publicar modelos de aprendizaje automático, estadísticos y de simulación abiertos y reproducibles
date: 2026-11-16
authors:
  - name: Subdirección para el Conocimiento del Riesgo
    affiliation: Unidad Nacional para la Gestión del Riesgo de Desastres (UNGRD)
    github: scr-ungrd
license: CC-BY-4.0
keywords:
  - modelos
  - aprendizaje automático
  - validación
  - incertidumbre
  - reproducibilidad
  - ficha del modelo
  - ciencia abierta
  - riesgo de desastres
abbreviations:
  UNGRD: Unidad Nacional para la Gestión del Riesgo de Desastres
  SCR: Subdirección para el Conocimiento del Riesgo
  WCAG: Web Content Accessibility Guidelines
  W3C: World Wide Web Consortium
  DOI: Digital Object Identifier
  ORCID: Open Researcher and Contributor ID
  OSI: Open Source Initiative
  OWASP: Open Worldwide Application Security Project
  MinTIC: Ministerio de Tecnologías de la Información y las Comunicaciones
  HIPs: Hazard Information Profiles
  ODD: Overview, Design concepts, Details
---

+++ {"part": "abstract"}

Este documento establece los requisitos que debe cumplir un modelo (de aprendizaje automático, estadístico o de simulación física) de conocimiento del riesgo para publicarse en la colección como un objeto documentado, validado y reproducible. Define 46 requisitos (41 obligatorios, de ellos 5 críticos, y 5 recomendados), cada uno con un identificador y una base documental citada. Se derivan de las fichas de modelo (*model cards*) y las hojas de datos (*datasheets*), el programa de reproducibilidad de NeurIPS, el protocolo ODD, el Digital Public Goods Standard y la lista OWASP Top 10:2025. Ningún requisito exige pagos. El documento incluye plantillas, una lista de verificación y un prompt que audita el cumplimiento y genera un reporte.

+++

## 1. Alcance y convenciones

### 1.1 Alcance

Estas instrucciones se aplican a todo **modelo** que un cuaderno de la colección entrene, calibre o ejecute para estimar una amenaza, una exposición, una vulnerabilidad, un riesgo o una pérdida. Incluye los modelos de aprendizaje automático, los estadísticos (por ejemplo, de frecuencia de extremos) y los de simulación física o basados en agentes.

Se distinguen cuatro objetos relacionados:

- **Cuaderno**: documenta un análisis y es la fuente del método. Se rige por la [guía](01-cuadernos-de-conocimiento.md).
- **Modelo**: la representación que produce los resultados. Se rige por este documento.
- **Tablero**: muestra resultados ya calculados. Se rige por los [requisitos para tableros](06-estandar-tableros.md).
- **Aplicación**: ejecuta el modelo con entradas de la persona usuaria. Se rige por los [requisitos para aplicaciones](07-estandar-aplicaciones.md).

Complementan los [requisitos para datos](03-estandar-de-datos.md), que cubren las entradas del modelo, y los [requisitos para el uso de IA](05-uso-de-ia.md), que cubren el uso de asistentes de IA en la preparación del trabajo. Un modelo preentrenado de terceros que el cuaderno solo llama como componente (por ejemplo, un modelo de lenguaje de Hugging Face) se rige por los [requisitos para el uso de LLMs](09-uso-de-llms.md); si el cuaderno lo ajusta o lo entrena, aplican ambos. Un cuaderno de análisis estadístico sin un modelo predictivo o de simulación no necesita aplicar estos requisitos. La seguridad común a todo repositorio (secretos, datos personales y rutas locales, código no confiable, dependencias y *releases*) la cubren los [requisitos de seguridad](10-requisitos-seguridad.md); los requisitos de seguridad de este documento se aplican además.

### 1.2 Convenciones

1. **Identificador.** Cada requisito tiene un código de tres letras y dos cifras (por ejemplo, USO-01). Los códigos se usan en la lista de verificación, en el prompt de validación y en los reportes.
2. **Nivel.** *Obligatorio* significa que el cuaderno, el tablero o la aplicación no se acepta si el requisito aplica y no se cumple. *Recomendado* significa que el cumplimiento mejora la calidad pero no condiciona la aceptación. *Crítico* es un requisito obligatorio cuyo incumplimiento bloquea la publicación, cualquiera sea la puntuación total.
3. **Base.** Entre paréntesis, cada requisito indica el documento, el año y, cuando corresponde, el criterio o el apartado del que procede. Los requisitos cuya base es «Requisito de esta guía» los establece este documento y no provienen de una fuente externa.
4. **Redacción.** Cada requisito se enuncia en el estado conforme: describe cómo es un objeto que lo cumple. Los requisitos que dicen «aplica solo si» se marcan «No aplica» cuando no corresponden.
5. **Citas y traducciones.** Las citas siguen la norma APA 7. Los textos de las fuentes en inglés se traducen al español; las traducciones son propias. Los nombres de campos, códigos y apartados de las fuentes se conservan en su idioma original.
6. **Fecha de consulta.** Las fuentes web sin fecha de publicación se consultaron el 16 de noviembre de 2026 (véanse las Referencias). Los estándares y las guías cambian: antes de publicar, confirme la versión vigente.

### 1.3 Política de costo cero

Ningún requisito de este documento exige comprar suscripciones, licencias ni cómputo. Un cuaderno que necesite una GPU de pago ofrece una versión reducida o pesos preentrenados que se ejecuten con cómputo gratuito (REP-03).

### 1.4 Documentos de referencia

**Tabla 1.** Documentos de los que se derivan los requisitos.

```{list-table}
:header-rows: 1

* - Documento
  - Qué establece
  - Requisitos que se derivan
* - Mitchell et al. (2019). Model cards
  - Formato para documentar el uso previsto, los datos y el desempeño desglosado de un modelo
  - USO, VAL-03, VAL-05
* - Gebru et al. (2021). Datasheets for datasets
  - Formato para documentar la motivación, composición y sesgos de un conjunto de datos
  - DAT-02
* - Pineau et al. (2021). Reproducibilidad en aprendizaje automático
  - Política de código, lista de verificación y reporte de varias ejecuciones (NeurIPS 2019)
  - MET-03, VAL-01, REP
* - Grimm et al. (2020). Protocolo ODD
  - Formato estándar para describir modelos basados en agentes y de simulación
  - MET-02
* - Digital Public Goods Alliance (s. f.); OWASP Foundation (2025); Carroll et al. (2020); CRED (2026)
  - No hacer daño, integridad de software, gobernanza de datos de comunidades y sesgos de reporte
  - ETI, MET-06, DOC-01
* - [Requisitos para datos](03-estandar-de-datos.md), [requisitos para el uso de IA](05-uso-de-ia.md) y [requisitos para aplicaciones](07-estandar-aplicaciones.md)
  - Datos, licencias, costo cero, declaración de IA y análisis de no hacer daño que el modelo hereda
  - DAT-01, DAT-05, REP-03, ETI-01, DOC-05
```

## 2. Requisitos

### 2.1 Propósito y uso previsto

Un modelo es una representación simplificada del riesgo, y sus resultados orientan decisiones. Esta sección pide declarar para qué sirve y para qué no. La ficha del modelo (*model card*) es el formato más usado: reúne el uso previsto, los usos no previstos, los datos y el desempeño en un solo documento (Mitchell et al., 2019).

:::{important} USO-02: los límites de validez son obligatorios
Un modelo entrenado en el Caribe puede fallar en los Andes, y uno calibrado con 2000–2020 puede no representar el clima actual. La ficha dice dónde, cuándo y a qué escala el modelo es válido.
:::

Use esta plantilla (`MODEL_CARD.md`):

```markdown
# Ficha del modelo

- **Nombre y versión:** <nombre> v<X.Y.Z>
- **Propósito y decisión que apoya:** <qué estima y para qué>
- **Uso previsto:** <territorio, periodo, escala>
- **Usos no previstos:** <por ejemplo, no sustituye un estudio de microzonificación>
- **Datos de entrenamiento:** <DOI, periodo, cobertura; hoja de datos>
- **Método:** <tipo de modelo, parámetros, enlace al cuaderno>
- **Desempeño:** <métricas con incertidumbre, por región y periodo>
- **Límites y casos de fallo:** <dónde falla y por qué>
- **Responsable de revisar el resultado:** <persona o dependencia>
- **Licencia, DOI y contacto:** <...>
```

*Requisitos de este grupo: USO-01, USO-02, USO-03, USO-04. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.2 Datos del modelo

Los datos del modelo cumplen los [requisitos para datos](03-estandar-de-datos.md). Esta sección agrega lo que un modelo necesita de ellos.

- **Hoja de datos.** Documenta cómo y por qué se recolectaron los datos de entrenamiento, qué contienen y qué sesgos tienen (Gebru et al., 2021).
- **Partición.** En datos con estructura espacial o temporal, una partición aleatoria deja registros vecinos en entrenamiento y en prueba, y el desempeño parece mejor de lo que es (DAT-03). Separe por bloques de territorio o por periodos.
- **Eventos raros.** Los extremos son pocos por definición; documente el desbalance y cómo se trató.
- **Clases de amenaza.** Use los códigos HIPs 2025 y registre la equivalencia con las clases de la fuente (DAT-05).

*Requisitos de este grupo: DAT-01, DAT-02, DAT-03, DAT-04, DAT-05, DAT-06, DAT-07. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.3 Descripción del método

El método se describe de modo que otra persona pueda reimplementarlo. Para cada parámetro, indique su valor, su unidad y de dónde salió. Los modelos basados en agentes y otras simulaciones se describen con el protocolo ODD (*Overview, Design concepts, Details*), un formato estándar que mejora la claridad y la replicación (Grimm et al., 2020).

Dos riesgos son frecuentes. El primero es ajustar los hiperparámetros con el conjunto de prueba: el desempeño reportado deja de ser independiente (MET-03; Pineau et al., 2021). El segundo es guardar los pesos con `pickle`, que puede ejecutar código al cargarse; la lista OWASP Top 10:2025 incluye los fallos de integridad de software y de datos entre sus riesgos (OWASP Foundation, 2025, A08).

*Requisitos de este grupo: MET-01, MET-02, MET-03, MET-04, MET-05, MET-06. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.4 Validación y desempeño

Validar es mostrar que el modelo funciona donde se va a usar. Esta sección pide cuatro cosas.

1. **Datos independientes.** Los datos de validación no se usan para entrenar ni calibrar (VAL-01).
2. **Desempeño desglosado.** Un promedio nacional puede ocultar un mal desempeño justo en los territorios con menos datos. Reporte por región, tipo de territorio y periodo (VAL-03; Mitchell et al., 2019).
3. **Línea base.** Compare con un método simple. Si el modelo no lo supera, no se justifica su complejidad (VAL-04).
4. **Casos de fallo.** Documente dónde falla y qué pasa fuera del rango de los datos (VAL-05).

*Requisitos de este grupo: VAL-01, VAL-02, VAL-03, VAL-04, VAL-05, VAL-06, VAL-07. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.5 Incertidumbre y sensibilidad

Un valor único sin incertidumbre da una precisión falsa. Identifique las fuentes de incertidumbre (datos, parámetros y estructura del modelo), muestre cuáles afectan más el resultado con un análisis de sensibilidad y entregue el resultado con intervalos, ensambles o probabilidades. Si usa lenguaje calibrado, siga la convención del IPCC y declárela.

*Requisitos de este grupo: INC-01, INC-02, INC-03, INC-04. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.6 Reproducibilidad

La reproducibilidad de un modelo es más difícil que la de un análisis: el entrenamiento puede ser aleatorio y depender del hardware. El programa de reproducibilidad de NeurIPS 2019 combinó una política de código, un reto comunitario y una lista de verificación de reproducibilidad (Pineau et al., 2021). Esta guía adopta tres de sus ideas: fijar semillas y reportar la dispersión de varias ejecuciones (REP-02), publicar el código y los artefactos (REP-04) y completar una lista de verificación (REP-05).

**Costo cero.** Un cuaderno que exige una GPU de pago no cumple los requisitos. Ofrezca una versión reducida o los pesos preentrenados para que cualquiera ejecute el cuaderno con cómputo gratuito (REP-03).

*Requisitos de este grupo: REP-01, REP-02, REP-03, REP-04, REP-05, REP-06, REP-07. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.7 Riesgos, sesgos y uso responsable

Un modelo de riesgo tiene consecuencias. El análisis de no hacer daño (ETI-01) sigue el Digital Public Goods Standard (Digital Public Goods Alliance, s. f., indicador 9) y usa la plantilla `DO_NO_HARM.md` de los [requisitos para aplicaciones](07-estandar-aplicaciones.md).

Los registros de desastres y las estaciones de medición se concentran donde hay más población e instituciones, y los modelos que aprenden de ellos heredan ese sesgo (CRED, 2026). Evalúe y declare cómo cambia el desempeño en los territorios con menos datos (ETI-02). No entrene con datos personales ni de comunidades sin autorización (Carroll et al., 2020).

*Requisitos de este grupo: ETI-01, ETI-02, ETI-03, ETI-04, ETI-05. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.8 Documentación y ciclo de vida

Un modelo se mantiene mientras sus datos y su territorio no cambien. Defina cuándo se considera obsoleto, quién decide reentrenarlo o retirarlo (DOC-03) y qué cambios suben la versión (DOC-02). Los pesos heredan las condiciones de los datos de entrenamiento: si una licencia de datos no permite redistribuir derivados, tampoco se publican los pesos (DOC-04).

*Requisitos de este grupo: DOC-01, DOC-02, DOC-03, DOC-04, DOC-05, DOC-06. Su enunciado completo está en la lista de verificación de la Sección 3.*

## 3. Lista de verificación

La lista tiene 46 requisitos: 41 obligatorios y 5 recomendados. Los 5 requisitos **críticos** (USO-02, DAT-01, VAL-01, REP-01 y ETI-01) bloquean la publicación si no se cumplen.

**Criterio de aceptación.** Un objeto cumple los requisitos si (1) ningún requisito crítico está en incumplimiento y (2) el puntaje de requisitos obligatorios es de 90 o más, calculado como se indica en el prompt de la Sección 4.

**2.1. Propósito y uso previsto**

- [ ] **USO-01.** Un archivo `MODEL_CARD.md` describe el modelo: propósito, versión, autoría, licencia, uso previsto y datos de entrenamiento. (Mitchell et al., 2019)
- [ ] **USO-02.** **Crítico.** La ficha declara los usos no previstos y los límites de validez del modelo (territorio, periodo, escala, rango de las variables), y avisa que el resultado no sustituye estudios ni productos oficiales. (Mitchell et al., 2019; Requisito de esta guía)
- [ ] **USO-03.** La ficha justifica por qué se necesita este tipo de modelo (aprendizaje automático, estadístico o físico) y qué decisión apoya. (Requisito de esta guía)
- [ ] **USO-04.** La ficha indica quién revisa el resultado antes de usarlo en una decisión de gestión del riesgo. (Requisito de esta guía)

**2.2. Datos del modelo**

- [ ] **DAT-01.** **Crítico.** Los datos de entrenamiento, calibración y forzamiento cumplen los [requisitos para datos](03-estandar-de-datos.md): licencia, metadatos y ausencia de datos personales. (Requisitos para datos, INV, LIC y PER)
- [ ] **DAT-02.** Los datos de entrenamiento tienen una hoja de datos (*datasheet*) con motivación, composición, recolección, sesgos conocidos y usos recomendados. (Gebru et al., 2021)
- [ ] **DAT-03.** La partición en entrenamiento, validación y prueba está documentada y evita la fuga de información; con datos espaciales o temporales, la separación es por bloques de territorio o por periodos, no aleatoria. (Requisito de esta guía)
- [ ] **DAT-04.** La fuente, la calidad y la incertidumbre de las etiquetas o de la verdad de terreno están documentadas. (Requisito de esta guía)
- [ ] **DAT-05.** Si el modelo clasifica amenazas o eventos, usa los códigos HIPs 2025 y registra la equivalencia con las clases de la fuente. (Requisitos para datos, EST-11)
- [ ] **DAT-06.** Los datos sintéticos o simulados se identifican como tales y no se mezclan con datos observados sin marcarlos. (Requisito de esta guía)
- [ ] **DAT-07.** Si los eventos son raros (por ejemplo, extremos), el desbalance se documenta y se trata de forma explícita. (Requisito de esta guía)

**2.3. Descripción del método**

- [ ] **MET-01.** El modelo se describe con sus ecuaciones o su arquitectura, sus supuestos, sus parámetros, las unidades y el origen de cada parámetro (calibrado o tomado de la literatura). (Requisito de esta guía)
- [ ] **MET-02.** Un modelo basado en agentes o de simulación social se describe con el protocolo ODD (aplica solo a modelos basados en agentes). (Grimm et al., 2020)
- [ ] **MET-03.** Los hiperparámetros y su método de selección están documentados, y la selección no usa el conjunto de prueba. (Pineau et al., 2021)
- [ ] **MET-04.** En un modelo físico o numérico se declaran la resolución, la discretización, las condiciones de frontera y las comprobaciones numéricas (convergencia, balance de masa) (aplica solo a modelos físicos). (Requisito de esta guía)
- [ ] **MET-05.** Los modelos o pesos de terceros se citan con nombre, versión, licencia, DOI y procedencia de los datos de preentrenamiento, si se conoce. (Requisitos para datos, INV-02 y INV-06)
- [ ] **MET-06.** Los pesos se guardan en un formato que no ejecuta código al cargarse (por ejemplo, ONNX, safetensors o NetCDF) y no en `pickle`. (OWASP Foundation, 2025, A08)

**2.4. Validación y desempeño**

- [ ] **VAL-01.** **Crítico.** El modelo se validó con datos independientes que no se usaron para entrenarlo ni calibrarlo. (Pineau et al., 2021; Requisito de esta guía)
- [ ] **VAL-02.** Las métricas se justifican para el problema (en eventos raros no basta la exactitud global) y se reportan con su incertidumbre. (Requisito de esta guía)
- [ ] **VAL-03.** El desempeño se desglosa por región, tipo de territorio, periodo y, si aplica, tipo o magnitud del evento. (Mitchell et al., 2019)
- [ ] **VAL-04.** El modelo se compara con una línea base simple (por ejemplo, climatología o persistencia) y con el método vigente, si existe. (Requisito de esta guía)
- [ ] **VAL-05.** Los casos de fallo conocidos y los límites de extrapolación están documentados. (Mitchell et al., 2019)
- [ ] **VAL-06.** Cuando hay eventos históricos documentados, se verifica si el modelo los habría reproducido o anticipado (*back-testing*). (Requisito de esta guía)
- [ ] **VAL-07.** *(Recomendado)* Una persona experta del dominio revisó los resultados y su validez física o territorial. (Requisito de esta guía)

**2.5. Incertidumbre y sensibilidad**

- [ ] **INC-01.** Las fuentes de incertidumbre (datos, parámetros y estructura del modelo) se identifican y, cuando es posible, se cuantifican. (Requisito de esta guía)
- [ ] **INC-02.** Un análisis de sensibilidad muestra qué parámetros o entradas más afectan el resultado. (Requisito de esta guía)
- [ ] **INC-03.** Los resultados se entregan con su incertidumbre (intervalos, ensambles o probabilidades) y no solo como un valor único. (Requisito de esta guía)
- [ ] **INC-04.** *(Recomendado)* Si el modelo entrega probabilidades, se comprueba su calibración. (Requisito de esta guía)

**2.6. Reproducibilidad**

- [ ] **REP-01.** **Crítico.** Desde un entorno limpio, el cuaderno reproduce el entrenamiento o la ejecución con resultados dentro de una tolerancia declarada. (Pineau et al., 2021; Requisito de esta guía)
- [ ] **REP-02.** Las semillas están fijadas, las fuentes de no determinismo (GPU, paralelismo) están declaradas y los resultados se reportan como media y dispersión de varias ejecuciones. (Pineau et al., 2021)
- [ ] **REP-03.** El cuaderno declara el hardware, la memoria y el tiempo que necesita, y se ejecuta con cómputo gratuito (Colab o Binder) o ofrece una versión reducida o pesos preentrenados. (Requisitos para datos, 1.3)
- [ ] **REP-04.** Los pesos y los artefactos intermedios están archivados con DOI y suma de verificación. (Chue Hong et al., 2022)
- [ ] **REP-05.** La lista de verificación de reproducibilidad de aprendizaje automático está completa y archivada en el repositorio. (Pineau et al., 2021)
- [ ] **REP-06.** Un registro versionado guarda, por cada ejecución, los parámetros, las métricas y la versión del código y de los datos. (Pineau et al., 2021)
- [ ] **REP-07.** *(Recomendado)* Pruebas automáticas con un caso de referencia detectan cambios inesperados en los resultados. (Requisito de esta guía)

**2.7. Riesgos, sesgos y uso responsable**

- [ ] **ETI-01.** **Crítico.** Existe un análisis de «no hacer daño» que identifica los usos indebidos y los daños posibles de los resultados del modelo y las medidas adoptadas. (Digital Public Goods Alliance, s. f., indicador 9)
- [ ] **ETI-02.** Se evaluaron los sesgos de los datos y del modelo, en especial la cobertura desigual de estaciones y registros entre territorios. (CRED, 2026; Mitchell et al., 2019)
- [ ] **ETI-03.** No se usan datos personales ni de comunidades para entrenar el modelo sin la autorización registrada que exigen los requisitos para datos. (Carroll et al., 2020; Requisitos para datos, PER-02)
- [ ] **ETI-04.** Si el modelo es una caja negra, sus resultados se acompañan de una explicación (importancia de variables o mapas de contribución) o de la declaración de que no es interpretable. (Requisito de esta guía)
- [ ] **ETI-05.** *(Recomendado)* Un modelo cuyos resultados orienten decisiones de alto impacto tuvo una validación externa. (Requisito de esta guía)

**2.8. Documentación y ciclo de vida**

- [ ] **DOC-01.** El `README` permite a una persona técnica entrenar, ejecutar y evaluar el modelo. (Digital Public Goods Alliance, s. f., indicador 5)
- [ ] **DOC-02.** Las versiones siguen el versionado semántico: un cambio de datos, de arquitectura o de hiperparámetros sube la versión, y el `CHANGELOG.md` registra su efecto en el desempeño. (Requisito de esta guía)
- [ ] **DOC-03.** Un criterio dice cuándo el modelo se considera obsoleto (por ejemplo, por cambio en los datos) y quién decide reentrenarlo o retirarlo. (Requisito de esta guía)
- [ ] **DOC-04.** El código y los pesos tienen una licencia abierta compatible con las licencias de los datos de entrenamiento. (Requisitos para datos, INV-05 y LIC-04)
- [ ] **DOC-05.** El uso de IA en la preparación del código, los textos o los datos se declara según los [requisitos para el uso de IA](05-uso-de-ia.md). (Requisitos para el uso de IA, U04)
- [ ] **DOC-06.** *(Recomendado)* Los pesos también se publican en un repositorio de modelos de acceso libre, con la ficha del modelo. (Requisito de esta guía)

## 4. Prompt para validar los requisitos para modelos

Este prompt convierte la lista de verificación en una auditoría repetible. Lee el repositorio de un modelo, revisa su código y su documentación, reproduce lo que sea posible y genera un **reporte de cumplimiento** en Markdown y JSON. Funciona con cualquier asistente de IA que pueda leer archivos y ejecutar comandos.

**Procedimiento de uso**

1. Copie el prompt completo y reemplace los valores entre `<>` de la sección ENTRADAS.
2. Ejecútelo desde un entorno con acceso a los archivos del repositorio. Para comprobar DOI, paquetes, la URL publicada o la ejecución, use el modo ampliado que indica la sección ENTRADAS.
3. Revise el reporte con una persona. Un asistente de IA puede equivocarse al leer un archivo o interpretar un criterio. El resultado es un apoyo a la revisión y no una certificación, y todo lo marcado «Requiere revisión humana» lo decide una persona.
4. Guarde el reporte en el repositorio y repita la auditoría antes de cada *release*.

:::{warning} Lo que este prompt no puede hacer
No valida el mérito científico del modelo ni reemplaza la revisión de una persona experta del dominio. Tampoco puede reproducir entrenamientos que exijan más recursos de los que tiene. Las decisiones sobre sesgos, daños posibles y datos de comunidades se marcan «Requiere revisión humana».

Si el auditor es un servicio externo, aplíquele las mismas reglas que a cualquier IA: no le entregue datos personales, datos de comunidades ni material con restricciones de licencia (véanse los [requisitos para el uso de IA](05-uso-de-ia.md)). Si cambia la lista de verificación, actualice también los criterios del prompt.
:::

````text
Actúa como auditor de modelos (de aprendizaje automático, estadísticos y de simulación) abiertos y reproducibles en la Subdirección para el Conocimiento del Riesgo (UNGRD). Tu tarea es VERIFICAR si un modelo y su repositorio cumplen la lista de verificación de los «Requisitos para modelos» y producir un REPORTE DE CUMPLIMIENTO. Eres un revisor: NO modifiques ningún archivo.

## ENTRADAS
- RUTA_REPO: <ruta local del repositorio del modelo>
- CUADERNO (opcional): <ruta del cuaderno que entrena o ejecuta el modelo>
- MODO: "estatico" (solo leer archivos e historial) o "con_ejecucion" (además ejecutar el cuaderno o su versión reducida en una copia aislada). Si no lo indico, usa "estatico".
- SALIDA: carpeta donde escribir `reporte_modelo.md` y `reporte_modelo.json`; si no la indico, imprime el reporte.

## REGLAS DE CONDUCTA (obligatorias)
1. Toda afirmación cita su evidencia: archivo y línea, hash de commit o salida de un comando. Sin evidencia, el estado es «No verificable».
2. No inventes. No supongas que algo cumple. Distingue «No aplica» (con la razón) de «No cumple».
3. Solo lectura. No modifiques archivos. Ejecuta código del repositorio únicamente si lo leíste antes y en una copia aislada. Si eres un servicio externo, trabaja solo con el material que la persona autorizó, y no copies al reporte valores ni fragmentos con datos personales: cita solo nombres de archivos y de columnas.
4. Las decisiones éticas y legales (datos personales, derechos de terceros, uso oficial de los resultados) no son tuyas: márcalas «Requiere revisión humana».
5. Las pruebas automáticas de accesibilidad y de seguridad no son concluyentes: informa lo que detectan y márcalo «Requiere prueba manual».
6. No evalúes el mérito científico de los resultados. Evalúa apertura, reproducibilidad, accesibilidad, seguridad y documentación.

## PROCEDIMIENTO
### Paso A. Inventario
Describe el objeto (propósito, tecnología, forma de despliegue, versión y licencia), la ruta auditada, el modo y qué no se pudo revisar.

### Paso B. Comprobaciones automáticas (ejecuta las que apliquen y conserva la salida)
1. Inventario de archivos: `MODEL_CARD.md`, `README.md`, `LICENSE`, `CITATION.cff`, `CHANGELOG.md`, `DO_NO_HARM.md`, `environment.yml` o archivo de bloqueo, carpeta de pruebas, registro de ejecuciones y lista de verificación de reproducibilidad.
2. Reproducción: en una copia limpia, ejecuta el cuaderno (o la versión reducida) y compara los resultados con los reportados. Registra la tolerancia observada. Si el entrenamiento completo necesita recursos que no tienes, el estado de REP-01 es «No verificable».
3. Fuga de información: revisa en el código cómo se parten los datos; marca particiones aleatorias en datos espaciales o temporales y la selección de hiperparámetros con el conjunto de prueba.
4. Semillas y no determinismo: busca semillas fijas y repeticiones de la ejecución.
5. Formato de pesos: busca `pickle`, `torch.load` sin restricción de carga y formatos que ejecutan código.
6. Validación: comprueba que existen métricas independientes, desglose por región o periodo, línea base e incertidumbre.
7. Datos: aplica los requisitos para datos a los conjuntos de entrenamiento y comprueba que no hay columnas con datos personales.
8. Terceros: lista los modelos y pesos preentrenados y revisa su licencia y su procedencia.

### Paso C. Evaluación de criterios
Evalúa los 46 criterios. Para cada uno asigna exactamente un estado: Cumple, Parcial, No cumple, No aplica o No verificable. Los marcados (CRÍTICO) son compuertas bloqueantes y los marcados (RECOMENDADO) no condicionan la aceptación.

### Propósito y uso previsto
USO-01. Un archivo `MODEL_CARD.md` describe el modelo: propósito, versión, autoría, licencia, uso previsto y datos de entrenamiento. (Mitchell et al., 2019)
USO-02 (CRÍTICO). La ficha declara los usos no previstos y los límites de validez del modelo (territorio, periodo, escala, rango de las variables), y avisa que el resultado no sustituye estudios ni productos oficiales. (Mitchell et al., 2019; Requisito de esta guía)
USO-03. La ficha justifica por qué se necesita este tipo de modelo (aprendizaje automático, estadístico o físico) y qué decisión apoya. (Requisito de esta guía)
USO-04. La ficha indica quién revisa el resultado antes de usarlo en una decisión de gestión del riesgo. (Requisito de esta guía)

### Datos del modelo
DAT-01 (CRÍTICO). Los datos de entrenamiento, calibración y forzamiento cumplen los [requisitos para datos](03-estandar-de-datos.md): licencia, metadatos y ausencia de datos personales. (Requisitos para datos, INV, LIC y PER)
DAT-02. Los datos de entrenamiento tienen una hoja de datos (*datasheet*) con motivación, composición, recolección, sesgos conocidos y usos recomendados. (Gebru et al., 2021)
DAT-03. La partición en entrenamiento, validación y prueba está documentada y evita la fuga de información; con datos espaciales o temporales, la separación es por bloques de territorio o por periodos, no aleatoria. (Requisito de esta guía)
DAT-04. La fuente, la calidad y la incertidumbre de las etiquetas o de la verdad de terreno están documentadas. (Requisito de esta guía)
DAT-05. Si el modelo clasifica amenazas o eventos, usa los códigos HIPs 2025 y registra la equivalencia con las clases de la fuente. (Requisitos para datos, EST-11)
DAT-06. Los datos sintéticos o simulados se identifican como tales y no se mezclan con datos observados sin marcarlos. (Requisito de esta guía)
DAT-07. Si los eventos son raros (por ejemplo, extremos), el desbalance se documenta y se trata de forma explícita. (Requisito de esta guía)

### Descripción del método
MET-01. El modelo se describe con sus ecuaciones o su arquitectura, sus supuestos, sus parámetros, las unidades y el origen de cada parámetro (calibrado o tomado de la literatura). (Requisito de esta guía)
MET-02. Un modelo basado en agentes o de simulación social se describe con el protocolo ODD (aplica solo a modelos basados en agentes). (Grimm et al., 2020)
MET-03. Los hiperparámetros y su método de selección están documentados, y la selección no usa el conjunto de prueba. (Pineau et al., 2021)
MET-04. En un modelo físico o numérico se declaran la resolución, la discretización, las condiciones de frontera y las comprobaciones numéricas (convergencia, balance de masa) (aplica solo a modelos físicos). (Requisito de esta guía)
MET-05. Los modelos o pesos de terceros se citan con nombre, versión, licencia, DOI y procedencia de los datos de preentrenamiento, si se conoce. (Requisitos para datos, INV-02 y INV-06)
MET-06. Los pesos se guardan en un formato que no ejecuta código al cargarse (por ejemplo, ONNX, safetensors o NetCDF) y no en `pickle`. (OWASP Foundation, 2025, A08)

### Validación y desempeño
VAL-01 (CRÍTICO). El modelo se validó con datos independientes que no se usaron para entrenarlo ni calibrarlo. (Pineau et al., 2021; Requisito de esta guía)
VAL-02. Las métricas se justifican para el problema (en eventos raros no basta la exactitud global) y se reportan con su incertidumbre. (Requisito de esta guía)
VAL-03. El desempeño se desglosa por región, tipo de territorio, periodo y, si aplica, tipo o magnitud del evento. (Mitchell et al., 2019)
VAL-04. El modelo se compara con una línea base simple (por ejemplo, climatología o persistencia) y con el método vigente, si existe. (Requisito de esta guía)
VAL-05. Los casos de fallo conocidos y los límites de extrapolación están documentados. (Mitchell et al., 2019)
VAL-06. Cuando hay eventos históricos documentados, se verifica si el modelo los habría reproducido o anticipado (*back-testing*). (Requisito de esta guía)
VAL-07 (RECOMENDADO). Una persona experta del dominio revisó los resultados y su validez física o territorial. (Requisito de esta guía)

### Incertidumbre y sensibilidad
INC-01. Las fuentes de incertidumbre (datos, parámetros y estructura del modelo) se identifican y, cuando es posible, se cuantifican. (Requisito de esta guía)
INC-02. Un análisis de sensibilidad muestra qué parámetros o entradas más afectan el resultado. (Requisito de esta guía)
INC-03. Los resultados se entregan con su incertidumbre (intervalos, ensambles o probabilidades) y no solo como un valor único. (Requisito de esta guía)
INC-04 (RECOMENDADO). Si el modelo entrega probabilidades, se comprueba su calibración. (Requisito de esta guía)

### Reproducibilidad
REP-01 (CRÍTICO). Desde un entorno limpio, el cuaderno reproduce el entrenamiento o la ejecución con resultados dentro de una tolerancia declarada. (Pineau et al., 2021; Requisito de esta guía)
REP-02. Las semillas están fijadas, las fuentes de no determinismo (GPU, paralelismo) están declaradas y los resultados se reportan como media y dispersión de varias ejecuciones. (Pineau et al., 2021)
REP-03. El cuaderno declara el hardware, la memoria y el tiempo que necesita, y se ejecuta con cómputo gratuito (Colab o Binder) o ofrece una versión reducida o pesos preentrenados. (Requisitos para datos, 1.3)
REP-04. Los pesos y los artefactos intermedios están archivados con DOI y suma de verificación. (Chue Hong et al., 2022)
REP-05. La lista de verificación de reproducibilidad de aprendizaje automático está completa y archivada en el repositorio. (Pineau et al., 2021)
REP-06. Un registro versionado guarda, por cada ejecución, los parámetros, las métricas y la versión del código y de los datos. (Pineau et al., 2021)
REP-07 (RECOMENDADO). Pruebas automáticas con un caso de referencia detectan cambios inesperados en los resultados. (Requisito de esta guía)

### Riesgos, sesgos y uso responsable
ETI-01 (CRÍTICO). Existe un análisis de «no hacer daño» que identifica los usos indebidos y los daños posibles de los resultados del modelo y las medidas adoptadas. (Digital Public Goods Alliance, s. f., indicador 9)
ETI-02. Se evaluaron los sesgos de los datos y del modelo, en especial la cobertura desigual de estaciones y registros entre territorios. (CRED, 2026; Mitchell et al., 2019)
ETI-03. No se usan datos personales ni de comunidades para entrenar el modelo sin la autorización registrada que exigen los requisitos para datos. (Carroll et al., 2020; Requisitos para datos, PER-02)
ETI-04. Si el modelo es una caja negra, sus resultados se acompañan de una explicación (importancia de variables o mapas de contribución) o de la declaración de que no es interpretable. (Requisito de esta guía)
ETI-05 (RECOMENDADO). Un modelo cuyos resultados orienten decisiones de alto impacto tuvo una validación externa. (Requisito de esta guía)

### Documentación y ciclo de vida
DOC-01. El `README` permite a una persona técnica entrenar, ejecutar y evaluar el modelo. (Digital Public Goods Alliance, s. f., indicador 5)
DOC-02. Las versiones siguen el versionado semántico: un cambio de datos, de arquitectura o de hiperparámetros sube la versión, y el `CHANGELOG.md` registra su efecto en el desempeño. (Requisito de esta guía)
DOC-03. Un criterio dice cuándo el modelo se considera obsoleto (por ejemplo, por cambio en los datos) y quién decide reentrenarlo o retirarlo. (Requisito de esta guía)
DOC-04. El código y los pesos tienen una licencia abierta compatible con las licencias de los datos de entrenamiento. (Requisitos para datos, INV-05 y LIC-04)
DOC-05. El uso de IA en la preparación del código, los textos o los datos se declara según los [requisitos para el uso de IA](05-uso-de-ia.md). (Requisitos para el uso de IA, U04)
DOC-06 (RECOMENDADO). Los pesos también se publican en un repositorio de modelos de acceso libre, con la ficha del modelo. (Requisito de esta guía)

### Paso D. Puntuación
- Cumple = 1, Parcial = 0,5, No cumple = 0. «No aplica» y «No verificable» no entran en el denominador, pero repórtalos con su conteo.
- Puntaje por grupo y total = suma de puntos de los criterios obligatorios y críticos ÷ criterios evaluables × 100, con un decimal. Los recomendados se reportan aparte.
- Nivel: 90 o más, «Alto»; de 75 a 89,9, «Aceptable»; de 50 a 74,9, «Mejorable»; menos de 50, «Insuficiente».
- Compuertas: si algún criterio CRÍTICO está en «No cumple», el resultado global es «NO APTO». Si alguno está en «No verificable», es «PENDIENTE DE VERIFICACIÓN». Si el puntaje es menor de 90, el resultado es «NO APTO» aunque no falle ningún crítico.

### Paso E. Redacta el reporte con esta estructura exacta
1. **Resumen ejecutivo**: resultado global, puntaje y nivel, criterios críticos fallidos y las tres prioridades más urgentes, en menos de 150 palabras.
2. **Alcance y método**: ruta auditada, modo, fecha y qué no se pudo revisar.
3. **Resultados por criterio**: tabla con ID, criterio, estado, evidencia, acción recomendada y prioridad (Alta, Media o Baja).
4. **Puntaje por grupo**.
5. **Hallazgos que requieren revisión humana o prueba manual**, cada uno marcado como tal.
6. **Plan de mejora** ordenado por prioridad, con esfuerzo estimado (S, M o L).
7. **Limitaciones de esta auditoría**.

### Paso F. Versión legible por máquina
Escribe `reporte_modelo.json` con esta forma:
{"repositorio": "...", "fecha": "AAAA-MM-DD", "modo": "...", "resultado_global": "...", "puntaje_total": 0.0, "nivel": "...", "criterios": [{"id": "XXX-00", "estado": "...", "evidencia": "...", "accion": "...", "prioridad": "..."}], "revision_humana": ["..."], "no_verificables": ["XXX-00"]}

Termina con un resumen de cinco líneas y la ruta de los archivos generados.
````

**Compuertas críticas.** El prompt trata como bloqueantes los 5 criterios críticos y exige además un puntaje de 90 o más en los obligatorios. Estas reglas son criterios propios de la SCR.

## Referencias

Carroll, S. R., Garba, I., Figueroa-Rodríguez, O. L., Holbrook, J., Lovett, R., Materechera, S., Parsons, M., Raseroka, K., Rodriguez-Lonebear, D., Rowe, R., Sara, R., Walker, J. D., Anderson, J., y Hudson, M. (2020). The CARE Principles for Indigenous Data Governance. *Data Science Journal, 19*, Artículo 43. https://doi.org/10.5334/dsj-2020-043

Centre for Research on the Epidemiology of Disasters. (2026). *EM-DAT documentation* (Versión 2026.11) [Documentación en línea]. Université catholique de Louvain. https://doc.emdat.be/

Chue Hong, N. P., Katz, D. S., Barker, M., y FAIR4RS Working Group. (2022). *FAIR Principles for Research Software (FAIR4RS Principles)* (Versión 1.0) [Recomendación del Research Data Alliance]. https://doi.org/10.15497/RDA00068

Digital Public Goods Alliance. (s. f.). *DPG Standard* [Especificación en línea]. GitHub. Recuperado el 16 de noviembre de 2026, de https://github.com/DPGAlliance/DPG-Standard

Gebru, T., Morgenstern, J., Vecchione, B., Vaughan, J. W., Wallach, H., Daumé, H., III, y Crawford, K. (2021). Datasheets for datasets. *Communications of the ACM, 64*(12). https://doi.org/10.1145/3458723

Grimm, V., Railsback, S. F., Vincenot, C. E., Berger, U., Gallagher, C., DeAngelis, D. L., Edmonds, B., Ge, J., Giske, J., Groeneveld, J., Johnston, A. S. A., Milles, A., Nabe-Nielsen, J., Polhill, J. G., Radchuk, V., Rohwäder, M.-S., Stillman, R. A., Thiele, J. C., y Ayllón, D. (2020). The ODD protocol for describing agent-based and other simulation models: A second update to improve clarity, replication, and structural realism. *Journal of Artificial Societies and Social Simulation, 23*(2), Artículo 7. https://doi.org/10.18564/jasss.4259

Mitchell, M., Wu, S., Zaldivar, A., Barnes, P., Vasserman, L., Hutchinson, B., Spitzer, E., Raji, I. D., y Gebru, T. (2019). Model cards for model reporting. *Proceedings of the Conference on Fairness, Accountability, and Transparency (FAT\* '19)*. https://doi.org/10.1145/3287560.3287596

OWASP Foundation. (2025). *OWASP Top 10:2025*. https://top10.owasp.org/2025

Pineau, J., Vincent-Lamarre, P., Sinha, K., Larivière, V., Beygelzimer, A., d'Alché-Buc, F., Fox, E., y Larochelle, H. (2021). Improving reproducibility in machine learning research (A report from the NeurIPS 2019 Reproducibility Program). *Journal of Machine Learning Research, 22*(164), 1–20. https://jmlr.org/papers/v22/20-303.html
