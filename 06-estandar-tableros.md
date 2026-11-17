---
title: Estándar de tableros
subtitle: Requisitos para publicar tableros (dashboards) abiertos, accesibles y reproducibles
date: 2026-11-16
authors:
  - name: Subdirección para el Conocimiento del Riesgo
    affiliation: Unidad Nacional para la Gestión del Riesgo de Desastres (UNGRD)
    github: scr-ungrd
license: CC-BY-4.0
keywords:
  - tableros
  - dashboards
  - visualización de datos
  - accesibilidad
  - WCAG
  - reproducibilidad
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
  DPG: Digital Public Goods
---

+++ {"part": "abstract"}

Este documento establece los requisitos que debe cumplir un tablero (*dashboard*) de conocimiento del riesgo para publicarse en la colección como un objeto abierto, accesible y reproducible. Define 58 requisitos (52 obligatorios, de ellos 7 críticos, y 6 recomendados), cada uno con un identificador y una base documental citada. Se derivan de la guía del *Government Analysis Function* del Reino Unido para tableros, WCAG 2.2, la Resolución 1519 de 2020 del MinTIC, la literatura sobre diseño de tableros y uso del color, los principios FAIR para software, la guía de despliegue de Quarto y la lista OWASP Top 10:2025. Ningún requisito exige pagos de suscripción ni de licencias. El documento incluye plantillas, una lista de verificación y un prompt que audita el cumplimiento y genera un reporte.

+++

## 1. Alcance y convenciones

### 1.1 Alcance

Estas instrucciones se aplican a todo **tablero** que acompañe a un cuaderno de la colección o se publique como producto independiente. Un tablero es una página que presenta indicadores, gráficos y mapas de datos ya calculados para que una audiencia los explore o los monitoree. Incluye los tableros estáticos (por ejemplo, Quarto Dashboards u Observable Framework) y los que se apoyan en un servidor.

Se distinguen tres objetos relacionados:

- **Cuaderno**: documenta un análisis, con su texto, su código y sus datos. Es la fuente del método.
- **Tablero**: muestra resultados ya calculados. Es una vista del cuaderno. Se rige por este documento.
- **Aplicación**: recibe entradas de la persona usuaria, ejecuta cálculos o expone una API. Se rige por el [estándar de aplicaciones](07-estandar-aplicaciones.md). Un tablero que acepta datos de la persona usuaria o ejecuta cálculos propios debe cumplir también ese estándar.

Complementan la [guía para publicar un cuaderno](01-cuadernos-de-conocimiento.md), el [estándar de datos](03-estandar-de-datos.md) y el [instructivo de uso de IA](05-uso-de-ia.md): los datos del tablero cumplen el primero y el uso de IA se declara según el segundo.

### 1.2 Convenciones

1. **Identificador.** Cada requisito tiene un código de tres letras y dos cifras (por ejemplo, PRO-01). Los códigos se usan en la lista de verificación, en el prompt de validación y en los reportes.
2. **Nivel.** *Obligatorio* significa que el cuaderno, el tablero o la aplicación no se acepta si el requisito aplica y no se cumple. *Recomendado* significa que el cumplimiento mejora la calidad pero no condiciona la aceptación. *Crítico* es un requisito obligatorio cuyo incumplimiento bloquea la publicación, cualquiera sea la puntuación total.
3. **Base.** Entre paréntesis, cada requisito indica el documento, el año y, cuando corresponde, el criterio o el apartado del que procede. Los requisitos cuya base es «Requisito de esta guía» los establece este documento y no provienen de una fuente externa.
4. **Redacción.** Cada requisito se enuncia en el estado conforme: describe cómo es un objeto que lo cumple. Los requisitos que dicen «aplica solo si» se marcan «No aplica» cuando no corresponden.
5. **Citas y traducciones.** Las citas siguen la norma APA 7. Los textos de las fuentes en inglés se traducen al español; las traducciones son propias. Los nombres de campos, códigos y apartados de las fuentes se conservan en su idioma original.
6. **Fecha de consulta.** Las fuentes web sin fecha de publicación se consultaron el 16 de noviembre de 2026 (véanse las Referencias). Los estándares y las guías cambian: antes de publicar, confirme la versión vigente.

### 1.3 Política de costo cero

Ningún requisito de este documento exige comprar suscripciones, licencias ni servicios. Los tableros se pueden construir y publicar con herramientas gratuitas (Quarto, GitHub Pages, Binder), y las pruebas de accesibilidad con herramientas gratuitas (Lighthouse, WAVE) y con un lector de pantalla gratuito (NVDA, VoiceOver u Orca). Los servicios de pago que se mencionan en las fuentes, como JAWS, no se exigen.

### 1.4 Documentos de referencia

**Tabla 1.** Documentos de los que se derivan los requisitos.

```{list-table}
:header-rows: 1

* - Documento
  - Qué establece
  - Requisitos que se derivan
* - Government Analysis Function (2026a, 2026b)
  - Guía oficial del Reino Unido para justificar, construir, probar, mantener y retirar tableros, con pruebas de accesibilidad
  - PRO, DAT-02, ACC, DOC
* - World Wide Web Consortium (2024). WCAG 2.2
  - Criterios de éxito de accesibilidad web (recomendación del W3C)
  - VIS-03, ACC
* - MinTIC (2020). Resolución 1519 de 2020
  - Estándares de accesibilidad web (WCAG 2.1 AA), seguridad digital y datos abiertos para las entidades públicas
  - ACC-01, ACC-03, ACC-06, ACC-10
* - Sarikaya et al. (2019)
  - Espacio de diseño de los tableros a partir de 83 ejemplos
  - PRO-01
* - Crameri et al. (2020)
  - Uso científico del color en visualizaciones
  - VIS-02
* - Quarto (s. f.); Observable (s. f.); Binder Project (s. f.)
  - Despliegue estático de tableros, cargadores de datos y fijación de entornos
  - REP-02 a REP-04
* - Wiggins (2017); OWASP Foundation (2025); GitHub (s. f.)
  - Configuración fuera del código y riesgos de seguridad de aplicaciones web
  - REP-05, SEG
* - Citation File Format (s. f.); Chue Hong et al. (2022); Digital Public Goods Alliance (s. f.)
  - Citación y principios FAIR de software; indicador de documentación de bienes públicos digitales
  - REP-01, REP-07, DOC-01
* - Congreso de la República (2012). Ley 1581 de 2012
  - Régimen general de protección de datos personales
  - SEG-01, SEG-02
* - [Estándar de datos](03-estandar-de-datos.md) y [Uso de IA](05-uso-de-ia.md) de esta colección
  - Requisitos de datos, metadatos, licencias y declaración de IA que el tablero hereda
  - DAT, DOC-04, DOC-08
```

