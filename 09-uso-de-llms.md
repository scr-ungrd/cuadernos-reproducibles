---
title: Requisitos para el uso de LLMs
subtitle: Requisitos para usar modelos de lenguaje y otros modelos preentrenados de repositorios como Hugging Face dentro de un cuaderno reproducible
date: 2026-11-19
authors:
  - name: Subdirección para el Conocimiento del Riesgo
    affiliation: Unidad Nacional para la Gestión del Riesgo de Desastres (UNGRD)
    github: scr-ungrd
site:
  hide_authors: true
license: CC-BY-4.0
keywords:
  - modelos de lenguaje
  - LLM
  - Hugging Face
  - modelos preentrenados
  - cadena de suministro
  - reproducibilidad
  - ciencia abierta
  - riesgo de desastres
abbreviations:
  UNGRD: Unidad Nacional para la Gestión del Riesgo de Desastres
  SCR: Subdirección para el Conocimiento del Riesgo
  LLM: modelo de lenguaje de gran escala
  API: interfaz de programación de aplicaciones
  DOI: Digital Object Identifier
  JSON: JavaScript Object Notation
  NIST: National Institute of Standards and Technology
  OWASP: Open Worldwide Application Security Project
  MOF: Model Openness Framework
  MCP: Model Context Protocol
---


## 1. Alcance y convenciones

### 1.1 Alcance

Estas instrucciones se aplican a todo **modelo preentrenado de terceros** que un cuaderno de la colección descargue o llame para producir un resultado: un modelo de lenguaje que clasifica, extrae o resume texto, un modelo de incrustaciones que busca documentos, un modelo de visión que detecta objetos en imágenes, o un modelo de voz que transcribe audio. Incluye los pesos que se descargan de un repositorio como Hugging Face y se ejecutan localmente, los modelos a los que se accede por una API alojada y los modelos que actúan como agentes o que usan herramientas, conectores o servidores del Model Context Protocol (MCP).

Estos requisitos existen porque un modelo preentrenado es un componente que quien escribe el cuaderno no construyó ni puede inspeccionar por completo. Sus pesos pueden cambiar sin aviso, su licencia puede limitar el uso, su carga puede ejecutar código y sus salidas pueden variar entre ejecuciones. Ninguno de los demás requisitos de la colección audita estos riesgos de forma completa.

Se distinguen cinco objetos relacionados:

- **Cuaderno**: documenta un análisis y es la fuente del método. Se rige por la [guía](01-cuadernos-de-conocimiento.md).
- **Asistente de IA**: herramienta que usa la persona autora para escribir, programar o traducir, incluidos los asistentes en modo agente con conectores o servidores MCP. Se rige por los [requisitos para el uso de IA](05-uso-de-ia.md).
- **Modelo propio**: el que la persona autora entrena, calibra o ejecuta para estimar amenaza, exposición, vulnerabilidad o riesgo. Se rige por los [requisitos para modelos](08-estandar-modelos.md).
- **Modelo de terceros usado como componente**: el que el cuaderno llama para procesar datos o texto. Se rige por este documento.
- **Tablero y aplicación**: muestran o ejecutan resultados. Se rigen por los requisitos para [tableros](06-estandar-tableros.md) y para [aplicaciones](07-estandar-aplicaciones.md).

La diferencia con los requisitos para el uso de IA es el objeto auditado. Aquellos requisitos responden a quién responde por el trabajo cuando una persona se apoya en un asistente. Estos responden a si el modelo que forma parte de la cadena de cálculo es identificable, seguro, legal, reproducible y válido para la tarea. Un mismo cuaderno puede estar sujeto a ambos: por ejemplo, el que usa Claude para escribir el código (requisitos para el uso de IA) y un modelo de Hugging Face para clasificar noticias (estos requisitos).

La frontera para los agentes es dónde corren: si el agente ayuda a quien escribe el cuaderno, se declara según los requisitos para el uso de IA; si el agente o el servidor MCP forma parte de la cadena de cálculo del cuaderno y se ejecuta cada vez que alguien lo reproduce, aplican estos requisitos. Si el cuaderno ajusta o entrena el modelo, aplica también los [requisitos para modelos](08-estandar-modelos.md). Un cuaderno que usa un modelo preentrenado solo para tareas de apoyo que no entran en los resultados (por ejemplo, formatear una tabla) no necesita aplicar estos requisitos y lo declara según los requisitos para el uso de IA. La seguridad común a todo repositorio (secretos, datos personales y rutas locales, código no confiable, dependencias y *releases*) la cubren los [requisitos de seguridad](10-requisitos-seguridad.md); los requisitos de seguridad de este documento (SEG) tratan lo específico de los modelos de terceros.

### 1.2 Convenciones

1. **Identificador.** Cada requisito tiene un código de tres letras y dos cifras (por ejemplo, IDE-02). Los códigos se usan en la lista de verificación, en el prompt de validación y en los reportes.
2. **Nivel.** *Obligatorio* significa que el cuaderno no se acepta si el requisito aplica y no se cumple. *Recomendado* significa que el cumplimiento mejora la calidad pero no condiciona la aceptación. *Crítico* es un requisito obligatorio cuyo incumplimiento bloquea la publicación, cualquiera sea la puntuación total.
3. **Base.** Entre paréntesis, cada requisito indica el documento, el año y, cuando corresponde, el criterio o el apartado del que procede. Los requisitos cuya base es «Requisito de esta guía» los establece este documento y no provienen de una fuente externa.
4. **Redacción.** Cada requisito se enuncia en el estado conforme: describe cómo es un cuaderno que lo cumple. Los requisitos que dicen «aplica solo» se marcan «No aplica» cuando no corresponden.
5. **Citas y traducciones.** Las citas siguen la norma APA 7. Los textos de las fuentes en inglés se traducen al español; las traducciones son propias. Los nombres de parámetros, campos y códigos se conservan en su idioma original.
6. **Fecha de consulta.** Las fuentes web sin fecha de publicación se consultaron el 19 de noviembre de 2026 (véanse las Referencias). Las plataformas, las bibliotecas y las guías cambian: antes de publicar, confirme la versión vigente.
7. **Uso del término «LLM».** Se usa por brevedad, pero los requisitos valen para cualquier modelo preentrenado de terceros, salvo que el texto indique lo contrario.

### 1.3 Política de costo cero

Ningún requisito de este documento exige comprar suscripciones, licencias, créditos de API ni cómputo. Un cuaderno que dependa de una API de pago o de un modelo que no cabe en cómputo gratuito ofrece un modelo más pequeño o las salidas guardadas, de modo que cualquier persona pueda reproducir los resultados sin pagar (EJE-01 y EJE-03).

### 1.4 Documentos de referencia

**Tabla 1.** Documentos de los que se derivan los requisitos.

