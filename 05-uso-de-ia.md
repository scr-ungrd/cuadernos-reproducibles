---
title: Requisitos para el uso de IA
subtitle: Requisitos y recomendaciones para usar inteligencia artificial de forma ética y responsable en un cuaderno reproducible
date: 2026-11-16
authors:
  - name: Subdirección para el Conocimiento del Riesgo
    affiliation: Unidad Nacional para la Gestión del Riesgo de Desastres (UNGRD)
    github: scr-ungrd
site:
  hide_authors: true
license: CC-BY-4.0
keywords:
  - inteligencia artificial
  - IA generativa
  - modelos de lenguaje
  - ética
  - integridad científica
  - reproducibilidad
  - riesgo de desastres
abbreviations:
  IA: inteligencia artificial
  LLM: modelo de lenguaje de gran escala
  ICMJE: International Committee of Medical Journal Editors
  NHESS: Natural Hazards and Earth System Sciences
  DOI: Digital Object Identifier
---


## Para qué sirven estos requisitos

Los asistentes de IA escriben código, resumen literatura, traducen y dibujan figuras. En un cuaderno reproducible, la pregunta central es **quién responde por lo que se ejecuta y por lo que se concluye**. Estos requisitos dan reglas prácticas para cuatro momentos: la escritura del texto, el código y el análisis, la construcción de datos y figuras, y la evaluación de cuadernos ajenos. Cubre también a los asistentes en modo agente que usan conectores o servidores del Model Context Protocol (MCP).


:::{important} Alcance y límites de estos requisitos
Las políticas de las revistas cambian con frecuencia y cada revista puede tener reglas propias que prevalecen sobre las de su editorial. Este documento resume las políticas consultadas el **16 de noviembre de 2026** y no reemplaza la política de la revista donde se vaya a enviar el trabajo. No es asesoría jurídica. Las recomendaciones que no citan ninguna fuente son criterios propios de la Subdirección para el Conocimiento del Riesgo (SCR).
:::

## Fuentes y síntesis de las políticas

**Fuentes.** Se consultaron las políticas de IA de Elsevier (s. f.), de Natural Hazards and Earth System Sciences [NHESS] (s. f.), de Nature Climate Change (s. f.), de Springer Nature (s. f.) y de Wiley (s. f.), y las recomendaciones del International Committee of Medical Journal Editors [ICMJE] (s. f.). La selección responde a su relevancia en desastres y cambio climático, no a un ranking ni a un índice de impacto. No se incluyeron las políticas de AGU, de Science (AAAS) ni de COPE, porque sus páginas oficiales no pudieron consultarse. Las referencias completas aparecen en la bibliografía, al final de este documento.

**Síntesis.** Las principales editoriales científicas del mundo coinciden en que la responsabilidad por el contenido es humana y no se delega, y en que una herramienta de IA no puede figurar como autora (Elsevier, s. f.; ICMJE, s. f.; Nature Climate Change, s. f.; Springer Nature, s. f.). Coinciden también en que el uso debe declararse (Elsevier, s. f.; NHESS, s. f.; Springer Nature, s. f.; Wiley, s. f.), en que no se admiten datos, citas ni resultados fabricados (NHESS, s. f.; Springer Nature, s. f.), en que las imágenes generadas o alteradas con IA no pueden representar datos ni resultados (Elsevier, s. f.; Springer Nature, s. f.; Wiley, s. f.) y en que los manuscritos en evaluación no deben subirse a herramientas de IA públicas (Elsevier, s. f.; NHESS, s. f.; Springer Nature, s. f.; Wiley, s. f.).

Las políticas difieren en tres aspectos. El primero es el umbral de la declaración: unas exigen declarar todo uso salvo la corrección ortográfica y gramatical (Elsevier, s. f.); otras, solo el uso que excede el apoyo asistivo (NHESS, s. f.) o el que genera o reformula texto, traduce o interviene en la metodología, el código y el análisis (Wiley, s. f.); y el marco de Springer Nature recomienda declarar incluso los usos de bajo riesgo (Nature Climate Change, s. f.). El segundo es el lugar de la declaración: una sección separada antes de las referencias (Elsevier, s. f.), Métodos o Agradecimientos (NHESS, s. f.), o Métodos, Agradecimientos y pies de figura según el tipo de uso (Wiley, s. f.). El tercero es el texto generado: NHESS (s. f.) no admite IA generativa para el texto ni para las interpretaciones, mientras que otras políticas permiten el apoyo con supervisión humana y declaración (Elsevier, s. f.; Springer Nature, s. f.; Wiley, s. f.). Cuando el destino de publicación es incierto, conviene aplicar la política más estricta de las tres, que en el caso del texto es la de NHESS.

## Clasificar cada uso por riesgo

Un marco de la editorial Springer Nature evalúa el uso de IA por su **nivel de riesgo y no por el tipo de herramienta**, con tres colores (Nature Climate Change, s. f.). La clasificación siguiente lo adapta a un cuaderno de riesgo de desastres, con apoyo en las listas de usos de Wiley (s. f.).