## 2. Requisitos

### 2.1 Propósito, alcance y responsabilidad

Un tablero responde a una pregunta de un público concreto. Sin esa definición, se acumulan indicadores que nadie usa. El término cubre usos muy distintos (Sarikaya et al., 2019), por eso la primera decisión es el propósito, y la segunda, si hace falta un tablero. La guía del *Government Analysis Function* del Reino Unido pide justificarlo antes de construirlo: solo si hay una necesidad identificada, los datos se actualizan con frecuencia y existe capacidad para mantenerlo; si no, basta un informe, una tabla o un cuaderno (Analysis Function, 2026a).

En esta colección el **cuaderno es la fuente del método y el tablero es una vista del resultado**. El tablero no debe contener análisis que no esté en el cuaderno (REP-06).

:::{important} PRO-03: un tablero no es una alerta
Un tablero con mapas de amenaza, exposición o riesgo puede leerse como un producto oficial. Si la entidad competente no lo autorizó, el aviso debe decir qué es, qué no es y a quién acudir para información oficial. Es un criterio propio de la SCR.
:::

Ficha mínima del tablero (`DASHBOARD.md`), de la que salen el aviso, la sección «Acerca de» y el `README`:

```markdown
# Ficha del tablero

- **Nombre y versión:** <nombre> v<X.Y.Z>
- **Propósito:** <la pregunta que responde>
- **Público y decisiones que apoya:** <quién lo usa y para qué>
- **Qué no es:** <por ejemplo, no es una alerta temprana ni un producto oficial del SNGRD>
- **Cuaderno que contiene el método:** <CRC-00X y enlace>
- **Datos:** <DOI del conjunto archivado, versión y fecha de corte>
- **Periodo y frecuencia de actualización:** <AAAA-MM-DD a AAAA-MM-DD; mensual, anual o versión final>
- **Responsable y contacto:** <persona o dependencia, correo>
- **Criterio de retiro:** <por ejemplo, sin actualización por 12 meses>
```

*Requisitos de este grupo: PRO-01, PRO-02, PRO-03, PRO-04, PRO-05. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.2 Datos del tablero

Los datos de un tablero siguen el [estándar de datos](03-estandar-de-datos.md) de la colección: lo que se muestra es un subconjunto de datos que ya están descritos, licenciados y depositados. El tablero agrega tres obligaciones propias de una visualización pública.

La primera es que **el tablero no puede ser la única forma de llegar a los datos**. El estándar de datos ya exige entregarlos completos y en bloque (EST-03), y la guía del *Analysis Function* pide ofrecer un archivo plano descargable de los datos de cada gráfico y no publicar un tablero sin los datos en otra forma (Analysis Function, 2026a, 2026b). La segunda es **mostrar de qué datos se trata**: versión, DOI, periodo y fecha de actualización, para que una cifra pueda citarse y verificarse. La tercera es **proteger a las personas en la agregación**: un mapa por manzana o una tabla con pocos casos puede identificar a un hogar, aunque los datos de origen estén anonimizados.

Si el tablero consulta una API en vivo, la reproducibilidad exige una copia con fecha. El tablero debe mostrar cuándo fue la última consulta exitosa y no ocultar una falla mostrando cifras antiguas como si fueran de hoy (DAT-08).

*Requisitos de este grupo: DAT-01, DAT-02, DAT-03, DAT-04, DAT-05, DAT-06, DAT-07, DAT-08, DAT-09. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.3 Código, entorno y reproducibilidad

Un tablero es reproducible si otra persona puede reconstruirlo desde cero y obtener las mismas cifras. Tres decisiones lo hacen posible.

**Preferir la salida estática.** Los tableros estáticos, como los de Quarto, solo necesitan un servidor web y pueden publicarse en GitHub Pages; los que requieren un servidor de aplicaciones (por ejemplo, Shiny) no se pueden alojar en un sitio web genérico (Quarto, s. f.). Un sitio estático es más barato de mantener, tiene menos superficie de ataque que uno con servidor y se archiva con más facilidad. Con Observable Framework, la lógica es equivalente: los cargadores de datos se ejecutan al construir el sitio y generan archivos estáticos (Observable, s. f.). Si el tablero necesita un servidor, deje de aplicar este estándar de forma exclusiva y aplique también el [estándar de aplicaciones](07-estandar-aplicaciones.md).

**Fijar el entorno.** Binder reconstruye la imagen cuando cambia el repositorio y recomienda fijar las versiones exactas de los paquetes, por ejemplo con `pip freeze` o `conda env export` (Binder Project, s. f.). Apuntar el enlace a un *commit* en lugar de una rama evita reconstrucciones inesperadas.

**Hacer una sola cadena de producción.** Los datos se generan desde `data/raw` con un script, el cuaderno consume esos datos y el tablero consume los resultados del cuaderno. Así las cifras del tablero y las del cuaderno no pueden divergir.

Estructura mínima del repositorio:

```text
tablero-<tema>/
├── README.md              # propósito, cómo reconstruir, cómo citar
├── DASHBOARD.md           # ficha del tablero (Sección 2.1)
├── CITATION.cff           # con ORCID de cada persona autora
├── LICENSE                # código MIT o Apache-2.0
├── CHANGELOG.md           # nota por cada actualización de datos
├── ACCESSIBILITY.md       # declaración de accesibilidad
├── environment.yml        # versiones fijadas
├── data/{raw,interim,processed}/
├── scripts/               # regeneran data/processed desde data/raw
├── metadata/              # sources.csv, data_catalog.csv, rdls/
├── dashboard/             # fuente del tablero (.qmd, .js, .py)
└── .github/workflows/     # reconstrucción y pruebas
```

*Requisitos de este grupo: REP-01, REP-02, REP-03, REP-04, REP-05, REP-06, REP-07, REP-08. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.4 Diseño visual y honestidad gráfica

La honestidad gráfica evita que la forma de mostrar un dato cambie lo que dice. En un tablero de riesgo, un mapa mal clasificado o una escala truncada puede cambiar una prioridad de gestión.