```{list-table}
:header-rows: 1

* - Documento
  - Qué establece
  - Requisitos que se derivan
* - Mitchell et al. (2019). Model cards; Gebru et al. (2021). Datasheets for datasets
  - Formatos para documentar el uso previsto, las limitaciones, los datos y el desempeño de un modelo y de sus datos
  - IDE-03, EVA-05, SES-02, DOC-01
* - Hugging Face (s. f.-a, s. f.-b, s. f.-c). Documentación del Hub y de Transformers
  - Metadatos de la ficha (licencia, modelo base, datos), riesgos de `pickle` y de `trust_remote_code`, y revisión como rama, etiqueta o *commit*
  - IDE-02, IDE-04, TER-01, SEG-01, SEG-02, SEG-03
* - OWASP Foundation (2025). OWASP Top 10 para aplicaciones con LLM
  - Riesgos de seguridad: inyección de prompts, divulgación de información, cadena de suministro, manejo de salidas, agencia excesiva y desinformación
  - SEG-02, SEG-04, SEG-06, SEG-07, SEG-08, PRO-03, PRI-01, PRI-03, EVA-06
* - National Institute of Standards and Technology (2024). Perfil de IA generativa (NIST AI 600-1)
  - Riesgos propios de la IA generativa, entre ellos la confabulación
  - EVA-06
* - Model Context Protocol (s. f.-a, s. f.-b). Especificación y guía de seguridad
  - Las herramientas equivalen a ejecución arbitraria de código, las descripciones de herramientas no son confiables si el servidor no lo es, los servidores locales corren con los privilegios del cliente y los permisos deben ser mínimos
  - SEG-07, SEG-08, EJE-06
* - White et al. (2024). Model Openness Framework
  - Clasificación de la completitud y la apertura de un modelo
  - IDE-06
* - Pineau et al. (2021); Chue Hong et al. (2022); Digital Public Goods Alliance (s. f.); Carroll et al. (2020); CRED (2026)
  - Reproducibilidad, software de investigación, no hacer daño, gobernanza de datos de comunidades y sesgos de reporte
  - EJE-04, EJE-07, SES-01, PRI-01, SES-02
* - [Requisitos para datos](03-estandar-de-datos.md), [requisitos para el uso de IA](05-uso-de-ia.md) y [requisitos para modelos](08-estandar-modelos.md)
  - Licencias, costo cero, datos derivados con modelos de lenguaje, declaración de IA y validación que estos requisitos heredan
  - IDE-05, TER-04, TER-05, EJE-01, EJE-03, EVA-01, PRI-04, DOC-03 a DOC-05
```

## 2. Requisitos

### 2.1 Identificación y procedencia

«Usamos un modelo de Hugging Face» no identifica nada: el contenido de un repositorio cambia. El parámetro `revision` de `from_pretrained` acepta una rama, una etiqueta o un identificador de *commit*, y por defecto es `main` (Hugging Face, s. f.-a). Una rama se mueve, así que dos ejecuciones con meses de diferencia pueden cargar pesos distintos sin que el código cambie. Fije el *hash* del *commit*.

:::{important} IDE-02: la revisión inmutable es obligatoria
Si el cuaderno no fija la revisión, nadie puede saber qué modelo produjo los resultados. En una API alojada, que no expone un *hash*, registre el nombre del modelo con su fecha de versión y la fecha de consulta (EJE-05).
:::

La ficha del modelo (*model card*) del repositorio reúne el uso previsto, las limitaciones, los datos de entrenamiento y los resultados de evaluación (Hugging Face, s. f.-b; Mitchell et al., 2019). Archive una copia fechada, porque el autor del modelo puede editarla. Si el modelo es un derivado (ajuste fino, adaptador, cuantización o fusión), el campo `base_model` de la ficha identifica el modelo de origen (Hugging Face, s. f.-b); cítelo también.

*Requisitos de este grupo: IDE-01, IDE-02, IDE-03, IDE-04, IDE-05, IDE-06. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.2 Licencia y términos