```{list-table} Clasificación de usos de IA en un cuaderno
:header-rows: 1
:label: tabla-riesgo-ia

* - Nivel
  - Qué significa
  - Ejemplos en un cuaderno
  - Qué hacer
* - **Verde**: permitido
  - Apoyo a la expresión, la organización o la eficiencia, sin influir en el juicio científico. El uso es reversible y verificable.
  - Pulir el idioma. Sugerir la estructura de una sección. Depurar errores. Dar formato al código. Redactar comentarios. Limpiar y deduplicar datos. Comparar opciones metodológicas.
  - Permitido. La SCR exige declarar todo uso salvo la corrección ortográfica y gramatical.
* - **Ámbar**: con cautela
  - La IA aporta razonamiento o contenido nuevo que puede influir en la interpretación, aunque la persona siga al mando.
  - Escribir scripts, flujos de procesamiento o modelos. Traducir. Reorganizar argumentos. Resumir o buscar literatura. Extraer datos con un modelo de lenguaje. Identificar patrones exploratorios. Explicar resultados estadísticos. Hacer diagramas conceptuales. Dar a un agente acceso a su equipo, a su repositorio o a conectores y servidores MCP.
  - Permitido con verificación humana demostrable y **declaración obligatoria**.
* - **Rojo**: no permitido
  - La IA sustituye la responsabilidad humana, el uso es opaco o genera resultados que no se pueden verificar.
  - Fabricar datos, citas o resultados. Presentar como propias hipótesis o conclusiones generadas por IA. Generar o alterar imágenes de datos observados. Atribuir autoría a una IA. Subir información confidencial a una IA pública. Delegar la evaluación por pares en una IA.
  - No se hace. Si ocurrió, se corrige y se informa.
```

## Recomendaciones para un uso ético y responsable

Cada recomendación cita las fuentes en que se apoya. Las que no citan ninguna son criterios propios de la SCR.

### Responsabilidad y autoría

1. **Asuma la responsabilidad total.** Quien firma el cuaderno responde por cada línea de código, cada cifra y cada frase, aunque las haya generado una IA (Elsevier, s. f.; ICMJE, s. f.; Springer Nature, s. f.; Wiley, s. f.).
2. **No incluya una IA como autora ni coautora.** Su uso se declara en la sección de IA, no en la lista de autores (Elsevier, s. f.; ICMJE, s. f.; Springer Nature, s. f.).
3. **Las conclusiones y la interpretación del riesgo son suyas.** La IA puede ayudar a explorar o a explicar, pero no determina conclusiones, evaluaciones ni decisiones (Nature Climate Change, s. f.).
4. **Valide con una persona experta lo que alimente decisiones de gestión del riesgo.** Una salida de IA sin validación experta no debe sustentar un mapa de amenaza, una alerta ni una priorización.

### Transparencia

5. **Declare el uso de IA y trate la declaración como un registro, no como un trámite.** Debe permitir a otra persona entender qué hizo la IA y qué hizo usted (Elsevier, s. f.; NHESS, s. f.; Springer Nature, s. f.; Wiley, s. f.). Use la plantilla de la sección siguiente.
6. **Conserve los prompts y los parámetros** en el repositorio. Las editoriales piden registrar las versiones de la herramienta, las fechas de uso, los prompts y el alcance (Springer Nature, s. f.), y pueden solicitar los prompts, las configuraciones y el código (Wiley, s. f.).
7. **Declare cada uso donde un lector lo buscaría**: la metodología, el código y el análisis en Métodos; la redacción y la traducción en Agradecimientos; las figuras en el pie de figura (NHESS, s. f.; Wiley, s. f.).
8. **Si no usó IA, dígalo.** El propósito de la declaración es eliminar la ambigüedad sobre cómo se usó la IA (Nature Climate Change, s. f.); por eso se recomienda escribir «No se usó IA» cuando corresponda.
9. **Revise la política de la revista de destino antes de enviar.** Las políticas se revisan periódicamente (Nature Climate Change, s. f.) y difieren entre editoriales.

### Integridad de datos, citas y resultados

10. **No fabrique ni altere datos, citas ni resultados con IA.** Es la línea roja que comparten las políticas que se pronuncian sobre el tema (NHESS, s. f.; Nature Climate Change, s. f.).
11. **Verifique cada referencia.** Las referencias generadas por IA pueden ser incorrectas o inventadas (Elsevier, s. f.; Springer Nature, s. f.). Compruebe que el DOI resuelve y que el trabajo dice lo que usted afirma.
12. **No cite una IA como fuente primaria** y atribuya correctamente todo lo citado (ICMJE, s. f.).
13. **Asegúrese de que no hay plagio** ni material con derechos de terceros en lo generado, ni en texto ni en imágenes (ICMJE, s. f.; Wiley, s. f.).

(uso-de-ia-datos)=
### Datos extraídos o generados con modelos de lenguaje

La documentación de EM-DAT enlaza conjuntos que usan modelos de lenguaje para extraer información de noticias o de Wikipedia, como *Disaster Storylines* y *Wikimpacts* (Centre for Research on the Epidemiology of Disasters [CRED], 2026, sección 6.2). Estos conjuntos muestran por qué los datos construidos con modelos de lenguaje necesitan reglas propias. Si el cuaderno llama a un modelo preentrenado de terceros (por ejemplo, de Hugging Face) como parte del análisis, cumpla además los [requisitos para el uso de LLMs](09-uso-de-llms.md), que audita la identificación, la licencia, la seguridad y la reproducibilidad del modelo.