Para el color, Crameri et al. (2020) muestran que los mapas de color no uniformes distorsionan los datos y que los de arcoíris y rojo-verde dificultan la lectura a personas con daltonismo; recomiendan paletas científicas perceptualmente uniformes. WCAG añade que el color no puede ser la única señal (W3C, 2024, criterio 1.4.1).

Para los mapas coropléticos, compare tasas y no conteos, declare cómo se clasificaron los valores y distinga lo observado de lo proyectado. Estos tres puntos (VIS-05 a VIS-07) son criterios propios de la SCR.

*Requisitos de este grupo: VIS-01, VIS-02, VIS-03, VIS-04, VIS-05, VIS-06, VIS-07, VIS-08, VIS-09, VIS-10. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.5 Accesibilidad

La accesibilidad es una condición de uso público, no un añadido final. El *Analysis Function* exige que sus tableros cumplan WCAG 2.2 A y AA, y reconoce que los tableros rara vez cumplen todos los requisitos, por lo que pide planificar la accesibilidad desde el inicio, ofrecer los datos en otra forma y publicar una declaración con lo que no se cumple (Analysis Function, 2026a, 2026b).

En Colombia, la Resolución 1519 de 2020 del MinTIC obliga a las entidades públicas a cumplir WCAG 2.1 nivel AA en sus portales y sedes electrónicas (MinTIC, 2020, art. 3 y anexo 1). Como WCAG 2.2 incluye los criterios de la 2.1 (W3C, 2024), cumplir la 2.2 AA cubre ambas exigencias. Un tablero de la UNGRD o de una entidad territorial puede ser parte de esa sede electrónica.

**Qué probar.** Las pruebas automáticas (Lighthouse, WAVE) detectan solo una parte de los problemas, alrededor del 30 % según el *Analysis Function*, y no cubren los elementos interactivos; por eso se combinan con una revisión manual de teclado, zoom, lector de pantalla y, cuando es posible, personas usuarias (Analysis Function, 2026b). La Resolución 1519 también considera los validadores automáticos solo como una verificación final y no como el método principal de revisión (MinTIC, 2020, anexo 1).

**Costo cero.** El *Analysis Function* menciona JAWS, que es de pago. Este estándar exige un lector de pantalla gratuito (NVDA en Windows, VoiceOver en macOS y iOS u Orca en Linux).

Plantilla de declaración de accesibilidad (`ACCESSIBILITY.md`):

```markdown
# Declaración de accesibilidad

- **Estándar de referencia:** WCAG 2.2, niveles A y AA.
- **Fecha de la última evaluación:** <AAAA-MM-DD>
- **Cómo se evaluó:** <Lighthouse, WAVE, teclado, zoom al 200 %, NVDA o VoiceOver, personas usuarias>
- **Partes que no cumplen:** <por ejemplo, el mapa interactivo no se opera con teclado>
- **Alternativa:** <tabla de datos en `/datos` y archivo CSV descargable>
- **Cuándo se corregirá:** <fecha o versión>
- **Cómo reportar un problema:** <correo o enlace a *issues*>
```

*Requisitos de este grupo: ACC-01, ACC-02, ACC-03, ACC-04, ACC-05, ACC-06, ACC-07, ACC-08, ACC-09, ACC-10, ACC-11, ACC-12. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.6 Privacidad, seguridad y terceros

Un tablero público es una superficie de exposición. Tres riesgos son frecuentes: publicar sin querer datos que identifican personas (SEG-01), cargar recursos de terceros que cambian o exigen claves (SEG-03) y dejar dependencias desactualizadas (SEG-05).

La Ley 1581 de 2012 establece el régimen general de protección de datos personales en Colombia (Congreso de la República, 2012). Un tablero que no recoge datos personales reduce de forma importante sus obligaciones; por eso la regla por defecto es no recogerlos, ni siquiera mediante analítica. El estándar de datos ya prohíbe publicar datos personales o de comunidades sin constancia de autorización (PER-02).

Para los riesgos técnicos, la lista OWASP Top 10:2025 ubica los fallos de la cadena de suministro de software en el tercer lugar (A03) y la mala configuración en el segundo (A02) (OWASP Foundation, 2025). En un sitio estático, el control más eficaz es mantener pocas dependencias, fijarlas y monitorearlas.

*Requisitos de este grupo: SEG-01, SEG-02, SEG-03, SEG-04, SEG-05, SEG-06. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.7 Documentación, citación y ciclo de vida

La documentación de un tablero responde cinco preguntas: qué es, de dónde salen los datos, cómo se reconstruye, qué cambió y cómo se cita. El *Analysis Function* pide una nota de cambio cada vez que se actualizan los datos, con lo que cambió y cuándo, y tratar el tablero como un servicio digital que se mantiene durante toda su vida (Analysis Function, 2026a).

**Ciclo de vida.** Un tablero sin mantenimiento es un riesgo: muestra cifras desactualizadas con aspecto de vigentes. La misma guía propone criterios de retiro (ya no se mantiene, ya no es útil o relevante), un aviso con antelación, la conservación de los datos y los metadatos con una nota de que no se actualizan, y el archivo del código en un repositorio público marcado como archivado (Analysis Function, 2026a). Aquí se agrega el depósito de la versión final en Zenodo con DOI, como ya exige el estándar de datos (PRE-01).

**Citación.** Cada versión del tablero tiene su DOI y un `CITATION.cff`, que GitHub muestra en la página del repositorio y Zenodo aprovecha al crear el registro (Citation File Format, s. f.).

*Requisitos de este grupo: DOC-01, DOC-02, DOC-03, DOC-04, DOC-05, DOC-06, DOC-07, DOC-08. Su enunciado completo está en la lista de verificación de la Sección 3.*

## 3. Lista de verificación

La lista tiene 58 requisitos: 52 obligatorios y 6 recomendados. Los 7 requisitos **críticos** (PRO-03, DAT-01, DAT-02, REP-01, REP-02, ACC-02 y SEG-01) bloquean la publicación si no se cumplen.

**Criterio de aceptación.** Un objeto cumple el estándar si (1) ningún requisito crítico está en incumplimiento y (2) el puntaje de requisitos obligatorios es de 90 o más, calculado como se indica en el prompt de la Sección 4.

**2.1. Propósito, alcance y responsabilidad**