La ficha del modelo declara su licencia en los metadatos, y cuando es una licencia propia usa `license: other` con el nombre y el enlace (Hugging Face, s. f.-b). Muchas licencias de modelos no son licencias abiertas en el sentido de la [OSI](https://opensource.org/): pueden prohibir usos, limitar el tamaño de la organización o exigir aceptar condiciones antes de descargar. Lea el texto, no la etiqueta.

Hay tres preguntas que el cuaderno debe poder responder. ¿La licencia permite el uso institucional de la UNGRD y la publicación de resultados? ¿Permite redistribuir los pesos o solo usarlos? ¿Impone condiciones sobre las salidas? Si la respuesta a la primera es no o no se sabe, el cuaderno no se publica (TER-01).

*Requisitos de este grupo: TER-01, TER-02, TER-03, TER-04, TER-05. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.3 Seguridad de la cadena de suministro

Cargar un modelo es ejecutar código de terceros. Hay tres vías. La primera es el formato de los pesos: `pickle` puede ejecutar código arbitrario al deserializarse, y el Hub lo advierte y muestra las importaciones de los archivos, aunque aclara que su análisis no es infalible y que la verificación es responsabilidad de quien carga el modelo (Hugging Face, s. f.-c). Prefiera `safetensors`. La segunda es `trust_remote_code`: cuando es verdadero, ejecuta en su equipo el código que está en el repositorio del modelo, y solo debe activarse en repositorios de confianza cuyo código haya leído (Hugging Face, s. f.-a). La tercera son las dependencias.

La lista OWASP Top 10 para aplicaciones con LLM incluye la cadena de suministro, la inyección de prompts, el manejo inadecuado de las salidas y la agencia excesiva (OWASP Foundation, 2025). En un cuaderno de análisis los dos últimos importan más de lo que parece: si el modelo lee noticias o documentos de terceros, el texto puede contener instrucciones que desvíen su comportamiento, y por eso su salida nunca se ejecuta como código ni se usa sin validar (SEG-06 y PRO-03).

Si el cuaderno usa conectores o servidores del Model Context Protocol (MCP), hay que tratarlos como código de terceros. La especificación indica que las herramientas representan ejecución arbitraria de código, que sus descripciones deben considerarse no confiables si el servidor no lo es, y que un servidor local corre con los mismos privilegios que el cliente (Model Context Protocol, s. f.-a, s. f.-b). Fije la versión del servidor, lea el comando que lo inicia, dele los permisos mínimos y registre sus llamadas (SEG-08 y EJE-06).

:::{important} SEG-01: no se ejecuta código remoto sin leerlo
`trust_remote_code=True` entrega el control de su equipo al repositorio del modelo. Si el modelo lo exige, lea los archivos de código de esa revisión, fíjela y declárelo.
:::

*Requisitos de este grupo: SEG-01, SEG-02, SEG-03, SEG-04, SEG-05, SEG-06, SEG-07, SEG-08. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.4 Ejecución y reproducibilidad

Un modelo generativo no siempre devuelve lo mismo: la temperatura, la semilla, la cuantización, la GPU y la versión de la biblioteca cambian la salida. Por eso la reproducibilidad de un cuaderno con LLM no se apoya en volver a llamar al modelo sino en **guardar las salidas en bruto** con su entrada, parámetros, fecha y revisión (EJE-03), y en hacer que las tablas y figuras se calculen desde ellas. Es la misma regla de los requisitos para el uso de IA para datos derivados con modelos de lenguaje. La repetición de la llamada es una verificación adicional, no la fuente de los resultados. Lo mismo vale para las herramientas y los servidores MCP: registre cada llamada con su resultado y reproduzca desde el registro (EJE-06).

Si el cuaderno usa una API alojada, el proveedor puede cambiar el modelo o retirarlo. Guarde las salidas y la fecha de consulta para que el cuaderno siga siendo útil cuando el servicio cambie (EJE-05).

*Requisitos de este grupo: EJE-01, EJE-02, EJE-03, EJE-04, EJE-05, EJE-06, EJE-07. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.5 Prompts y configuración

El prompt es parte del método, tanto como un parámetro o una ecuación. Debe estar versionado en el repositorio, documentado y probado. Pida salidas en un formato verificable, como JSON con un esquema o una lista cerrada de categorías, y valide cada respuesta: así una salida mal formada se rechaza y se cuenta, en vez de pasar inadvertida a los resultados (PRO-03).

*Requisitos de este grupo: PRO-01, PRO-02, PRO-03, PRO-04, PRO-05. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.6 Evaluación

Que un modelo tenga buenas cifras en una prueba comparativa no dice cómo se comporta con noticias en español sobre una inundación en el Chocó. La evaluación se hace en la tarea concreta, con una muestra de referencia que revisan personas expertas y que no se usó para escribir el prompt ni para ajustar el modelo (EVA-01). Compare con una línea base simple: si unas reglas o un diccionario hacen lo mismo, no se justifica el LLM (EVA-03).

Los modelos generativos producen contenido plausible pero falso, lo que el perfil de IA generativa del NIST llama confabulación (National Institute of Standards and Technology, 2024) y OWASP incluye como desinformación (OWASP Foundation, 2025). Documente los errores, no solo el promedio de aciertos (EVA-06).

:::{important} EVA-01: sin muestra de referencia no hay resultado
Los datos construidos con un modelo de lenguaje son datos derivados con riesgo de error. Revise a mano una muestra, publique la tasa de error y los casos que fallaron antes de usar los resultados.
:::

*Requisitos de este grupo: EVA-01, EVA-02, EVA-03, EVA-04, EVA-05, EVA-06, EVA-07. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.7 Privacidad y datos

Hay dos formas de usar un modelo y tienen riesgos distintos. Con **pesos locales**, los datos no salen de su equipo. Con una **API alojada** (incluidos los proveedores de inferencia y los Spaces de un repositorio de modelos), cada prompt viaja a un tercero que puede conservarlo o usarlo para entrenar. Por eso los datos personales, los de comunidades, los no publicados y los que tienen restricciones de licencia solo se procesan con modelos locales (PRI-01; Carroll et al., 2020). Revise también los términos del servicio (PRI-02).

*Requisitos de este grupo: PRI-01, PRI-02, PRI-03, PRI-04. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.8 Riesgos, sesgos y uso responsable

Los modelos de lenguaje aprenden de textos en los que unas regiones, idiomas y tipos de fuente pesan más que otros, y heredan los sesgos de reporte que tienen los registros de desastres (CRED, 2026). Evalúe y declare cómo cambia el desempeño con el español de Colombia y con los territorios con menos cobertura de prensa (SES-02). El análisis de no hacer daño (SES-01) sigue el Digital Public Goods Standard y usa la plantilla `DO_NO_HARM.md` de los [requisitos para aplicaciones](07-estandar-aplicaciones.md).

*Requisitos de este grupo: SES-01, SES-02, SES-03, SES-04, SES-05. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.9 Documentación y ciclo de vida

La ficha de uso (`LLM_USE.md`) reúne en un solo archivo lo que otra persona necesita para saber qué modelos usa el cuaderno y bajo qué condiciones. Es el equivalente, para un modelo de terceros, de la ficha `MODEL_CARD.md` de los requisitos para modelos.

Use esta plantilla (`LLM_USE.md`), con una entrada por modelo:

```markdown
# Ficha de uso de modelos de terceros

## Modelo 1: <nombre>

- **Identificador y repositorio:** <organización/nombre>, <enlace>
- **Revisión fijada:** <hash del commit> (o <versión con fecha> si es una API)
- **Acceso:** <pesos locales | API alojada de <proveedor>>
- **Tarea en el cuaderno:** <qué hace y en qué notebooks>
- **Licencia y condiciones:** <identificador o enlace; restricciones; acceso restringido sí/no>
- **Modelo base y apertura:** <base_model; nivel del Model Openness Framework si se conoce>
- **Formato de pesos y código remoto:** <safetensors | otro>; trust_remote_code = <falso | verdadero y revisado>
- **Parámetros de generación:** <temperatura, top_p, máximo de tokens, semilla, cuantización>
- **Prompts:** <ruta en el repositorio>
- **Salidas en bruto:** <ruta; el cuaderno se reproduce desde ellas sí/no>
- **Evaluación:** <muestra, tamaño, métricas con incertidumbre, línea base>
- **Errores y sesgos conocidos:** <resumen y enlace al análisis>
- **Datos enviados a servicios de terceros:** <ninguno | solo texto público | ...>
- **Responsable de revisar los resultados:** <persona o dependencia>
- **Hardware y tiempo de ejecución:** <...>
```

*Requisitos de este grupo: DOC-01, DOC-02, DOC-03, DOC-04, DOC-05, DOC-06. Su enunciado completo está en la lista de verificación de la Sección 3.*

## 3. Lista de verificación

La lista tiene 53 requisitos: 47 obligatorios y 6 recomendados. Los 5 requisitos **críticos** (IDE-02, TER-01, SEG-01, EVA-01 y PRI-01) bloquean la publicación si no se cumplen.

**Criterio de aceptación.** Un cuaderno cumple los requisitos si (1) ningún requisito crítico está en incumplimiento y (2) el puntaje de requisitos obligatorios es de 90 o más, calculado como se indica en el prompt de la Sección 4.

**2.1. Identificación y procedencia**

- [ ] **IDE-01.** Cada modelo se identifica con su identificador completo en el repositorio de origen (organización y nombre), la tarea para la que se usa y la forma de acceso: pesos descargados que se ejecutan localmente o API alojada. (Requisito de esta guía)
- [ ] **IDE-02.** **Crítico.** Cada modelo está fijado a una revisión inmutable (el *hash* de un *commit*), no a una rama como `main` ni a una etiqueta que pueda moverse; en una API alojada, a la versión del modelo con su fecha. (Hugging Face, s. f.-a; Requisito de esta guía)
- [ ] **IDE-03.** La ficha del modelo (*model card*) del repositorio de origen se leyó y se archivó una copia fechada en el repositorio del cuaderno; resume el uso previsto, las limitaciones y los datos de entrenamiento que declara el modelo, o indica que no los declara. (Mitchell et al., 2019; Gebru et al., 2021; Hugging Face, s. f.-b)
- [ ] **IDE-04.** Si el modelo es un derivado (ajuste fino, adaptador, cuantización o fusión), se identifican el modelo base y el tipo de relación. (Hugging Face, s. f.-b)
- [ ] **IDE-05.** Cada modelo se cita en las referencias con autoría o entidad, año, versión, enlace y DOI cuando exista. (Requisitos para datos, INV-02)
- [ ] **IDE-06.** *(Recomendado)* Se indica el grado de apertura del modelo (solo pesos, o también código de entrenamiento y datos) con el Model Openness Framework. (White et al., 2024)

**2.2. Licencia y términos**

- [ ] **TER-01.** **Crítico.** La licencia del modelo permite el uso previsto (investigación, uso institucional, publicación de resultados y de derivados) y está registrada con su identificador o su texto. (Hugging Face, s. f.-b; Requisito de esta guía)
- [ ] **TER-02.** Si el modelo es de acceso restringido o exige aceptar condiciones, las aceptó una persona con autoridad para hacerlo, y el cuaderno explica cómo obtener el acceso sin publicar credenciales ni pesos que la licencia no permita redistribuir. (Requisito de esta guía)
- [ ] **TER-03.** Las restricciones de uso de la licencia (usos prohibidos, uso no comercial, límites por tamaño de la organización) se revisaron frente al uso institucional y a la publicación abierta del cuaderno. (Requisito de esta guía)
- [ ] **TER-04.** Las condiciones de los datos de entrenamiento que declara el modelo se revisaron; si no las declara, queda registrado como limitación. (Gebru et al., 2021; Requisitos para datos, INV-05)
- [ ] **TER-05.** Las salidas del modelo se publican bajo una licencia compatible con los términos del modelo o del proveedor de la API. (Requisitos para el uso de IA, U21)

**2.3. Seguridad de la cadena de suministro**

- [ ] **SEG-01.** **Crítico.** El cuaderno no ejecuta código remoto del repositorio del modelo sin revisarlo: `trust_remote_code` es falso, o se activa solo después de leer ese código y de fijar la revisión. (Hugging Face, s. f.-a)
- [ ] **SEG-02.** Los pesos se cargan en un formato que no ejecuta código al cargarse (`safetensors` u ONNX). Si solo existe un archivo `pickle`, se verifica el origen y se documenta el riesgo. (Hugging Face, s. f.-c; OWASP Foundation, 2025, LLM03)
- [ ] **SEG-03.** El origen del modelo es una organización o persona verificable, y el cuaderno registra la suma de verificación o el *hash* de la revisión de los archivos descargados. (Hugging Face, s. f.-c; Requisito de esta guía)
- [ ] **SEG-04.** Las bibliotecas que cargan y ejecutan el modelo (`transformers`, `tokenizers`, `huggingface_hub` y similares) tienen versión fijada en `environment.yml`, y el cuaderno no instala paquetes desde fuentes sin versión. (OWASP Foundation, 2025, LLM03)
- [ ] **SEG-05.** Los tokens y las claves de API se leen de variables de entorno o de secretos, y no aparecen en el cuaderno, en las salidas guardadas ni en el historial de git. (Requisito de esta guía)
- [ ] **SEG-06.** Si el modelo recibe texto de fuentes externas (noticias, páginas web, documentos de terceros), ese texto se trata como no confiable: la salida del modelo no se ejecuta como código ni dispara acciones sin revisión. (OWASP Foundation, 2025, LLM01 y LLM05)
- [ ] **SEG-07.** Si el modelo actúa como agente con herramientas (ejecuta código, consulta bases de datos, escribe archivos), sus permisos son mínimos, corre en un entorno aislado y toda acción irreversible requiere aprobación humana (aplica solo a agentes). (OWASP Foundation, 2025, LLM06)
- [ ] **SEG-08.** Si el cuaderno usa conectores o servidores MCP, estos son de origen verificable, tienen la versión fijada y corren con los privilegios mínimos; el texto que devuelven y las descripciones de sus herramientas se tratan como no confiables (aplica solo si el cuaderno usa MCP). (MCP, s. f.-a, s. f.-b; OWASP Foundation, 2025, LLM01 y LLM03)

**2.4. Ejecución y reproducibilidad**

- [ ] **EJE-01.** El cuaderno declara el hardware, la memoria y el tiempo que necesita, y se ejecuta con cómputo gratuito (Colab o Binder) o ofrece un modelo más pequeño o una versión reducida. (Requisitos para modelos, REP-03)
- [ ] **EJE-02.** Los parámetros de generación (temperatura, `top_p`, máximo de tokens, semilla, cuantización y precisión numérica) están fijados y registrados; si la tarea lo permite, la decodificación es determinista. (Requisito de esta guía)
- [ ] **EJE-03.** Las salidas en bruto que alimentan resultados se guardan junto con su entrada, los parámetros, la fecha y la revisión del modelo, y los resultados se reproducen desde esas salidas, sin una nueva llamada al modelo. (Requisitos para el uso de IA, U12)
- [ ] **EJE-04.** El cuaderno declara las fuentes de no determinismo (GPU, versión de las bibliotecas, tamaño del lote) y reporta la variación de varias ejecuciones o demuestra que las salidas guardadas bastan para reproducir los resultados. (Pineau et al., 2021)
- [ ] **EJE-05.** Si usa una API alojada, el cuaderno archiva las salidas y la fecha de consulta, y no queda inutilizable si el proveedor cambia o retira el modelo. (Requisito de esta guía)
- [ ] **EJE-06.** Si el modelo usa herramientas o servidores MCP, cada llamada (herramienta, argumentos, resultado y fecha) se registra, y los resultados se reproducen desde ese registro y no desde una nueva llamada (aplica solo si hay herramientas o MCP). (Requisitos para el uso de IA, U26; Requisito de esta guía)
- [ ] **EJE-07.** *(Recomendado)* El modelo y el tokenizador se archivan con DOI y suma de verificación cuando la licencia lo permite, o el cuaderno documenta cómo recuperar la revisión exacta. (Chue Hong et al., 2022)

**2.5. Prompts y configuración**

- [ ] **PRO-01.** Los prompts (instrucciones del sistema, plantillas, ejemplos y esquemas de salida) están en archivos versionados del repositorio, no solo escritos en celdas sueltas. (Requisito de esta guía)
- [ ] **PRO-02.** Cada prompt documenta su objetivo, sus variables de entrada y el formato de salida esperado, y sus cambios se registran en el `CHANGELOG.md`. (Requisito de esta guía)
- [ ] **PRO-03.** La salida del modelo se restringe a un formato verificable (JSON con esquema u opciones cerradas), y el cuaderno valida cada salida y registra las que rechaza. (OWASP Foundation, 2025, LLM05)
- [ ] **PRO-04.** Los prompts no contienen datos personales, credenciales ni datos con restricciones de licencia. (Requisitos para el uso de IA, U20)
- [ ] **PRO-05.** *(Recomendado)* El cuaderno prueba la sensibilidad de los resultados a variaciones del prompt (parafraseos, orden de los ejemplos) y reporta cuánto cambian. (Requisito de esta guía)

**2.6. Evaluación**

- [ ] **EVA-01.** **Crítico.** Una muestra de referencia etiquetada por personas expertas, separada de los ejemplos del prompt y de cualquier ajuste, valida la salida del modelo para la tarea concreta antes de usar los resultados. (Requisitos para el uso de IA, U11; Requisitos para modelos, VAL-01)
- [ ] **EVA-02.** Las métricas se justifican para la tarea y se reportan con su incertidumbre, junto con el tamaño de la muestra y el acuerdo entre las personas que la etiquetaron. (Requisitos para modelos, VAL-02)
- [ ] **EVA-03.** El desempeño se compara con una línea base sin modelo de lenguaje (reglas, diccionarios, expresiones regulares o un clasificador sencillo), y se justifica por qué se necesita un LLM. (Requisitos para modelos, VAL-04)
- [ ] **EVA-04.** La evaluación usa textos del dominio y del idioma de uso (español de Colombia, topónimos locales, términos de gestión del riesgo), no solo las pruebas genéricas del repositorio de origen. (Requisito de esta guía)
- [ ] **EVA-05.** Las cifras de desempeño que publica el modelo (pruebas comparativas y tablas de clasificación) se tratan como referencia y no como evidencia de su desempeño en esta tarea; se considera la posible contaminación de las pruebas con datos de entrenamiento. (Mitchell et al., 2019; Requisito de esta guía)
- [ ] **EVA-06.** Se documentan los errores frecuentes, incluidas las confabulaciones (contenido plausible pero falso), con la tasa de error por categoría y ejemplos de los casos que fallaron. (NIST, 2024; OWASP Foundation, 2025, LLM09)
- [ ] **EVA-07.** *(Recomendado)* Se mide la consistencia (la misma entrada en varias ejecuciones) y, si el modelo reporta confianza, su calibración. (Requisitos para modelos, INC-04)

**2.7. Privacidad y datos**

- [ ] **PRI-01.** **Crítico.** No se envían datos personales, de comunidades, no publicados ni con restricciones de licencia a un servicio alojado de terceros (API, proveedores de inferencia o Spaces); esos datos solo se procesan con modelos que se ejecutan localmente. (Carroll et al., 2020; OWASP Foundation, 2025, LLM02; Requisitos para el uso de IA, U20)
- [ ] **PRI-02.** Para cada servicio alojado se documenta qué datos recibe, quién lo opera y en qué país, y se revisaron sus términos sobre retención de datos y entrenamiento. (Requisitos para el uso de IA, U21)
- [ ] **PRI-03.** Las salidas se revisan antes de publicarlas para comprobar que no reproducen datos personales ni texto con derechos de terceros. (OWASP Foundation, 2025, LLM02)
- [ ] **PRI-04.** Lo que el cuaderno publique en un repositorio de modelos o de datos (modelos ajustados, conjuntos derivados, Spaces) cumple los requisitos para datos y no incluye datos de comunidades sin autorización registrada. (Carroll et al., 2020; Requisitos para datos, PER-02)

**2.8. Riesgos, sesgos y uso responsable**

- [ ] **SES-01.** Existe un análisis de «no hacer daño» del uso del modelo de lenguaje: usos indebidos, errores con consecuencias y medidas adoptadas (`DO_NO_HARM.md`). (Digital Public Goods Alliance, s. f., indicador 9)
- [ ] **SES-02.** Se evaluaron y se declaran los sesgos del modelo y de su fuente: geográficos (más texto de unas regiones que de otras), de idioma y de tipo de fuente. (CRED, 2026; Mitchell et al., 2019)
- [ ] **SES-03.** Ninguna decisión de gestión del riesgo (alerta, priorización, mapa) depende solo de la salida del modelo; una persona experta la revisa. (Requisitos para el uso de IA, recomendación 4)
- [ ] **SES-04.** Los datos y los textos generados con un modelo se rotulan como tales, con el modelo y la fecha, en las tablas, las figuras y los conjuntos publicados. (Requisito de esta guía)
- [ ] **SES-05.** *(Recomendado)* Se estima y se declara el consumo de energía o las emisiones de la ejecución del modelo. (Hugging Face, s. f.-b)

**2.9. Documentación y ciclo de vida**

- [ ] **DOC-01.** Un archivo `LLM_USE.md` registra cada modelo usado, con su identificación, licencia, parámetros, prompts, evaluación y limitaciones. (Mitchell et al., 2019; Requisito de esta guía)
- [ ] **DOC-02.** El `README` explica cómo obtener cada modelo y volver a ejecutar el cuaderno: revisión exacta, comando y, si el acceso es restringido, cómo solicitarlo. (Digital Public Goods Alliance, s. f., indicador 5)
- [ ] **DOC-03.** Un cambio de modelo, de revisión, de prompt o de parámetros sube la versión del cuaderno, y el `CHANGELOG.md` registra su efecto en los resultados. (Requisitos para modelos, DOC-02)
- [ ] **DOC-04.** El uso de modelos como componente del análisis se declara en `LLM_USE.md`, y el uso de asistentes para escribir o programar se declara según los [requisitos para el uso de IA](05-uso-de-ia.md); ambas declaraciones son coherentes entre sí. (Requisitos para el uso de IA, U04)
- [ ] **DOC-05.** Si el cuaderno entrena o ajusta un modelo, cumple además los [requisitos para modelos](08-estandar-modelos.md) y publica su `MODEL_CARD.md` (aplica solo si hay ajuste o entrenamiento). (Requisitos para modelos, USO-01)
- [ ] **DOC-06.** *(Recomendado)* El modelo ajustado se publica en un repositorio de modelos de acceso libre, con su ficha. (Hugging Face, s. f.-b)

## 4. Prompt para validar el uso de LLMs

Este prompt convierte la lista de verificación en una auditoría repetible. Lee el repositorio de un cuaderno, busca los modelos preentrenados que carga o llama, comprueba su identificación, su licencia, su seguridad y su reproducibilidad, y genera un **reporte de cumplimiento** en Markdown y JSON. Funciona con cualquier asistente de IA que pueda leer archivos y ejecutar comandos.

**Procedimiento de uso**

1. Copie el prompt completo y reemplace los valores entre `<>` de la sección ENTRADAS.
2. Ejecútelo desde un entorno con acceso a los archivos del repositorio. Para consultar el repositorio de origen de cada modelo (licencia, revisión, modelo base), use el modo `con_red`.
3. Revise el reporte con una persona. Un asistente de IA puede equivocarse al leer un archivo o interpretar un criterio. El resultado es un apoyo a la revisión y no una certificación, y todo lo marcado «Requiere revisión humana» lo decide una persona.
4. Guarde el reporte en el repositorio y repita la auditoría antes de cada *release* y cada vez que cambie un modelo, una revisión o un prompt.

:::{warning} Lo que este prompt no puede hacer
No valida el mérito científico del análisis ni sustituye la revisión de una persona experta del dominio. No puede probar que un modelo es seguro: reconoce señales (formatos de pesos, banderas de ejecución de código, revisiones sin fijar) pero no analiza el contenido de los pesos. Tampoco puede reproducir ejecuciones que exijan más recursos de los que tiene. Las decisiones sobre licencias, datos de comunidades y daños posibles se marcan «Requiere revisión humana».

En modo `con_red` solo debe enviar a Internet identificadores de modelos, nunca datos del repositorio. Si el auditor es un servicio externo, aplíquele las mismas reglas que a cualquier IA: no le entregue datos personales, datos de comunidades ni material con restricciones de licencia (véanse los [requisitos para el uso de IA](05-uso-de-ia.md)). Si cambia la lista de verificación, actualice también los criterios del prompt.
:::

````text
Actúa como auditor del uso de modelos preentrenados de terceros (modelos de lenguaje y otros, obtenidos de repositorios como Hugging Face o de APIs alojadas) en cuadernos reproducibles de la Subdirección para el Conocimiento del Riesgo (UNGRD). Tu tarea es VERIFICAR si un cuaderno y su repositorio cumplen la lista de verificación de los «Requisitos para el uso de LLMs» y producir un REPORTE DE CUMPLIMIENTO. Eres un revisor: NO modifiques ningún archivo.

## ENTRADAS
- RUTA_REPO: <ruta local del repositorio del cuaderno>
- CUADERNO (opcional): <ruta del cuaderno .md/.ipynb que usa los modelos>
- MODO: "estatico" (solo leer archivos e historial) o "con_red" (además consultar los metadatos públicos de cada modelo en su repositorio de origen) o "con_ejecucion" (además ejecutar el cuaderno o su versión reducida en una copia aislada). Si no lo indico, usa "estatico".
- SALIDA: carpeta donde escribir `reporte_llms.md` y `reporte_llms.json`; si no la indico, imprime el reporte.

## REGLAS DE CONDUCTA (obligatorias)
1. Toda afirmación cita su evidencia: archivo y línea, hash de commit, respuesta de un servicio o salida de un comando. Sin evidencia, el estado es «No verificable».
2. No inventes. No supongas que algo cumple. Distingue «No aplica» (con la razón) de «No cumple».
3. Solo lectura. No modifiques archivos. No descargues ni cargues pesos de modelos. Ejecuta código del repositorio únicamente si lo leíste antes, en una copia aislada y en modo «con_ejecucion».
4. En modo «con_red» envía a Internet solo identificadores públicos de modelos, nunca datos, prompts ni fragmentos del repositorio. Si eres un servicio externo, trabaja solo con el material que la persona autorizó, y no copies al reporte valores ni fragmentos con datos personales ni credenciales: cita solo nombres de archivos, de variables y de columnas.
5. Las decisiones éticas y legales (licencias, datos personales, datos de comunidades, derechos de terceros) no son tuyas: márcalas «Requiere revisión humana».
6. Las pruebas automáticas de seguridad no son concluyentes: informa lo que detectan y márcalo «Requiere prueba manual».
7. No evalúes el mérito científico de los resultados. Evalúa identificación, licencia, seguridad, reproducibilidad, evaluación documentada, privacidad y documentación.

## PROCEDIMIENTO
### Paso A. Inventario de modelos
Describe la ruta auditada, el modo y qué no se pudo revisar. Lista cada modelo de terceros que el repositorio carga o llama: identificador, forma de acceso (pesos locales o API alojada), tarea, archivos donde aparece y revisión fijada o no. Si no encuentras ninguno, repórtalo y marca todos los criterios «No aplica».

### Paso B. Comprobaciones automáticas (ejecuta las que apliquen y conserva la salida)
1. Detección: busca `from_pretrained`, `pipeline(`, `AutoModel`, `AutoTokenizer`, `snapshot_download`, `hf_hub_download`, `InferenceClient`, `sentence_transformers`, `transformers`, `huggingface_hub`, `diffusers`, `timm`, `torch.hub`, `spacy.load`, `whisper`, `onnxruntime`, `openai`, `anthropic`, `langchain`, `llama_cpp`, `ollama` y llamadas HTTP a servicios de modelos, en `.py`, `.ipynb`, `.md`, `environment.yml` y `requirements.txt`. Para `pipeline(` y nombres similares (por ejemplo, `make_pipeline` de `scikit-learn`), confirma por la importación que provienen de una biblioteca de modelos preentrenados y descarta los falsos positivos.
2. Revisión fijada: para cada `from_pretrained`, `pipeline(model=...)` o descarga, comprueba que `revision` sea un hash de 40 caracteres y no `main`, una rama ni una etiqueta móvil. Para una API, comprueba que el nombre del modelo incluya su fecha de versión.
3. Código remoto: busca `trust_remote_code=True`. Si existe, verifica que el repositorio documente la lectura del código y la revisión fijada.
4. Formato de pesos: busca `pickle`, `torch.load` sin `weights_only=True`, archivos `.bin` o `.pkl` de pesos, y comprueba si se usa `safetensors` u ONNX.
5. Agentes y MCP: busca `mcp`, `fastmcp`, `mcpServers`, `.mcp.json`, `.cursor/mcp.json`, `.vscode/mcp.json` y bucles de agente con herramientas. Para cada servidor, registra origen, versión fijada, permisos y si las llamadas se registran.
6. Credenciales: busca tokens y claves en archivos y en el historial de git (`hf_`, `sk-`, `api_key`, `HF_TOKEN` con valor asignado). Reporta el archivo y la línea, no el valor.
7. Dependencias: comprueba que las bibliotecas que cargan modelos tienen versión fijada.
8. Prompts: comprueba si los prompts están en archivos versionados y si el cuaderno valida el formato de la salida.
9. Parámetros y salidas: comprueba que los parámetros de generación estén fijados y que existan salidas en bruto guardadas con su entrada, fecha y revisión; comprueba si el cuaderno se puede reproducir sin llamar al modelo.
10. Privacidad: identifica qué datos se envían a servicios alojados. Marca los que parezcan personales, de comunidades, no publicados o con restricciones de licencia como «Requiere revisión humana».
11. Evaluación: busca una muestra de referencia, métricas con incertidumbre, línea base sin modelo de lenguaje y análisis de errores.
12. Repositorio de origen (solo en modo «con_red»): para cada modelo, consulta los metadatos públicos del Hub (`https://huggingface.co/api/models/<identificador>`) y registra licencia, si es de acceso restringido, modelo base, etiquetas y la fecha del último cambio. Compara la revisión fijada con la actual. Si no hay red o el modelo no está en el Hub, el estado de lo que dependa de ello es «No verificable».
13. Ficha y documentos: comprueba que existan `LLM_USE.md`, la copia archivada de la ficha del modelo, `DO_NO_HARM.md`, `CHANGELOG.md`, `README.md` y `environment.yml`.
14. Reproducción (solo en modo «con_ejecucion»): en una copia limpia, ejecuta el cuaderno desde las salidas guardadas y compara los resultados. Registra las diferencias.

### Paso C. Evaluación de criterios
Evalúa los 53 criterios. Para cada uno asigna exactamente un estado: Cumple, Parcial, No cumple, No aplica o No verificable. Los marcados (CRÍTICO) son compuertas bloqueantes y los marcados (RECOMENDADO) no condicionan la aceptación.

### Identificación y procedencia
IDE-01. Cada modelo se identifica con su identificador completo en el repositorio de origen (organización y nombre), la tarea para la que se usa y la forma de acceso: pesos descargados que se ejecutan localmente o API alojada. (Requisito de esta guía)
IDE-02 (CRÍTICO). Cada modelo está fijado a una revisión inmutable (el *hash* de un *commit*), no a una rama como `main` ni a una etiqueta que pueda moverse; en una API alojada, a la versión del modelo con su fecha. (Hugging Face, s. f.-a; Requisito de esta guía)
IDE-03. La ficha del modelo (*model card*) del repositorio de origen se leyó y se archivó una copia fechada en el repositorio del cuaderno; resume el uso previsto, las limitaciones y los datos de entrenamiento que declara el modelo, o indica que no los declara. (Mitchell et al., 2019; Gebru et al., 2021; Hugging Face, s. f.-b)
IDE-04. Si el modelo es un derivado (ajuste fino, adaptador, cuantización o fusión), se identifican el modelo base y el tipo de relación. (Hugging Face, s. f.-b)
IDE-05. Cada modelo se cita en las referencias con autoría o entidad, año, versión, enlace y DOI cuando exista. (Requisitos para datos, INV-02)
IDE-06 (RECOMENDADO). Se indica el grado de apertura del modelo (solo pesos, o también código de entrenamiento y datos) con el Model Openness Framework. (White et al., 2024)

### Licencia y términos
TER-01 (CRÍTICO). La licencia del modelo permite el uso previsto (investigación, uso institucional, publicación de resultados y de derivados) y está registrada con su identificador o su texto. (Hugging Face, s. f.-b; Requisito de esta guía)
TER-02. Si el modelo es de acceso restringido o exige aceptar condiciones, las aceptó una persona con autoridad para hacerlo, y el cuaderno explica cómo obtener el acceso sin publicar credenciales ni pesos que la licencia no permita redistribuir. (Requisito de esta guía)
TER-03. Las restricciones de uso de la licencia (usos prohibidos, uso no comercial, límites por tamaño de la organización) se revisaron frente al uso institucional y a la publicación abierta del cuaderno. (Requisito de esta guía)
TER-04. Las condiciones de los datos de entrenamiento que declara el modelo se revisaron; si no las declara, queda registrado como limitación. (Gebru et al., 2021; Requisitos para datos, INV-05)
TER-05. Las salidas del modelo se publican bajo una licencia compatible con los términos del modelo o del proveedor de la API. (Requisitos para el uso de IA, U21)

### Seguridad de la cadena de suministro
SEG-01 (CRÍTICO). El cuaderno no ejecuta código remoto del repositorio del modelo sin revisarlo: `trust_remote_code` es falso, o se activa solo después de leer ese código y de fijar la revisión. (Hugging Face, s. f.-a)
SEG-02. Los pesos se cargan en un formato que no ejecuta código al cargarse (`safetensors` u ONNX). Si solo existe un archivo `pickle`, se verifica el origen y se documenta el riesgo. (Hugging Face, s. f.-c; OWASP Foundation, 2025, LLM03)
SEG-03. El origen del modelo es una organización o persona verificable, y el cuaderno registra la suma de verificación o el *hash* de la revisión de los archivos descargados. (Hugging Face, s. f.-c; Requisito de esta guía)
SEG-04. Las bibliotecas que cargan y ejecutan el modelo (`transformers`, `tokenizers`, `huggingface_hub` y similares) tienen versión fijada en `environment.yml`, y el cuaderno no instala paquetes desde fuentes sin versión. (OWASP Foundation, 2025, LLM03)
SEG-05. Los tokens y las claves de API se leen de variables de entorno o de secretos, y no aparecen en el cuaderno, en las salidas guardadas ni en el historial de git. (Requisito de esta guía)
SEG-06. Si el modelo recibe texto de fuentes externas (noticias, páginas web, documentos de terceros), ese texto se trata como no confiable: la salida del modelo no se ejecuta como código ni dispara acciones sin revisión. (OWASP Foundation, 2025, LLM01 y LLM05)
SEG-07. Si el modelo actúa como agente con herramientas (ejecuta código, consulta bases de datos, escribe archivos), sus permisos son mínimos, corre en un entorno aislado y toda acción irreversible requiere aprobación humana (aplica solo a agentes). (OWASP Foundation, 2025, LLM06)
SEG-08. Si el cuaderno usa conectores o servidores MCP, estos son de origen verificable, tienen la versión fijada y corren con los privilegios mínimos; el texto que devuelven y las descripciones de sus herramientas se tratan como no confiables (aplica solo si el cuaderno usa MCP). (MCP, s. f.-a, s. f.-b; OWASP Foundation, 2025, LLM01 y LLM03)

### Ejecución y reproducibilidad
EJE-01. El cuaderno declara el hardware, la memoria y el tiempo que necesita, y se ejecuta con cómputo gratuito (Colab o Binder) o ofrece un modelo más pequeño o una versión reducida. (Requisitos para modelos, REP-03)
EJE-02. Los parámetros de generación (temperatura, `top_p`, máximo de tokens, semilla, cuantización y precisión numérica) están fijados y registrados; si la tarea lo permite, la decodificación es determinista. (Requisito de esta guía)
EJE-03. Las salidas en bruto que alimentan resultados se guardan junto con su entrada, los parámetros, la fecha y la revisión del modelo, y los resultados se reproducen desde esas salidas, sin una nueva llamada al modelo. (Requisitos para el uso de IA, U12)
EJE-04. El cuaderno declara las fuentes de no determinismo (GPU, versión de las bibliotecas, tamaño del lote) y reporta la variación de varias ejecuciones o demuestra que las salidas guardadas bastan para reproducir los resultados. (Pineau et al., 2021)
EJE-05. Si usa una API alojada, el cuaderno archiva las salidas y la fecha de consulta, y no queda inutilizable si el proveedor cambia o retira el modelo. (Requisito de esta guía)
EJE-06. Si el modelo usa herramientas o servidores MCP, cada llamada (herramienta, argumentos, resultado y fecha) se registra, y los resultados se reproducen desde ese registro y no desde una nueva llamada (aplica solo si hay herramientas o MCP). (Requisitos para el uso de IA, U26; Requisito de esta guía)
EJE-07 (RECOMENDADO). El modelo y el tokenizador se archivan con DOI y suma de verificación cuando la licencia lo permite, o el cuaderno documenta cómo recuperar la revisión exacta. (Chue Hong et al., 2022)

### Prompts y configuración
PRO-01. Los prompts (instrucciones del sistema, plantillas, ejemplos y esquemas de salida) están en archivos versionados del repositorio, no solo escritos en celdas sueltas. (Requisito de esta guía)
PRO-02. Cada prompt documenta su objetivo, sus variables de entrada y el formato de salida esperado, y sus cambios se registran en el `CHANGELOG.md`. (Requisito de esta guía)
PRO-03. La salida del modelo se restringe a un formato verificable (JSON con esquema u opciones cerradas), y el cuaderno valida cada salida y registra las que rechaza. (OWASP Foundation, 2025, LLM05)
PRO-04. Los prompts no contienen datos personales, credenciales ni datos con restricciones de licencia. (Requisitos para el uso de IA, U20)
PRO-05 (RECOMENDADO). El cuaderno prueba la sensibilidad de los resultados a variaciones del prompt (parafraseos, orden de los ejemplos) y reporta cuánto cambian. (Requisito de esta guía)

### Evaluación
EVA-01 (CRÍTICO). Una muestra de referencia etiquetada por personas expertas, separada de los ejemplos del prompt y de cualquier ajuste, valida la salida del modelo para la tarea concreta antes de usar los resultados. (Requisitos para el uso de IA, U11; Requisitos para modelos, VAL-01)
EVA-02. Las métricas se justifican para la tarea y se reportan con su incertidumbre, junto con el tamaño de la muestra y el acuerdo entre las personas que la etiquetaron. (Requisitos para modelos, VAL-02)
EVA-03. El desempeño se compara con una línea base sin modelo de lenguaje (reglas, diccionarios, expresiones regulares o un clasificador sencillo), y se justifica por qué se necesita un LLM. (Requisitos para modelos, VAL-04)
EVA-04. La evaluación usa textos del dominio y del idioma de uso (español de Colombia, topónimos locales, términos de gestión del riesgo), no solo las pruebas genéricas del repositorio de origen. (Requisito de esta guía)
EVA-05. Las cifras de desempeño que publica el modelo (pruebas comparativas y tablas de clasificación) se tratan como referencia y no como evidencia de su desempeño en esta tarea; se considera la posible contaminación de las pruebas con datos de entrenamiento. (Mitchell et al., 2019; Requisito de esta guía)
EVA-06. Se documentan los errores frecuentes, incluidas las confabulaciones (contenido plausible pero falso), con la tasa de error por categoría y ejemplos de los casos que fallaron. (NIST, 2024; OWASP Foundation, 2025, LLM09)
EVA-07 (RECOMENDADO). Se mide la consistencia (la misma entrada en varias ejecuciones) y, si el modelo reporta confianza, su calibración. (Requisitos para modelos, INC-04)

### Privacidad y datos
PRI-01 (CRÍTICO). No se envían datos personales, de comunidades, no publicados ni con restricciones de licencia a un servicio alojado de terceros (API, proveedores de inferencia o Spaces); esos datos solo se procesan con modelos que se ejecutan localmente. (Carroll et al., 2020; OWASP Foundation, 2025, LLM02; Requisitos para el uso de IA, U20)
PRI-02. Para cada servicio alojado se documenta qué datos recibe, quién lo opera y en qué país, y se revisaron sus términos sobre retención de datos y entrenamiento. (Requisitos para el uso de IA, U21)
PRI-03. Las salidas se revisan antes de publicarlas para comprobar que no reproducen datos personales ni texto con derechos de terceros. (OWASP Foundation, 2025, LLM02)
PRI-04. Lo que el cuaderno publique en un repositorio de modelos o de datos (modelos ajustados, conjuntos derivados, Spaces) cumple los requisitos para datos y no incluye datos de comunidades sin autorización registrada. (Carroll et al., 2020; Requisitos para datos, PER-02)

### Riesgos, sesgos y uso responsable
SES-01. Existe un análisis de «no hacer daño» del uso del modelo de lenguaje: usos indebidos, errores con consecuencias y medidas adoptadas (`DO_NO_HARM.md`). (Digital Public Goods Alliance, s. f., indicador 9)
SES-02. Se evaluaron y se declaran los sesgos del modelo y de su fuente: geográficos (más texto de unas regiones que de otras), de idioma y de tipo de fuente. (CRED, 2026; Mitchell et al., 2019)
SES-03. Ninguna decisión de gestión del riesgo (alerta, priorización, mapa) depende solo de la salida del modelo; una persona experta la revisa. (Requisitos para el uso de IA, recomendación 4)
SES-04. Los datos y los textos generados con un modelo se rotulan como tales, con el modelo y la fecha, en las tablas, las figuras y los conjuntos publicados. (Requisito de esta guía)
SES-05 (RECOMENDADO). Se estima y se declara el consumo de energía o las emisiones de la ejecución del modelo. (Hugging Face, s. f.-b)

### Documentación y ciclo de vida
DOC-01. Un archivo `LLM_USE.md` registra cada modelo usado, con su identificación, licencia, parámetros, prompts, evaluación y limitaciones. (Mitchell et al., 2019; Requisito de esta guía)
DOC-02. El `README` explica cómo obtener cada modelo y volver a ejecutar el cuaderno: revisión exacta, comando y, si el acceso es restringido, cómo solicitarlo. (Digital Public Goods Alliance, s. f., indicador 5)
DOC-03. Un cambio de modelo, de revisión, de prompt o de parámetros sube la versión del cuaderno, y el `CHANGELOG.md` registra su efecto en los resultados. (Requisitos para modelos, DOC-02)
DOC-04. El uso de modelos como componente del análisis se declara en `LLM_USE.md`, y el uso de asistentes para escribir o programar se declara según los [requisitos para el uso de IA](05-uso-de-ia.md); ambas declaraciones son coherentes entre sí. (Requisitos para el uso de IA, U04)
DOC-05. Si el cuaderno entrena o ajusta un modelo, cumple además los [requisitos para modelos](08-estandar-modelos.md) y publica su `MODEL_CARD.md` (aplica solo si hay ajuste o entrenamiento). (Requisitos para modelos, USO-01)
DOC-06 (RECOMENDADO). El modelo ajustado se publica en un repositorio de modelos de acceso libre, con su ficha. (Hugging Face, s. f.-b)

### Paso D. Puntuación
- Cumple = 1, Parcial = 0,5, No cumple = 0. «No aplica» y «No verificable» no entran en el denominador, pero repórtalos con su conteo.
- Puntaje por grupo y total = suma de puntos de los criterios obligatorios y críticos ÷ criterios evaluables × 100, con un decimal. Los recomendados se reportan aparte.
- Nivel: 90 o más, «Alto»; de 75 a 89,9, «Aceptable»; de 50 a 74,9, «Mejorable»; menos de 50, «Insuficiente».
- Si ningún criterio es evaluable (por ejemplo, porque el repositorio no usa modelos de terceros), el resultado global es «NO APLICA» y no se calcula puntaje.
- Compuertas: si algún criterio CRÍTICO está en «No cumple», el resultado global es «NO APTO». Si alguno está en «No verificable», es «PENDIENTE DE VERIFICACIÓN». Si el puntaje es menor de 90, el resultado es «NO APTO» aunque no falle ningún crítico.

### Paso E. Redacta el reporte con esta estructura exacta
1. **Resumen ejecutivo**: resultado global, puntaje y nivel, criterios críticos fallidos y las tres prioridades más urgentes, en menos de 150 palabras.
2. **Alcance y método**: ruta auditada, modo, fecha y qué no se pudo revisar.
3. **Inventario de modelos**: tabla con modelo, forma de acceso, revisión fijada, licencia (si se consultó), tarea y archivos.
4. **Resultados por criterio**: tabla con ID, criterio, estado, evidencia, acción recomendada y prioridad (Alta, Media o Baja).
5. **Puntaje por grupo**.
6. **Hallazgos que requieren revisión humana o prueba manual**, cada uno marcado como tal.
7. **Ficha de uso sugerida**: borrador de `LLM_USE.md` con los datos que sí pudiste confirmar y marcadores `<...>` donde falte información que solo la persona autora conoce.
8. **Plan de mejora** ordenado por prioridad, con esfuerzo estimado (S, M o L).
9. **Limitaciones de esta auditoría**.

### Paso F. Versión legible por máquina
Escribe `reporte_llms.json` con esta forma:
{"repositorio": "...", "fecha": "AAAA-MM-DD", "modo": "...", "resultado_global": "...", "puntaje_total": 0.0, "nivel": "...", "modelos": [{"modelo": "...", "acceso": "local|api", "revision_fijada": true, "licencia": "...", "tarea": "..."}], "criterios": [{"id": "XXX-00", "estado": "...", "evidencia": "...", "accion": "...", "prioridad": "..."}], "revision_humana": ["..."], "no_verificables": ["XXX-00"]}

Termina con un resumen de cinco líneas y la ruta de los archivos generados.
````

**Compuertas críticas.** El prompt trata como bloqueantes los 5 criterios críticos y exige además un puntaje de 90 o más en los obligatorios. Estas reglas son criterios propios de la SCR.

## Referencias

Carroll, S. R., Garba, I., Figueroa-Rodríguez, O. L., Holbrook, J., Lovett, R., Materechera, S., Parsons, M., Raseroka, K., Rodriguez-Lonebear, D., Rowe, R., Sara, R., Walker, J. D., Anderson, J., y Hudson, M. (2020). The CARE Principles for Indigenous Data Governance. *Data Science Journal, 19*, Artículo 43. https://doi.org/10.5334/dsj-2020-043

Centre for Research on the Epidemiology of Disasters. (2026). *EM-DAT documentation* (Versión 2026.11) [Documentación en línea]. Université catholique de Louvain. https://doc.emdat.be/

Chue Hong, N. P., Katz, D. S., Barker, M., y FAIR4RS Working Group. (2022). *FAIR Principles for Research Software (FAIR4RS Principles)* (Versión 1.0) [Recomendación del Research Data Alliance]. https://doi.org/10.15497/RDA00068

Digital Public Goods Alliance. (s. f.). *DPG Standard* [Especificación en línea]. GitHub. Recuperado el 16 de noviembre de 2026, de https://github.com/DPGAlliance/DPG-Standard

Gebru, T., Morgenstern, J., Vecchione, B., Vaughan, J. W., Wallach, H., Daumé, H., III, y Crawford, K. (2021). Datasheets for datasets. *Communications of the ACM, 64*(12). https://doi.org/10.1145/3458723

Hugging Face. (s. f.-a). *Auto classes* [Documentación de Transformers]. Recuperado el 19 de noviembre de 2026, de https://huggingface.co/docs/transformers/main/en/model_doc/auto

Hugging Face. (s. f.-b). *Model cards* [Documentación del Hub]. Recuperado el 19 de noviembre de 2026, de https://huggingface.co/docs/hub/model-cards

Hugging Face. (s. f.-c). *Pickle scanning* [Documentación del Hub]. Recuperado el 19 de noviembre de 2026, de https://huggingface.co/docs/hub/security-pickle

Mitchell, M., Wu, S., Zaldivar, A., Barnes, P., Vasserman, L., Hutchinson, B., Spitzer, E., Raji, I. D., y Gebru, T. (2019). Model cards for model reporting. *Proceedings of the Conference on Fairness, Accountability, and Transparency (FAT\* '19)*. https://doi.org/10.1145/3287560.3287596

Model Context Protocol. (s. f.-a). *Security best practices* [Especificación del protocolo, versión 2026-07-28]. Recuperado el 19 de noviembre de 2026, de https://modelcontextprotocol.io/specification/latest/basic/security_best_practices

Model Context Protocol. (s. f.-b). *Specification* [Especificación del protocolo, versión 2026-07-28]. Recuperado el 19 de noviembre de 2026, de https://modelcontextprotocol.io/specification/latest

National Institute of Standards and Technology. (2024). *Artificial intelligence risk management framework: Generative artificial intelligence profile* (NIST AI 600-1). https://doi.org/10.6028/NIST.AI.600-1

OWASP Foundation. (2025). *OWASP Top 10 for LLM applications 2025*. Recuperado el 19 de noviembre de 2026, de https://genai.owasp.org/llm-top-10/

Pineau, J., Vincent-Lamarre, P., Sinha, K., Larivière, V., Beygelzimer, A., d'Alché-Buc, F., Fox, E., y Larochelle, H. (2021). Improving reproducibility in machine learning research (A report from the NeurIPS 2019 Reproducibility Program). *Journal of Machine Learning Research, 22*(164), 1–20. https://jmlr.org/papers/v22/20-303.html

White, M., Haddad, I., Osborne, C., Liu, X.-Y. Y., Abdelmonsef, A., Varghese, S., y Le Hors, A. (2024). *The Model Openness Framework: Promoting completeness and openness for reproducibility, transparency, and usability in artificial intelligence* (arXiv:2403.13784). https://arxiv.org/abs/2403.13784