14. **Trátelos como datos derivados con riesgo de error**, no como una fuente primaria. Documente el modelo, la versión, el prompt, los parámetros y la fecha (Wiley, s. f.).
15. **Mida el error.** Revise a mano una muestra y publique la tasa de error y los casos que fallaron. Wiley (s. f.) pide describir cómo se revisó y validó lo generado.
16. **Guarde las salidas en bruto.** Un modelo no siempre devuelve lo mismo. Si el cuaderno llama a un modelo, fije el modelo, la versión y los parámetros, y haga que los resultados se reproduzcan desde las salidas guardadas, no desde una nueva llamada.
17. **Declare los sesgos heredados.** Los textos de los que aprenden los modelos reflejan los mismos sesgos de reporte que los registros de desastres: geográficos, de umbral y de contabilidad (CRED, 2026, sección 5.2). Wiley (s. f.) pide evaluar los sesgos de las salidas. La extensión de los sesgos de reporte a los modelos de lenguaje es una inferencia de la SCR.

### Código

18. **Lea, pruebe y revise todo el código generado.** Los ejemplos de declaración de Wiley (s. f.) indican que el código generado fue revisado, probado y corregido por los autores, que confirmaron la exactitud y la reproducibilidad.
19. **Ejecute el cuaderno desde cero en un entorno limpio**, como ya pide la [guía de la colección](01-cuadernos-de-conocimiento.md). Un script que parece correcto no es un script que funciona.
20. **Verifique las dependencias que la IA sugiera.** Compruebe que el paquete existe, fije la versión en `environment.yml` y revise su licencia.

### Figuras y mapas

21. **Genere las figuras y los mapas con código, a partir de los datos.** Las visualizaciones de datos solo se admiten cuando derivan directamente de los datos subyacentes (Elsevier, s. f.; Wiley, s. f.).
22. **No use IA generativa para crear o retocar imágenes de datos observados**, de mediciones ni de resultados. En un cuaderno de riesgo, eso incluye mapas de amenaza, imágenes satelitales y fotografías de daños (Elsevier, s. f.; Springer Nature, s. f.; Wiley, s. f.).
23. **Declare las ilustraciones conceptuales** hechas con IA, en el pie de figura y en la declaración (Elsevier, s. f.; NHESS, s. f.; Wiley, s. f.).

### Confidencialidad, derechos y equidad

24. **No envíe a una IA pública** datos personales, datos de comunidades, información no publicada o con restricciones de licencia. Las editoriales exigen proteger la confidencialidad (Springer Nature, s. f.; Wiley, s. f.), y esto se suma a los principios CARE (Carroll et al., 2020) de los requisitos para datos. Revise también si los términos de la fuente permiten enviarla a un tercero.
25. **Lea los términos de la herramienta.** El proveedor no debe adquirir derechos sobre su contenido ni poder entrenar su modelo con él (Wiley, s. f.).
26. **Use la IA para ampliar el acceso, no para ampliar brechas.** Una traducción asistida o un resumen en lenguaje sencillo pueden ayudar a las comunidades que usan los datos; revíselos con personas del territorio.

### Evaluación de cuadernos

27. **Quien evalúa cuadernos no los sube a una IA pública**, y el informe de evaluación lo redacta una persona (Elsevier, s. f.; NHESS, s. f.; Springer Nature, s. f.; Wiley, s. f.).

### Agentes, conectores y servidores MCP

Un asistente en modo agente (Claude Code, Codex o Copilot en modo agente, por ejemplo) lee archivos, ejecuta comandos y, mediante conectores o servidores del Model Context Protocol, consulta servicios externos como el correo, el almacenamiento en la nube, un gestor de referencias o una base bibliográfica. Las editoriales no regulan todavía este uso; las tres recomendaciones siguientes son criterios propios de la SCR, con apoyo en la especificación del Model Context Protocol [MCP] (MCP, s. f.-a, s. f.-b) y en la lista OWASP Top 10 para aplicaciones con LLM (OWASP Foundation, 2025), consultadas el 19 de noviembre de 2026.

28. **Declare el arnés, los conectores y los permisos.** Liste el asistente y el entorno desde el que lo usó (por ejemplo, una CLI, una extensión de VS Code o una aplicación de escritorio), con su versión, y los conectores y los servidores MCP habilitados (nombre, origen y versión) y qué podían hacer: leer, escribir o ejecutar. Las herramientas de MCP representan ejecución arbitraria de código y el cliente debe obtener el consentimiento de la persona antes de invocarlas (MCP, s. f.-b).
29. **Dé el menor acceso necesario y trate los servidores como código de terceros.** Instale solo servidores de origen verificable y con versión fijada, y lea el comando que los inicia: un servidor local corre con los mismos privilegios que el cliente (MCP, s. f.-a). Conceda primero permisos de lectura, y no conecte carpetas, cuentas ni bases con datos personales, de comunidades o con restricciones de licencia. Las descripciones de las herramientas deben considerarse no confiables si el servidor no lo es (MCP, s. f.-b), y el texto que devuelve un conector (un correo, un documento, una página web) puede traer instrucciones ocultas que desvíen al agente (OWASP Foundation, 2025, LLM01).
30. **No deje que un conector sea la fuente de un dato.** Lo que el agente trae por un conector es una consulta, no una fuente citable. Reconstruya la descarga con un script del cuaderno desde la fuente original, o guarde en bruto la consulta, la fecha y la salida, como pide la recomendación 16.