- [ ] **PRO-01.** El tablero declara, en la primera pantalla o en un enlace visible, su propósito, su público y las decisiones que apoya. (Sarikaya et al., 2019; Analysis Function, 2026a)
- [ ] **PRO-02.** El repositorio documenta por qué se justifica un tablero frente a alternativas más simples (cuaderno, tabla descargable, informe) e identifica el cuaderno de la colección que contiene el método. (Analysis Function, 2026a)
- [ ] **PRO-03.** **Crítico.** El tablero no se presenta como alerta, pronóstico ni producto oficial del Sistema Nacional de Gestión del Riesgo de Desastres, salvo autorización escrita de la entidad competente, y lo indica con un aviso visible. (Requisito de esta guía)
- [ ] **PRO-04.** El tablero muestra el periodo que cubre, la fecha de la última actualización de los datos y la frecuencia de actualización prevista. (Analysis Function, 2026a)
- [ ] **PRO-05.** Una persona o dependencia figura como responsable del mantenimiento, con un medio de contacto. (Analysis Function, 2026a)

**2.2. Datos del tablero**

- [ ] **DAT-01.** **Crítico.** Todo conjunto de datos que alimenta el tablero cumple el [estándar de datos](03-estandar-de-datos.md): licencia, metadatos y ausencia de datos personales. (Estándar de datos, INV, LIC y PER)
- [ ] **DAT-02.** **Crítico.** Los datos de cada gráfico y de cada mapa se descargan en un archivo plano legible por máquina (CSV o GeoJSON); el tablero no es la única vía de acceso a los datos. (Analysis Function, 2026a; Analysis Function, 2026b; Estándar de datos, EST-03)
- [ ] **DAT-03.** Un script o flujo versionado regenera los datos del tablero desde `data/raw`, sin ediciones manuales intermedias. (Estándar de datos, EST-01)
- [ ] **DAT-04.** Cada indicador tiene definición, fórmula, unidad, fuente, periodo y nivel espacial en un glosario accesible desde el tablero. (Estándar de datos, EST-04 y CAL-11)
- [ ] **DAT-05.** El tablero muestra la versión de los datos y el DOI del conjunto archivado del que se alimenta. (Estándar de datos, DEP-03 y DEP-04)
- [ ] **DAT-06.** Los valores faltantes se muestran como faltantes, no como cero. (Estándar de datos, CAL-03)
- [ ] **DAT-07.** Las cifras se agregan o se suprimen cuando un valor permitiría identificar a una persona o una vivienda. (Estándar de datos, PER-04 y PER-07)
- [ ] **DAT-08.** Si el tablero consulta una API en vivo, conserva una copia con fecha, muestra la fecha de la última consulta exitosa y no presenta datos antiguos como vigentes cuando la consulta falla. (Requisito de esta guía)
- [ ] **DAT-09.** Las limitaciones y los sesgos conocidos de los datos (cobertura, subregistro, resolución) se muestran junto a los resultados que afectan. (Estándar de datos, VAL-02 y VAL-04)

**2.3. Código, entorno y reproducibilidad**

- [ ] **REP-01.** **Crítico.** El código fuente completo está en un repositorio público con una licencia aprobada por la OSI (MIT o Apache-2.0) y un archivo `LICENSE`; el contenido (texto y figuras) declara CC BY 4.0. (Estándar de datos, LIC-04; Chue Hong et al., 2022)
- [ ] **REP-02.** **Crítico.** El tablero se reconstruye desde un clon limpio con una orden documentada (por ejemplo, `quarto render`) y produce las mismas cifras; la reconstrucción se prueba en integración continua o en Binder. (Binder Project, s. f.; Requisito de esta guía)
- [ ] **REP-03.** Las dependencias están fijadas por versión en `environment.yml`, `requirements.txt` o un archivo de bloqueo. (Binder Project, s. f.; Wiggins, 2017, factor II)
- [ ] **REP-04.** El tablero se publica como sitio estático; si exige un servidor, el repositorio justifica por qué y documenta cómo ejecutarlo en local. (Quarto, s. f.)
- [ ] **REP-05.** Ninguna clave, token ni contraseña figura en el repositorio ni en su historial; la configuración sensible se lee de variables de entorno. (Wiggins, 2017, factor III; OWASP Foundation, 2025, A02)
- [ ] **REP-06.** Cada cifra y cada figura del tablero sale del mismo código y de los mismos datos que el cuaderno vinculado, o se importa de él. (Requisito de esta guía)
- [ ] **REP-07.** Cada versión publicada tiene un *release* en GitHub, un DOI de Zenodo y un `CITATION.cff` con el ORCID de cada persona autora. (Citation File Format, s. f.; Chue Hong et al., 2022; Estándar de datos, DEP-06 y DEP-11)
- [ ] **REP-08.** *(Recomendado)* Una acción de integración continua reconstruye el tablero, valida los enlaces y ejecuta las pruebas de datos en cada cambio. (Requisito de esta guía)

**2.4. Diseño visual y honestidad gráfica**

- [ ] **VIS-01.** Cada gráfico y cada mapa tiene un título que dice qué muestra, con su unidad, su periodo y su fuente. (Requisito de esta guía)
- [ ] **VIS-02.** Las paletas son perceptualmente uniformes y legibles con daltonismo; no se usa arcoíris ni rojo-verde para datos continuos. (Crameri et al., 2020)
- [ ] **VIS-03.** El color no es el único medio de transmitir información: se añade etiqueta, patrón o forma. (W3C, 2024, criterio 1.4.1)
- [ ] **VIS-04.** *(Recomendado)* El tablero usa pocos colores y pocas tipografías, de forma consistente, y da respuesta visual al pasar el cursor y al enfocar. (Analysis Function, 2026b)
- [ ] **VIS-05.** Los ejes y las escalas no distorsionan: las barras parten de cero y las escalas son comparables entre paneles, o la diferencia se señala. (Requisito de esta guía)
- [ ] **VIS-06.** Los mapas coropléticos usan tasas o proporciones y no conteos brutos cuando las unidades difieren en tamaño o población, y declaran el método de clasificación, los cortes, la unidad espacial y el sistema de referencia. (Requisito de esta guía)
- [ ] **VIS-07.** Lo observado, lo estimado y lo proyectado (escenarios) se distinguen visualmente y en el texto, con su incertidumbre. (Requisito de esta guía)
- [ ] **VIS-08.** Los mapas base y las teselas muestran la atribución que exige su licencia. (Requisito de esta guía)
- [ ] **VIS-09.** La información esencial está visible sin interacción; no depende solo de ventanas emergentes (*tooltips*). (Requisito de esta guía)
- [ ] **VIS-10.** *(Recomendado)* El estado de los filtros se refleja en la URL para poder compartir una vista exacta. (Requisito de esta guía)