## Cómo declarar el uso de IA

### Qué debe incluir una declaración

Una declaración completa combina lo que piden Wiley (s. f.) y Springer Nature (s. f.) y responde:

- **Herramienta y versión**: nombre y modelo, por ejemplo «Claude Sonnet 5.5».
- **Fecha** o periodo de uso.
- **Para qué** se usó y **en qué partes** del cuaderno.
- **Qué hizo la persona**: cómo dirigió, revisó y verificó el resultado.
- **Qué datos se enviaron a la herramienta** y cómo se protegió la privacidad.
- **Qué conectores o servidores MCP** tuvo habilitados el asistente y con qué permisos, si lo usó en modo agente.
- **Dónde están los prompts** y los parámetros.

### Plantilla de declaración

Pegue esta plantilla en el cuaderno y en el repositorio. Si no usó IA, reemplácela por la frase «No se usó inteligencia artificial en la preparación de este trabajo».

```markdown
## Declaración de uso de inteligencia artificial

- **Herramienta y versión:** <nombre y modelo>
- **Entorno o cliente:** <CLI, extensión del editor o aplicación, con su versión; solo si usó un asistente en modo agente>
- **Fecha de uso:** <AAAA-MM>
- **Para qué se usó:** <por ejemplo, escribir un primer borrador del script de descarga; traducir el resumen al inglés>
- **Dónde se usó:** <secciones, notebooks o archivos>
- **Revisión humana:** <qué se leyó, qué pruebas se ejecutaron, cómo se verificaron las citas>
- **Datos enviados a la herramienta:** <ninguno | solo texto público | ...>
- **Conectores, servidores MCP y permisos:** <ninguno | nombre, origen, versión y permisos (lectura, escritura, ejecución)>
- **Prompts y salidas:** <ruta en el repositorio, por ejemplo `AI_USE.md`>

Las personas autoras revisaron todo el contenido generado con IA y asumen la responsabilidad total por su exactitud e integridad.
```

**Ejemplo de redacción**, basado en los modelos de declaración de Elsevier (s. f.) y Wiley (s. f.): «Durante la preparación de este trabajo, las autoras y los autores usaron Claude Sonnet 5.5 (consultado en noviembre de 2026) para escribir un primer borrador de los scripts de descarga y para traducir el resumen al inglés. El código fue leído, ejecutado en un entorno limpio y corregido por el equipo, y las citas se verificaron una a una. No se enviaron datos personales a la herramienta. Los autores asumen la responsabilidad total por el contenido».

### Registro de uso: `AI_USE.md`

Lleve un registro en el repositorio, una fila por uso. Es la fuente de la que sale la declaración y la evidencia ante una consulta.

```markdown
| Fecha | Herramienta y versión | Para qué | Archivo | Riesgo | Revisión humana | Prompts |
|---|---|---|---|---|---|---|
| <AAAA-MM-DD> | <modelo> | <tarea> | <ruta> | verde/ámbar | <qué se hizo> | <ruta o enlace> |
```

## Lista de verificación de uso de IA

Marque cada punto antes de entregar el cuaderno. Los criterios críticos son compuertas: si uno falla, el cuaderno no se entrega hasta corregirlo.

**Responsabilidad y autoría**

- [ ] **U01.** **Crítico.** Ninguna herramienta de IA figura como autora ni coautora (Elsevier, s. f.; ICMJE, s. f.; Nature Climate Change, s. f.; Springer Nature, s. f.).
- [ ] **U02.** Cada persona autora revisó, editó y asume la responsabilidad de todo el contenido, incluido el generado con IA (Elsevier, s. f.; ICMJE, s. f.; Springer Nature, s. f.; Wiley, s. f.).
- [ ] **U03.** Las conclusiones y la interpretación del riesgo son humanas: la IA no las determinó (Nature Climate Change, s. f.).

**Transparencia y declaración**

- [ ] **U04.** **Crítico.** Existe una declaración de uso de IA en el cuaderno y en el repositorio, o la frase «No se usó IA» (Elsevier, s. f.; NHESS, s. f.; Springer Nature, s. f.; Wiley, s. f.).
- [ ] **U05.** La declaración indica herramienta, versión, fecha, para qué se usó, en qué secciones y qué revisó la persona (Springer Nature, s. f.; Wiley, s. f.).
- [ ] **U06.** Los prompts y los parámetros relevantes se conservan en el repositorio (`AI_USE.md` o equivalente) (Springer Nature, s. f.; Wiley, s. f.).
- [ ] **U07.** El uso en metodología, código o análisis se declara en Métodos; el de redacción o traducción, en Agradecimientos; el de figuras, en el pie de figura (NHESS, s. f.; Wiley, s. f.).
- [ ] **U08.** Se revisó la política de IA de la revista o del repositorio de destino antes de enviar (Nature Climate Change, s. f.).

**Integridad de datos, citas y resultados**

- [ ] **U09.** **Crítico.** No se fabricaron ni alteraron datos, citas ni resultados con IA (NHESS, s. f.; Nature Climate Change, s. f.).
- [ ] **U10.** Cada referencia existe, su DOI resuelve y respalda lo que el texto afirma (Elsevier, s. f.; Springer Nature, s. f.).
- [ ] **U11.** Los datos extraídos o transformados con un modelo de lenguaje se documentan como datos derivados: modelo, versión, prompt, parámetros, muestra de validación y tasa de error (Wiley, s. f.).
- [ ] **U12.** Las salidas de IA que alimentan resultados se guardaron en bruto, y el cuaderno no depende de una llamada en vivo a un modelo para reproducirse (o fija modelo, versión y parámetros).
- [ ] **U13.** Se comprobó que lo generado no contiene plagio ni material con derechos de terceros (ICMJE, s. f.; Wiley, s. f.).

**Código**

- [ ] **U14.** El código generado con IA fue leído, probado y revisado por una persona (Wiley, s. f.).
- [ ] **U15.** El cuaderno se ejecuta de principio a fin en un entorno limpio.
- [ ] **U16.** Las dependencias sugeridas por la IA existen, están fijadas en `environment.yml` y su licencia es compatible.

**Figuras y mapas**

- [ ] **U17.** Las figuras y los mapas de datos se generan con código a partir de los datos, no con imágenes generativas (Elsevier, s. f.; Wiley, s. f.).
- [ ] **U18.** **Crítico.** Ninguna imagen creada o editada con IA representa datos observados, mediciones o resultados (Elsevier, s. f.; Springer Nature, s. f.; Wiley, s. f.).
- [ ] **U19.** Las ilustraciones conceptuales hechas con IA se declaran en el pie de figura y en la declaración (Elsevier, s. f.; NHESS, s. f.; Wiley, s. f.).

**Confidencialidad, derechos y equidad**

- [ ] **U20.** **Crítico.** No se envió a una IA pública información personal, sensible, de comunidades, no publicada o con restricciones de licencia (Carroll et al., 2020; Springer Nature, s. f.; Wiley, s. f.).
- [ ] **U21.** Se revisaron los términos de la herramienta: no adquiere derechos sobre el contenido ni lo usa para entrenarse (Wiley, s. f.).
- [ ] **U22.** Se evaluaron los sesgos de las salidas, sobre todo los geográficos y de fuentes (CRED, 2026; Wiley, s. f.).
- [ ] **U23.** Quien evalúa cuadernos no sube los materiales en evaluación a una IA pública (Elsevier, s. f.; NHESS, s. f.; Springer Nature, s. f.; Wiley, s. f.).

**Agentes, conectores y MCP**

- [ ] **U24.** Si se usó un asistente en modo agente, la declaración indica el entorno desde el que se usó y lista los conectores y los servidores MCP habilitados (nombre, origen verificable y versión) y los permisos que tuvieron (MCP, s. f.-b; criterio propio de la SCR).
- [ ] **U25.** Los conectores y los servidores MCP no dieron acceso a información personal, de comunidades, no publicada o con restricciones de licencia, y los permisos se limitaron a lo necesario (MCP, s. f.-a, s. f.-b).
- [ ] **U26.** Los datos y las referencias que llegaron por un conector se descargaron de nuevo desde su fuente con un script del cuaderno, o se guardaron en bruto con la consulta y la fecha; el cuaderno no depende del conector para reproducirse.

## Prompt para el checklist de uso de IA

Este prompt convierte la lista de verificación en una auditoría repetible: revisa el repositorio y el texto de un cuaderno, busca indicios de uso de IA, contrasta lo declarado con lo detectado y genera un **reporte de cumplimiento** en Markdown y JSON. Funciona con un asistente que pueda leer archivos y ejecutar comandos.

**Cómo usarlo**

1. Copie el prompt y reemplace los valores entre `<>` de la sección ENTRADAS.
2. Ejecútelo desde el repositorio. Para comprobar DOI y paquetes, use el modo `con_red`.
3. Revise el reporte con una persona. **Es una ayuda para la revisión, no un veredicto.** Las discrepancias se aclaran con quien escribió el cuaderno.

:::{warning} Lo que este prompt no puede hacer
No puede probar que un texto o un código fue escrito por una IA, ni distinguir con certeza lo generado de lo escrito a mano. Las señales que busca (firmas en el historial de git, archivos de configuración de asistentes, llamadas a modelos, referencias que no resuelven) son **indicios**, y el prompt le ordena no acusar a nadie. Tampoco decide cuestiones de consentimiento, datos de comunidades o derechos de terceros: las marca para revisión humana.

Si el auditor es un servicio externo, aplíquele las mismas reglas que a cualquier IA: no le entregue datos personales, datos de comunidades ni material con restricciones de licencia. El prompt le pide citar solo nombres de archivos y de columnas. Si cambia la lista de verificación, actualice también los criterios del prompt.
:::

````text
Actúa como auditor de integridad y ética del uso de inteligencia artificial (IA) en la Subdirección para el Conocimiento del Riesgo (UNGRD). Tu tarea es VERIFICAR si un cuaderno reproducible y su repositorio cumplen la lista de verificación de los «Requisitos para el uso de IA» y producir un REPORTE DE CUMPLIMIENTO. Eres un revisor: NO modifiques ningún archivo.