**2.5. Accesibilidad**

- [ ] **ACC-01.** El tablero se probó contra WCAG 2.2, niveles A y AA, que incluye los criterios de WCAG 2.1 nivel AA que la Resolución 1519 de 2020 exige a las entidades públicas. (W3C, 2024; MinTIC, 2020, art. 3 y anexo 1; Analysis Function, 2026b)
- [ ] **ACC-02.** **Crítico.** Los datos de cada gráfico y de cada mapa están disponibles como tabla en la misma página o en un enlace, de modo que ninguna información dependa de percibir el gráfico. (Analysis Function, 2026a; Analysis Function, 2026b; W3C, 2024, criterio 1.1.1)
- [ ] **ACC-03.** Cada gráfico tiene un texto alternativo que dice qué muestra y cuál es su mensaje principal. (W3C, 2024, criterio 1.1.1; MinTIC, 2020, anexo 1)
- [ ] **ACC-04.** Todo el tablero (filtros, leyendas y elementos del gráfico) se opera con teclado, con foco visible y orden lógico. (W3C, 2024, criterios 2.1.1 y 2.4.7; Analysis Function, 2026b)
- [ ] **ACC-05.** El contraste del texto es de al menos 4,5:1 y el de los elementos gráficos esenciales, de al menos 3:1. (W3C, 2024, criterios 1.4.3 y 1.4.11)
- [ ] **ACC-06.** El contenido se amplía al 200 % sin pérdida de información y no exige desplazamiento horizontal; se probó en un teléfono y una tableta. (W3C, 2024, criterios 1.4.4 y 1.4.10; Analysis Function, 2026b; MinTIC, 2020, anexo 1)
- [ ] **ACC-07.** El HTML es semántico, los encabezados no saltan de nivel y el idioma está declarado (`lang="es"`). (Analysis Function, 2026b; W3C, 2024, criterio 3.1.1)
- [ ] **ACC-08.** El tablero se probó con al menos un lector de pantalla gratuito (NVDA, VoiceOver u Orca). (Analysis Function, 2026b)
- [ ] **ACC-09.** Se ejecutaron pruebas automáticas (Lighthouse, WAVE) y una revisión manual, y se guardó el resultado en el repositorio. (Analysis Function, 2026b)
- [ ] **ACC-10.** Ningún contenido se mueve, parpadea ni se actualiza solo sin aviso y sin un control para detenerlo. (MinTIC, 2020, anexo 1; W3C, 2024, criterio 2.2.2)
- [ ] **ACC-11.** Existe una declaración de accesibilidad que lista los incumplimientos conocidos y cuándo se corregirán. (Analysis Function, 2026b)
- [ ] **ACC-12.** *(Recomendado)* Los elementos que se pulsan miden al menos 24 × 24 píxeles CSS. (W3C, 2024, criterio 2.5.8)

**2.6. Privacidad, seguridad y terceros**

- [ ] **SEG-01.** **Crítico.** El tablero no publica datos personales, datos de comunidades ni información pública clasificada o reservada. (Congreso de la República, 2012; Estándar de datos, PER-02 y GOV-08)
- [ ] **SEG-02.** Si mide el uso (analítica), lo declara, no recoge datos personales y no usa cookies de terceros sin consentimiento. (Congreso de la República, 2012; Analysis Function, 2026a)
- [ ] **SEG-03.** Las bibliotecas, fuentes, mapas base y APIs de terceros figuran con su licencia y sus términos; ninguno exige pago ni una clave privada en el navegador. (Requisito de esta guía)
- [ ] **SEG-04.** El tablero se sirve solo por HTTPS y sin contenido mixto. (OWASP Foundation, 2025, A04)
- [ ] **SEG-05.** Las dependencias tienen alertas automáticas de vulnerabilidades (Dependabot o equivalente). (GitHub, s. f.; OWASP Foundation, 2025, A03)
- [ ] **SEG-06.** *(Recomendado)* Los *scripts* cargados desde redes de distribución externas están fijados por versión. (OWASP Foundation, 2025, A03 y A08)

**2.7. Documentación, citación y ciclo de vida**

- [ ] **DOC-01.** El `README` explica el propósito, cómo reconstruir el tablero, las fuentes de datos, cómo citarlo, la licencia y el contacto. (Digital Public Goods Alliance, s. f., indicador 5)
- [ ] **DOC-02.** El tablero incluye una sección «Acerca de» con las fuentes, las definiciones, las limitaciones, la versión y los enlaces al cuaderno y al repositorio. (Analysis Function, 2026a)
- [ ] **DOC-03.** Un `CHANGELOG.md` registra cada actualización de datos: qué cambió y cuándo. (Analysis Function, 2026a)
- [ ] **DOC-04.** El tablero muestra una cita sugerida con el DOI. (Estándar de datos, DEP-07)
- [ ] **DOC-05.** Existe un plan de retiro: criterios, aviso visible con antelación (el *Analysis Function* sugiere al menos seis meses), conservación de datos y metadatos y archivo del código. (Analysis Function, 2026a)
- [ ] **DOC-06.** Hay un canal para recibir comentarios (*issues* o correo) y un registro de cómo se atendieron. (Analysis Function, 2026a)
- [ ] **DOC-07.** *(Recomendado)* El tablero se probó con personas usuarias representativas del público al que se dirige. (Analysis Function, 2026a; Analysis Function, 2026b)
- [ ] **DOC-08.** El uso de IA en el código, los textos o las figuras se declara según el [instructivo de uso de IA](05-uso-de-ia.md). (Uso de IA, U04)

## 4. Prompt para validar el estándar de tableros

Este prompt convierte la lista de verificación en una auditoría repetible. Lee el repositorio de un tablero, ejecuta comprobaciones automáticas y genera un **reporte de cumplimiento** en Markdown y JSON. Funciona con cualquier asistente de IA que pueda leer archivos y ejecutar comandos.

**Procedimiento de uso**