## ENTRADAS
- RUTA_REPO: <ruta local del repositorio del cuaderno>
- TEXTO (opcional): <ruta del manuscrito, del cuaderno .md/.ipynb o del PDF>
- DESTINO (opcional): <revista o repositorio de destino y enlace a su política de IA>
- MODO: "estatico" (solo leer archivos e historial local) o "con_red" (además puedes comprobar DOI y paquetes). Si no lo indico, usa "estatico".
- CONECTORES (opcional): <lista de conectores y servidores MCP que reporta el propio cliente del asistente, o «ninguno»>. La configuración de usuario no está en el repositorio, así que sin este dato U25 queda «No verificable».
- SALIDA: carpeta donde escribir `reporte_uso_ia.md` y `reporte_uso_ia.json`; si no la indico, imprime el reporte.

## REGLAS DE CONDUCTA (obligatorias)
1. Toda afirmación cita su evidencia: archivo y línea, hash de commit, o salida de un comando. Sin evidencia, el estado es «No verificable».
2. Las señales de uso de IA son indicios, no pruebas. No acuses de mala conducta ni afirmes que un texto «fue escrito por IA». Si algo parece no declarado, repórtalo como «Discrepancia a aclarar con la persona autora».
3. No inventes. No supongas que algo cumple. Distingue «No aplica» (con la razón) de «No cumple».
4. Solo lectura. No ejecutes código del cuaderno que no hayas leído. Si eres un servicio externo, trabaja solo con el material que la persona autorizó, y no copies al reporte valores de columnas ni fragmentos con datos personales: cita solo nombres de archivos y de columnas.
5. Las decisiones éticas y legales (consentimiento, datos de comunidades, derechos de terceros) no son tuyas: márcalas «Requiere revisión humana».
6. No evalúes el mérito científico. Evalúa transparencia, responsabilidad, integridad y confidencialidad.

## PROCEDIMIENTO
### Paso A. Declaraciones
Busca la declaración de uso de IA en `AI_USE.md`, `README.md`, `DATA_STATEMENT.md`, el cuaderno o el manuscrito (secciones Métodos, Agradecimientos, pies de figura). Para cada declaración extrae: herramienta, versión, fecha, propósito, secciones afectadas, revisión humana, datos enviados a la herramienta, conectores o servidores MCP con sus permisos y ubicación de los prompts. Anota qué falta.

### Paso B. Señales de uso de IA (indicios)
1. Historial de git: busca firmas o menciones de asistentes en mensajes y en las líneas `Co-Authored-By` (`git log --format='%H %an %s%n%b'`). Cuenta los commits con rastro y el total, y compara con lo declarado. Revisa también `git status`: los cambios sin commit no dejan rastro en el historial y se reportan como «No verificable».
2. Archivos de configuración de asistentes: `CLAUDE.md`, `AGENTS.md`, `.cursorrules`, `.github/copilot-instructions.md`, carpetas `.claude/` o similares. Configuración de conectores y de servidores MCP: `.mcp.json`, `.cursor/mcp.json`, `.vscode/mcp.json` o cualquier archivo con una clave `mcpServers`. Reporta el nombre de cada servidor, su origen, su versión y sus permisos, sin copiar claves ni tokens.
3. Código que llama a modelos: importaciones o claves de OpenAI, Anthropic, Google, Hugging Face, `transformers`, `langchain` y similares. Para cada llamada: modelo, versión, parámetros (temperatura, semilla) y si las salidas se guardan en bruto.
4. Datos derivados de modelos de lenguaje: scripts o columnas que indiquen extracción, clasificación o resumen con LLM. ¿Hay prompt, muestra de validación y tasa de error?
5. Referencias: comprueba que cada una existe. En modo "con_red", resuelve el DOI y compara título, año y autores con el registro; señala DOI inexistentes, o referencias cuyos datos no coinciden.
6. Dependencias: en modo "con_red", comprueba que cada paquete de `environment.yml` o `requirements.txt` existe en el índice correspondiente y que tiene versión fijada y licencia.
7. Figuras: toda figura o mapa de `images/` debe tener un script o celda que la produzca a partir de los datos. Señala imágenes sin origen reproducible.
8. Confidencialidad: revisa si los prompts guardados, `AI_USE.md` o el historial contienen datos personales, de comunidades o información con restricciones de licencia. Reporta dónde, no el contenido.
9. Contraste: compara lo declarado con lo detectado. Cualquier diferencia es una discrepancia a aclarar.

### Paso C. Clasificación de cada uso por riesgo
Clasifica cada uso de IA que encuentres (declarado o detectado):
- VERDE (permitido): pulir el idioma, sugerir estructura, depurar errores, formatear código, documentar, limpiar o deduplicar datos, comparar opciones metodológicas.
- ÁMBAR (permitido con verificación y declaración): escribir scripts o pipelines de análisis, traducir, reorganizar argumentos, resumir o buscar literatura, extraer datos con un modelo de lenguaje, identificar patrones exploratorios, explicar resultados estadísticos, ilustraciones conceptuales, dar a un agente acceso a su equipo, a su repositorio o a conectores y servidores MCP.
- ROJO (no permitido): fabricar datos, citas o resultados; presentar como propias hipótesis o conclusiones generadas por IA; generar o alterar imágenes de datos observados o resultados; atribuir autoría a una IA; subir información confidencial a una IA pública; delegar la evaluación por pares en una IA.
Para cada uso reporta: categoría, ¿está declarado?, ¿tiene revisión humana demostrable?

### Paso D. Evaluación de criterios
Evalúa los 26 criterios. Para cada uno asigna exactamente un estado: Cumple, Parcial, No cumple, No aplica o No verificable. Los marcados (CRÍTICO) son compuertas bloqueantes.

### Responsabilidad y autoría
U01 (CRÍTICO). Ninguna herramienta de IA figura como autora ni coautora (Elsevier, s. f.; ICMJE, s. f.; Nature Climate Change, s. f.; Springer Nature, s. f.).
U02. Cada persona autora revisó, editó y asume la responsabilidad de todo el contenido, incluido el generado con IA (Elsevier, s. f.; ICMJE, s. f.; Springer Nature, s. f.; Wiley, s. f.).
U03. Las conclusiones y la interpretación del riesgo son humanas: la IA no las determinó (Nature Climate Change, s. f.).

### Transparencia y declaración
U04 (CRÍTICO). Existe una declaración de uso de IA en el cuaderno y en el repositorio, o la frase «No se usó IA» (Elsevier, s. f.; NHESS, s. f.; Springer Nature, s. f.; Wiley, s. f.).
U05. La declaración indica herramienta, versión, fecha, para qué se usó, en qué secciones y qué revisó la persona (Springer Nature, s. f.; Wiley, s. f.).
U06. Los prompts y los parámetros relevantes se conservan en el repositorio (`AI_USE.md` o equivalente) (Springer Nature, s. f.; Wiley, s. f.).
U07. El uso en metodología, código o análisis se declara en Métodos; el de redacción o traducción, en Agradecimientos; el de figuras, en el pie de figura (NHESS, s. f.; Wiley, s. f.).
U08. Se revisó la política de IA de la revista o del repositorio de destino antes de enviar (Nature Climate Change, s. f.).

### Integridad de datos, citas y resultados
U09 (CRÍTICO). No se fabricaron ni alteraron datos, citas ni resultados con IA (NHESS, s. f.; Nature Climate Change, s. f.).
U10. Cada referencia existe, su DOI resuelve y respalda lo que el texto afirma (Elsevier, s. f.; Springer Nature, s. f.).
U11. Los datos extraídos o transformados con un modelo de lenguaje se documentan como datos derivados: modelo, versión, prompt, parámetros, muestra de validación y tasa de error (Wiley, s. f.).
U12. Las salidas de IA que alimentan resultados se guardaron en bruto, y el cuaderno no depende de una llamada en vivo a un modelo para reproducirse (o fija modelo, versión y parámetros).
U13. Se comprobó que lo generado no contiene plagio ni material con derechos de terceros (ICMJE, s. f.; Wiley, s. f.).

### Código
U14. El código generado con IA fue leído, probado y revisado por una persona (Wiley, s. f.).
U15. El cuaderno se ejecuta de principio a fin en un entorno limpio.
U16. Las dependencias sugeridas por la IA existen, están fijadas en `environment.yml` y su licencia es compatible.

### Figuras y mapas
U17. Las figuras y los mapas de datos se generan con código a partir de los datos, no con imágenes generativas (Elsevier, s. f.; Wiley, s. f.).
U18 (CRÍTICO). Ninguna imagen creada o editada con IA representa datos observados, mediciones o resultados (Elsevier, s. f.; Springer Nature, s. f.; Wiley, s. f.).
U19. Las ilustraciones conceptuales hechas con IA se declaran en el pie de figura y en la declaración (Elsevier, s. f.; NHESS, s. f.; Wiley, s. f.).

### Confidencialidad, derechos y equidad
U20 (CRÍTICO). No se envió a una IA pública información personal, sensible, de comunidades, no publicada o con restricciones de licencia (Carroll et al., 2020; Springer Nature, s. f.; Wiley, s. f.).
U21. Se revisaron los términos de la herramienta: no adquiere derechos sobre el contenido ni lo usa para entrenarse (Wiley, s. f.).
U22. Se evaluaron los sesgos de las salidas, sobre todo los geográficos y de fuentes (CRED, 2026; Wiley, s. f.).
U23. Quien evalúa cuadernos no sube los materiales en evaluación a una IA pública (Elsevier, s. f.; NHESS, s. f.; Springer Nature, s. f.; Wiley, s. f.).

### Agentes, conectores y MCP
U24. Si se usó un asistente en modo agente, la declaración indica el entorno desde el que se usó y lista los conectores y los servidores MCP habilitados (nombre, origen verificable y versión) y los permisos que tuvieron (MCP, s. f.-b; criterio propio de la SCR).
U25. Los conectores y los servidores MCP no dieron acceso a información personal, de comunidades, no publicada o con restricciones de licencia, y los permisos se limitaron a lo necesario (MCP, s. f.-a, s. f.-b).
U26. Los datos y las referencias que llegaron por un conector se descargaron de nuevo desde su fuente con un script del cuaderno, o se guardaron en bruto con la consulta y la fecha; el cuaderno no depende del conector para reproducirse.

### Paso E. Puntuación
- Cumple = 1, Parcial = 0,5, No cumple = 0. «No aplica» y «No verificable» no entran en el denominador, pero repórtalos con su conteo.
- Puntaje por grupo y total = suma de puntos ÷ criterios evaluables × 100, con un decimal.
- Nivel: 90 o más, «Alto»; de 75 a 89,9, «Aceptable»; de 50 a 74,9, «Mejorable»; menos de 50, «Insuficiente».
- Si la declaración dice que no se usaron conectores ni servidores MCP, U24, U25 y U26 son «No aplica».
- Compuertas: si algún criterio CRÍTICO está en «No cumple» o hay un uso ROJO, el resultado global es «NO APTO». Si alguno está en «No verificable», es «PENDIENTE DE VERIFICACIÓN».