1. Copie el prompt completo y reemplace los valores entre `<>` de la sección ENTRADAS.
2. Ejecútelo desde un entorno con acceso a los archivos del repositorio. Para comprobar DOI, paquetes y la URL publicada, use el modo `con_red`.
3. Revise el reporte con una persona. Un asistente de IA puede equivocarse al leer un archivo o interpretar un criterio. El resultado es un apoyo a la revisión y no una certificación, y todo lo marcado «Requiere revisión humana» lo decide una persona.
4. Guarde el reporte en el repositorio y repita la auditoría antes de cada *release*.

:::{warning} Lo que este prompt no puede hacer
No puede probar la accesibilidad real de un tablero: Lighthouse y WAVE detectan solo una parte de los problemas, y la revisión con teclado, zoom y lector de pantalla la hace una persona. Tampoco decide si un indicador es adecuado ni si el tablero puede presentarse como un producto oficial; esos puntos se marcan «Requiere revisión humana».

Si el auditor es un servicio externo, aplíquele las mismas reglas que a cualquier IA: no le entregue datos personales, datos de comunidades ni material con restricciones de licencia (véase el [instructivo de uso de IA](05-uso-de-ia.md)). Si cambia la lista de verificación, actualice también los criterios del prompt.
:::

````text
Actúa como auditor de tableros (dashboards) abiertos y reproducibles en la Subdirección para el Conocimiento del Riesgo (UNGRD). Tu tarea es VERIFICAR si un tablero y su repositorio cumplen la lista de verificación del «Estándar de tableros» y producir un REPORTE DE CUMPLIMIENTO. Eres un revisor: NO modifiques ningún archivo.

## ENTRADAS
- RUTA_REPO: <ruta local del repositorio del tablero>
- URL_TABLERO (opcional): <URL del tablero publicado>
- CUADERNO (opcional): <ruta o enlace del cuaderno que contiene el método>
- MODO: "estatico" (solo leer archivos e historial local) o "con_red" (además puedes comprobar DOI, paquetes y la URL publicada). Si no lo indico, usa "estatico".
- SALIDA: carpeta donde escribir `reporte_tablero.md` y `reporte_tablero.json`; si no la indico, imprime el reporte.

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
1. Inventario de archivos: `README.md`, `LICENSE`, `CITATION.cff`, `CHANGELOG.md`, `DASHBOARD.md`, `ACCESSIBILITY.md`, `environment.yml` o archivo de bloqueo, carpeta `dashboard/` y `.github/workflows/`.
2. Reconstrucción: ejecuta en una copia limpia la orden documentada en el `README` (por ejemplo, `quarto render`) y reporta si termina sin errores. Si no se documenta una orden, el estado de REP-02 es «No cumple».
3. Dependencias: comprueba que las versiones están fijadas; en modo "con_red", comprueba que cada paquete existe.
4. Secretos: busca claves, tokens y contraseñas en los archivos y en el historial (`git log -p`); reporta solo archivo y línea, nunca el valor.
5. Datos: comprueba que cada gráfico tiene datos descargables, que no hay columnas con nombres de personas, documentos o direcciones exactas, y que los faltantes no son ceros. Aplica el estándar de datos a los conjuntos usados.
6. Recursos externos: lista las URL de bibliotecas, fuentes tipográficas, teselas y APIs (`https://` en el HTML generado) y revisa su licencia, su versión fijada y si exigen claves.
7. Accesibilidad estática: en el HTML generado revisa `lang`, texto alternativo en imágenes y gráficos, jerarquía de encabezados, etiquetas de controles y contraste de la paleta. En modo "con_red" y con URL_TABLERO, ejecuta Lighthouse y WAVE y guarda los resultados. Los resultados automáticos no sustituyen la revisión con teclado ni con lector de pantalla: márcalos «Requiere prueba manual».

### Paso C. Evaluación de criterios
Evalúa los 58 criterios. Para cada uno asigna exactamente un estado: Cumple, Parcial, No cumple, No aplica o No verificable. Los marcados (CRÍTICO) son compuertas bloqueantes y los marcados (RECOMENDADO) no condicionan la aceptación.

### Propósito, alcance y responsabilidad
PRO-01. El tablero declara, en la primera pantalla o en un enlace visible, su propósito, su público y las decisiones que apoya. (Sarikaya et al., 2019; Analysis Function, 2026a)
PRO-02. El repositorio documenta por qué se justifica un tablero frente a alternativas más simples (cuaderno, tabla descargable, informe) e identifica el cuaderno de la colección que contiene el método. (Analysis Function, 2026a)
PRO-03 (CRÍTICO). El tablero no se presenta como alerta, pronóstico ni producto oficial del Sistema Nacional de Gestión del Riesgo de Desastres, salvo autorización escrita de la entidad competente, y lo indica con un aviso visible. (Requisito de esta guía)
PRO-04. El tablero muestra el periodo que cubre, la fecha de la última actualización de los datos y la frecuencia de actualización prevista. (Analysis Function, 2026a)
PRO-05. Una persona o dependencia figura como responsable del mantenimiento, con un medio de contacto. (Analysis Function, 2026a)

### Datos del tablero
DAT-01 (CRÍTICO). Todo conjunto de datos que alimenta el tablero cumple el [estándar de datos](03-estandar-de-datos.md): licencia, metadatos y ausencia de datos personales. (Estándar de datos, INV, LIC y PER)
DAT-02 (CRÍTICO). Los datos de cada gráfico y de cada mapa se descargan en un archivo plano legible por máquina (CSV o GeoJSON); el tablero no es la única vía de acceso a los datos. (Analysis Function, 2026a; Analysis Function, 2026b; Estándar de datos, EST-03)
DAT-03. Un script o flujo versionado regenera los datos del tablero desde `data/raw`, sin ediciones manuales intermedias. (Estándar de datos, EST-01)
DAT-04. Cada indicador tiene definición, fórmula, unidad, fuente, periodo y nivel espacial en un glosario accesible desde el tablero. (Estándar de datos, EST-04 y CAL-11)
DAT-05. El tablero muestra la versión de los datos y el DOI del conjunto archivado del que se alimenta. (Estándar de datos, DEP-03 y DEP-04)
DAT-06. Los valores faltantes se muestran como faltantes, no como cero. (Estándar de datos, CAL-03)
DAT-07. Las cifras se agregan o se suprimen cuando un valor permitiría identificar a una persona o una vivienda. (Estándar de datos, PER-04 y PER-07)
DAT-08. Si el tablero consulta una API en vivo, conserva una copia con fecha, muestra la fecha de la última consulta exitosa y no presenta datos antiguos como vigentes cuando la consulta falla. (Requisito de esta guía)
DAT-09. Las limitaciones y los sesgos conocidos de los datos (cobertura, subregistro, resolución) se muestran junto a los resultados que afectan. (Estándar de datos, VAL-02 y VAL-04)