### Paso F. Redacta el reporte con esta estructura exacta
1. **Resumen ejecutivo**: resultado global, puntaje y nivel, usos de riesgo ámbar y rojo, y las tres prioridades más urgentes, en menos de 150 palabras.
2. **Alcance y método**: ruta auditada, modo, fecha, destino y qué no se pudo revisar.
3. **Inventario de usos de IA**: tabla con uso, herramienta y versión, categoría (verde, ámbar o rojo), ¿declarado?, ¿revisión humana demostrable? y evidencia.
4. **Resultados por criterio**: tabla con ID, criterio, estado, evidencia, acción recomendada y prioridad (Alta, Media o Baja).
5. **Puntaje por grupo**.
6. **Discrepancias a aclarar**: lo detectado que no está declarado, redactado sin acusaciones.
7. **Riesgos de confidencialidad y derechos**: cada uno marcado «Requiere revisión humana».
8. **Declaración sugerida**: borrador de declaración de uso de IA con los datos que sí pudiste confirmar y marcadores `<...>` donde falte información que solo la persona autora conoce.
9. **Plan de mejora** ordenado por prioridad, con esfuerzo estimado (S, M o L).
10. **Limitaciones de esta auditoría**.

### Paso G. Versión legible por máquina
Escribe `reporte_uso_ia.json` con esta forma:
{"repositorio": "...", "fecha": "AAAA-MM-DD", "modo": "...", "resultado_global": "...", "puntaje_total": 0.0, "nivel": "...", "usos": [{"uso": "...", "herramienta": "...", "categoria": "verde|ambar|rojo", "declarado": true, "revision_humana": true, "evidencia": "..."}], "criterios": [{"id": "U00", "estado": "...", "evidencia": "...", "accion": "...", "prioridad": "..."}], "discrepancias": ["..."], "no_verificables": ["U00"]}

Termina con un resumen de cinco líneas y la ruta de los archivos generados.
````

**Compuertas críticas.** El prompt trata como bloqueantes 5 criterios (U01, U04, U09, U18, U20) y también cualquier uso clasificado en rojo: autoría atribuida a una IA, datos, citas o resultados fabricados, imágenes generadas que representan datos, información confidencial enviada a una IA pública, y ausencia de declaración. Esta regla es un criterio propio de la SCR.

## Referencias

Carroll, S. R., Garba, I., Figueroa-Rodríguez, O. L., Holbrook, J., Lovett, R., Materechera, S., Parsons, M., Raseroka, K., Rodriguez-Lonebear, D., Rowe, R., Sara, R., Walker, J. D., Anderson, J., y Hudson, M. (2020). The CARE Principles for Indigenous Data Governance. *Data Science Journal, 19*, Artículo 43. https://doi.org/10.5334/dsj-2020-043

Centre for Research on the Epidemiology of Disasters. (2026). *EM-DAT documentation* (Versión 2026.11) [Documentación en línea]. Université catholique de Louvain. https://doc.emdat.be/

Elsevier. (s. f.). *Generative AI policies for journals*. Recuperado el 16 de noviembre de 2026, de https://www.elsevier.com/about/policies-and-standards/generative-ai-policies-for-journals

International Committee of Medical Journal Editors. (s. f.). *Preparing a manuscript for submission to a medical journal: A. Use of AI by authors* [Recomendaciones del ICMJE, sección V.A]. Recuperado el 16 de noviembre de 2026, de https://www.icmje.org/recommendations/browse/artificial-intelligence/ai-use-by-authors.html

Model Context Protocol. (s. f.-a). *Security best practices* [Especificación del protocolo, versión 2026-07-28]. Recuperado el 19 de noviembre de 2026, de https://modelcontextprotocol.io/specification/latest/basic/security_best_practices

Model Context Protocol. (s. f.-b). *Specification* [Especificación del protocolo, versión 2026-07-28]. Recuperado el 19 de noviembre de 2026, de https://modelcontextprotocol.io/specification/latest

Natural Hazards and Earth System Sciences. (s. f.). *AI policy*. Copernicus Publications y European Geosciences Union. Recuperado el 16 de noviembre de 2026, de https://www.natural-hazards-and-earth-system-sciences.net/policies/ai_policy.html

Nature Climate Change. (s. f.). *Artificial intelligence (AI)*. Springer Nature. Recuperado el 16 de noviembre de 2026, de https://www.nature.com/nclimate/editorial-policies/ai

OWASP Foundation. (2025). *OWASP Top 10 for LLM applications 2025*. Recuperado el 19 de noviembre de 2026, de https://genai.owasp.org/llm-top-10/

Springer Nature. (s. f.). *AI guidance for researchers, editors and reviewers*. Recuperado el 16 de noviembre de 2026, de https://group.springernature.com/gp/group/ai/ai-guidance-for-our-researchers-and-communities

Wiley. (s. f.). *Using AI tools in your research*. Recuperado el 16 de noviembre de 2026, de https://www.wiley.com/en-us/publish/article/ai-guidelines/