### Código, entorno y reproducibilidad
REP-01 (CRÍTICO). El código fuente completo está en un repositorio público con una licencia aprobada por la OSI (MIT o Apache-2.0) y un archivo `LICENSE`; el contenido (texto y figuras) declara CC BY 4.0. (Estándar de datos, LIC-04; Chue Hong et al., 2022)
REP-02 (CRÍTICO). El tablero se reconstruye desde un clon limpio con una orden documentada (por ejemplo, `quarto render`) y produce las mismas cifras; la reconstrucción se prueba en integración continua o en Binder. (Binder Project, s. f.; Requisito de esta guía)
REP-03. Las dependencias están fijadas por versión en `environment.yml`, `requirements.txt` o un archivo de bloqueo. (Binder Project, s. f.; Wiggins, 2017, factor II)
REP-04. El tablero se publica como sitio estático; si exige un servidor, el repositorio justifica por qué y documenta cómo ejecutarlo en local. (Quarto, s. f.)
REP-05. Ninguna clave, token ni contraseña figura en el repositorio ni en su historial; la configuración sensible se lee de variables de entorno. (Wiggins, 2017, factor III; OWASP Foundation, 2025, A02)
REP-06. Cada cifra y cada figura del tablero sale del mismo código y de los mismos datos que el cuaderno vinculado, o se importa de él. (Requisito de esta guía)
REP-07. Cada versión publicada tiene un *release* en GitHub, un DOI de Zenodo y un `CITATION.cff` con el ORCID de cada persona autora. (Citation File Format, s. f.; Chue Hong et al., 2022; Estándar de datos, DEP-06 y DEP-11)
REP-08 (RECOMENDADO). Una acción de integración continua reconstruye el tablero, valida los enlaces y ejecuta las pruebas de datos en cada cambio. (Requisito de esta guía)

### Diseño visual y honestidad gráfica
VIS-01. Cada gráfico y cada mapa tiene un título que dice qué muestra, con su unidad, su periodo y su fuente. (Requisito de esta guía)
VIS-02. Las paletas son perceptualmente uniformes y legibles con daltonismo; no se usa arcoíris ni rojo-verde para datos continuos. (Crameri et al., 2020)
VIS-03. El color no es el único medio de transmitir información: se añade etiqueta, patrón o forma. (W3C, 2024, criterio 1.4.1)
VIS-04 (RECOMENDADO). El tablero usa pocos colores y pocas tipografías, de forma consistente, y da respuesta visual al pasar el cursor y al enfocar. (Analysis Function, 2026b)
VIS-05. Los ejes y las escalas no distorsionan: las barras parten de cero y las escalas son comparables entre paneles, o la diferencia se señala. (Requisito de esta guía)
VIS-06. Los mapas coropléticos usan tasas o proporciones y no conteos brutos cuando las unidades difieren en tamaño o población, y declaran el método de clasificación, los cortes, la unidad espacial y el sistema de referencia. (Requisito de esta guía)
VIS-07. Lo observado, lo estimado y lo proyectado (escenarios) se distinguen visualmente y en el texto, con su incertidumbre. (Requisito de esta guía)
VIS-08. Los mapas base y las teselas muestran la atribución que exige su licencia. (Requisito de esta guía)
VIS-09. La información esencial está visible sin interacción; no depende solo de ventanas emergentes (*tooltips*). (Requisito de esta guía)
VIS-10 (RECOMENDADO). El estado de los filtros se refleja en la URL para poder compartir una vista exacta. (Requisito de esta guía)

### Accesibilidad
ACC-01. El tablero se probó contra WCAG 2.2, niveles A y AA, que incluye los criterios de WCAG 2.1 nivel AA que la Resolución 1519 de 2020 exige a las entidades públicas. (W3C, 2024; MinTIC, 2020, art. 3 y anexo 1; Analysis Function, 2026b)
ACC-02 (CRÍTICO). Los datos de cada gráfico y de cada mapa están disponibles como tabla en la misma página o en un enlace, de modo que ninguna información dependa de percibir el gráfico. (Analysis Function, 2026a; Analysis Function, 2026b; W3C, 2024, criterio 1.1.1)
ACC-03. Cada gráfico tiene un texto alternativo que dice qué muestra y cuál es su mensaje principal. (W3C, 2024, criterio 1.1.1; MinTIC, 2020, anexo 1)
ACC-04. Todo el tablero (filtros, leyendas y elementos del gráfico) se opera con teclado, con foco visible y orden lógico. (W3C, 2024, criterios 2.1.1 y 2.4.7; Analysis Function, 2026b)
ACC-05. El contraste del texto es de al menos 4,5:1 y el de los elementos gráficos esenciales, de al menos 3:1. (W3C, 2024, criterios 1.4.3 y 1.4.11)
ACC-06. El contenido se amplía al 200 % sin pérdida de información y no exige desplazamiento horizontal; se probó en un teléfono y una tableta. (W3C, 2024, criterios 1.4.4 y 1.4.10; Analysis Function, 2026b; MinTIC, 2020, anexo 1)
ACC-07. El HTML es semántico, los encabezados no saltan de nivel y el idioma está declarado (`lang="es"`). (Analysis Function, 2026b; W3C, 2024, criterio 3.1.1)
ACC-08. El tablero se probó con al menos un lector de pantalla gratuito (NVDA, VoiceOver u Orca). (Analysis Function, 2026b)
ACC-09. Se ejecutaron pruebas automáticas (Lighthouse, WAVE) y una revisión manual, y se guardó el resultado en el repositorio. (Analysis Function, 2026b)
ACC-10. Ningún contenido se mueve, parpadea ni se actualiza solo sin aviso y sin un control para detenerlo. (MinTIC, 2020, anexo 1; W3C, 2024, criterio 2.2.2)
ACC-11. Existe una declaración de accesibilidad que lista los incumplimientos conocidos y cuándo se corregirán. (Analysis Function, 2026b)
ACC-12 (RECOMENDADO). Los elementos que se pulsan miden al menos 24 × 24 píxeles CSS. (W3C, 2024, criterio 2.5.8)

### Privacidad, seguridad y terceros
SEG-01 (CRÍTICO). El tablero no publica datos personales, datos de comunidades ni información pública clasificada o reservada. (Congreso de la República, 2012; Estándar de datos, PER-02 y GOV-08)
SEG-02. Si mide el uso (analítica), lo declara, no recoge datos personales y no usa cookies de terceros sin consentimiento. (Congreso de la República, 2012; Analysis Function, 2026a)
SEG-03. Las bibliotecas, fuentes, mapas base y APIs de terceros figuran con su licencia y sus términos; ninguno exige pago ni una clave privada en el navegador. (Requisito de esta guía)
SEG-04. El tablero se sirve solo por HTTPS y sin contenido mixto. (OWASP Foundation, 2025, A04)
SEG-05. Las dependencias tienen alertas automáticas de vulnerabilidades (Dependabot o equivalente). (GitHub, s. f.; OWASP Foundation, 2025, A03)
SEG-06 (RECOMENDADO). Los *scripts* cargados desde redes de distribución externas están fijados por versión. (OWASP Foundation, 2025, A03 y A08)

### Documentación, citación y ciclo de vida
DOC-01. El `README` explica el propósito, cómo reconstruir el tablero, las fuentes de datos, cómo citarlo, la licencia y el contacto. (Digital Public Goods Alliance, s. f., indicador 5)
DOC-02. El tablero incluye una sección «Acerca de» con las fuentes, las definiciones, las limitaciones, la versión y los enlaces al cuaderno y al repositorio. (Analysis Function, 2026a)
DOC-03. Un `CHANGELOG.md` registra cada actualización de datos: qué cambió y cuándo. (Analysis Function, 2026a)
DOC-04. El tablero muestra una cita sugerida con el DOI. (Estándar de datos, DEP-07)
DOC-05. Existe un plan de retiro: criterios, aviso visible con antelación (el *Analysis Function* sugiere al menos seis meses), conservación de datos y metadatos y archivo del código. (Analysis Function, 2026a)
DOC-06. Hay un canal para recibir comentarios (*issues* o correo) y un registro de cómo se atendieron. (Analysis Function, 2026a)
DOC-07 (RECOMENDADO). El tablero se probó con personas usuarias representativas del público al que se dirige. (Analysis Function, 2026a; Analysis Function, 2026b)
DOC-08. El uso de IA en el código, los textos o las figuras se declara según el [instructivo de uso de IA](05-uso-de-ia.md). (Uso de IA, U04)

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
Escribe `reporte_tablero.json` con esta forma:
{"repositorio": "...", "fecha": "AAAA-MM-DD", "modo": "...", "resultado_global": "...", "puntaje_total": 0.0, "nivel": "...", "criterios": [{"id": "XXX-00", "estado": "...", "evidencia": "...", "accion": "...", "prioridad": "..."}], "revision_humana": ["..."], "no_verificables": ["XXX-00"]}

Termina con un resumen de cinco líneas y la ruta de los archivos generados.
````

**Compuertas críticas.** El prompt trata como bloqueantes los 7 criterios críticos y exige además un puntaje de 90 o más en los obligatorios. Estas reglas son criterios propios de la SCR.

## Referencias

Binder Project. (s. f.). *Ensure reproducibility for your Binder*. The Binder Project. Recuperado el 16 de noviembre de 2026, de https://mybinder.readthedocs.io/en/latest/tutorials/reproducibility.html

Chue Hong, N. P., Katz, D. S., Barker, M., y FAIR4RS Working Group. (2022). *FAIR Principles for Research Software (FAIR4RS Principles)* (Versión 1.0) [Recomendación del Research Data Alliance]. https://doi.org/10.15497/RDA00068

Citation File Format. (s. f.). *Citation File Format*. Recuperado el 16 de noviembre de 2026, de https://citation-file-format.github.io/

Congreso de la República de Colombia. (2012). *Ley 1581 de 2012, por la cual se dictan disposiciones generales para la protección de datos personales*.

Crameri, F., Shephard, G. E., y Heron, P. J. (2020). The misuse of colour in science communication. *Nature Communications, 11*, Artículo 5444. https://doi.org/10.1038/s41467-020-19160-7

Digital Public Goods Alliance. (s. f.). *DPG Standard* [Especificación en línea]. GitHub. Recuperado el 16 de noviembre de 2026, de https://github.com/DPGAlliance/DPG-Standard

Government Analysis Function. (2026a). *Data visualisation: building and managing dashboards*. Gobierno del Reino Unido. https://analysisfunction.civilservice.gov.uk/policy-store/data-visualisation-building-and-managing-dashboards

Government Analysis Function. (2026b). *Data visualisation: testing dashboards for design and accessibility*. Gobierno del Reino Unido. https://analysisfunction.civilservice.gov.uk/policy-store/data-visualisation-testing-dashboards-for-design-and-accessibility

GitHub. (s. f.). *Dependabot quickstart guide*. GitHub Docs. Recuperado el 16 de noviembre de 2026, de https://docs.github.com/en/code-security/getting-started/dependabot-quickstart-guide

Ministerio de Tecnologías de la Información y las Comunicaciones. (2020). *Resolución 1519 de 2020, por la cual se definen los estándares y directrices para publicar la información señalada en la Ley 1712 del 2014 y se definen los requisitos materia de acceso a la información pública, accesibilidad web, seguridad digital y datos abiertos* (Diario Oficial n.º 51.521 de 7 de diciembre de 2020). https://normas.cra.gov.co/gestor/docs/resolucion_mintic_1519_2020.htm

Observable. (s. f.). *Data loaders*. Observable Framework. Recuperado el 16 de noviembre de 2026, de https://observablehq.com/framework/data-loaders

OWASP Foundation. (2025). *OWASP Top 10:2025*. https://top10.owasp.org/2025

Quarto. (s. f.). *Dashboard deployment*. Posit. Recuperado el 16 de noviembre de 2026, de https://quarto.org/docs/dashboards/deployment.html

Sarikaya, A., Correll, M., Bartram, L., Tory, M., y Fisher, D. (2019). What do we talk about when we talk about dashboards? *IEEE Transactions on Visualization and Computer Graphics, 25*(1). https://doi.org/10.1109/TVCG.2018.2864903

World Wide Web Consortium. (2024). *Web Content Accessibility Guidelines (WCAG) 2.2* [Recomendación del W3C, 12 de diciembre de 2024]. https://www.w3.org/TR/WCAG22/

Wiggins, A. (2017). *The twelve-factor app*. https://12factor.net/
