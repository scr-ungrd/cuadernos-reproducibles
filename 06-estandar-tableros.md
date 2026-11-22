---
title: Requisitos para tableros
subtitle: Requisitos para publicar tableros (dashboards) abiertos, accesibles y reproducibles
date: 2026-11-16
authors:
  - name: Subdirección para el Conocimiento del Riesgo
    affiliation: Unidad Nacional para la Gestión del Riesgo de Desastres (UNGRD)
    github: scr-ungrd
site:
  hide_authors: true
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


## 1. Alcance y convenciones

### 1.1 Alcance

Estas instrucciones se aplican a todo **tablero** que acompañe a un cuaderno de la colección o se publique como producto independiente. Un tablero es una página que presenta indicadores, gráficos y mapas de datos ya calculados para que una audiencia los explore o los monitoree. Incluye los tableros estáticos (por ejemplo, Quarto Dashboards u Observable Framework) y los que se apoyan en un servidor.

Se distinguen tres objetos relacionados:

- **Cuaderno**: documenta un análisis, con su texto, su código y sus datos. Es la fuente del método.
- **Tablero**: muestra resultados ya calculados. Es una vista del cuaderno. Se rige por este documento.
- **Aplicación**: recibe entradas de la persona usuaria, ejecuta cálculos o expone una API. Se rige por los [requisitos para aplicaciones](07-estandar-aplicaciones.md). Un tablero que acepta datos de la persona usuaria o ejecuta cálculos propios debe cumplir también esos requisitos. Si el tablero muestra resultados de un modelo, el modelo cumple los [requisitos para modelos](08-estandar-modelos.md).

Complementan la [guía para publicar un cuaderno](01-cuadernos-de-conocimiento.md), los [requisitos para datos](03-estandar-de-datos.md) y los [requisitos para el uso de IA](05-uso-de-ia.md): los datos del tablero cumplen los requisitos para datos y el uso de IA se declara según los requisitos para el uso de IA. La seguridad común a todo repositorio (secretos, datos personales y rutas locales, código no confiable, dependencias y *releases*) la cubren los [requisitos de seguridad](10-requisitos-seguridad.md); los requisitos de seguridad de este documento se aplican además.

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
* - [Requisitos para datos](03-estandar-de-datos.md) y [requisitos para el uso de IA](05-uso-de-ia.md) de esta colección
  - Requisitos para datos, metadatos, licencias y declaración de IA que el tablero hereda
  - DAT, DOC-04, DOC-08
```

## 2. Requisitos

### 2.1 Propósito, alcance y responsabilidad

Esta sección define para quién es el tablero y qué decisión apoya. El término «tablero» cubre usos muy distintos (Sarikaya et al., 2019), por eso el propósito se declara antes de diseñar. Un tablero solo se justifica si hay una necesidad identificada, los datos se actualizan con frecuencia y hay capacidad para mantenerlo; de lo contrario, basta un informe, una tabla o un cuaderno (Analysis Function, 2026a).

En la colección, el cuaderno contiene el método y el tablero es una vista del resultado. El tablero no debe incluir análisis que no esté en el cuaderno (REP-06).

:::{important} PRO-03: un tablero no es una alerta
Un mapa de amenaza o de riesgo puede leerse como un producto oficial. Si la entidad competente no lo autorizó, el aviso dice qué es el tablero, qué no es y dónde consultar la información oficial.
:::

Use esta ficha (`DASHBOARD.md`) como base del aviso, de la sección «Acerca de» y del `README`:

```markdown
# Ficha del tablero

- **Nombre y versión:** <nombre> v<X.Y.Z>
- **Propósito:** <la pregunta que responde>
- **Público y decisiones que apoya:** <quién lo usa y para qué>
- **Qué no es:** <por ejemplo, no es una alerta temprana ni un producto oficial del SNGRD>
- **Cuaderno con el método:** <CRC-00X y enlace>
- **Datos:** <DOI del conjunto archivado, versión y fecha de corte>
- **Periodo y frecuencia de actualización:** <AAAA-MM-DD a AAAA-MM-DD; mensual, anual o versión final>
- **Responsable y contacto:** <persona o dependencia, correo>
- **Criterio de retiro:** <por ejemplo, sin actualización por 12 meses>
```

*Requisitos de este grupo: PRO-01, PRO-02, PRO-03, PRO-04, PRO-05. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.2 Datos del tablero

Los datos del tablero cumplen los [requisitos para datos](03-estandar-de-datos.md). Esta sección agrega tres reglas propias de una visualización pública.

1. **El tablero no es la única vía a los datos.** Cada gráfico ofrece un archivo plano descargable, y no se publica un tablero sin los datos en otra forma (Analysis Function, 2026a, 2026b).
2. **El tablero dice de qué datos se trata.** Muestra la versión, el DOI, el periodo y la fecha de actualización, para que una cifra pueda citarse y verificarse.
3. **La agregación protege a las personas.** Un mapa por manzana o una tabla con pocos casos puede identificar un hogar, aunque los datos de origen estén anonimizados.

Si el tablero consulta una API en vivo, conserve una copia con fecha y muestre cuándo fue la última consulta exitosa. No presente cifras antiguas como vigentes (DAT-08).

*Requisitos de este grupo: DAT-01, DAT-02, DAT-03, DAT-04, DAT-05, DAT-06, DAT-07, DAT-08, DAT-09. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.3 Código, entorno y reproducibilidad

Un tablero es reproducible si otra persona puede reconstruirlo desde cero y obtener las mismas cifras.

- **Prefiera la salida estática.** Un tablero estático solo necesita un servidor web y se publica en GitHub Pages; uno con servidor, como Shiny, no se puede alojar en un sitio genérico (Quarto, s. f.). Con Observable Framework, los cargadores de datos corren al construir el sitio y generan archivos estáticos (Observable, s. f.). Si necesita un servidor, aplique también los [requisitos para aplicaciones](07-estandar-aplicaciones.md).
- **Fije el entorno.** Binder recomienda fijar versiones exactas con `pip freeze` o `conda env export`, y enlazar a un *commit* y no a una rama (Binder Project, s. f.).
- **Use una sola cadena de producción.** Los datos salen de `data/raw` con un script, el cuaderno los consume y el tablero consume los resultados del cuaderno. Así las cifras no pueden diverger.

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

Esta sección evita que la forma de mostrar un dato cambie lo que dice. En un tablero de riesgo, un mapa mal clasificado o una escala truncada puede cambiar una prioridad.

- **Color.** Los mapas de color no uniformes distorsionan los datos, y el arcoíris y el rojo-verde dificultan la lectura con daltonismo. Use paletas perceptualmente uniformes (Crameri et al., 2020). El color nunca es la única señal (W3C, 2024, criterio 1.4.1).
- **Mapas.** Compare tasas y no conteos, declare cómo clasificó los valores y distinga lo observado de lo proyectado (VIS-05 a VIS-07; criterios propios de la SCR).

*Requisitos de este grupo: VIS-01, VIS-02, VIS-03, VIS-04, VIS-05, VIS-06, VIS-07, VIS-08, VIS-09, VIS-10. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.5 Accesibilidad

Todo tablero público cumple WCAG 2.2 niveles A y AA. Ese nivel incluye WCAG 2.1 AA, que la Resolución 1519 de 2020 exige a las entidades públicas en sus portales y sedes electrónicas (MinTIC, 2020, art. 3 y anexo 1; W3C, 2024). El *Analysis Function* reconoce que los tableros rara vez cumplen todo; por eso pide ofrecer los datos en otra forma y publicar una declaración con lo que no se cumple (Analysis Function, 2026a, 2026b).

**Cómo probar.** Las pruebas automáticas (Lighthouse, WAVE) detectan cerca del 30 % de los problemas y no cubren lo interactivo; combínelas con una revisión manual de teclado, zoom y lector de pantalla (Analysis Function, 2026b). La Resolución 1519 trata los validadores automáticos como una verificación final (MinTIC, 2020, anexo 1).

**Costo cero.** Use un lector de pantalla gratuito: NVDA, VoiceOver u Orca. No exigimos JAWS.

Declaración de accesibilidad (`ACCESSIBILITY.md`):

```markdown
# Declaración de accesibilidad

- **Estándar de referencia:** WCAG 2.2, niveles A y AA.
- **Fecha de la última evaluación:** <AAAA-MM-DD>
- **Cómo se evaluó:** <Lighthouse, WAVE, teclado, zoom al 200 %, NVDA o VoiceOver, personas usuarias>
- **Partes que no cumplen:** <por ejemplo, el mapa interactivo no se opera con teclado>
- **Alternativa:** <tabla de datos y archivo CSV descargable>
- **Cuándo se corregirá:** <fecha o versión>
- **Cómo reportar un problema:** <correo o enlace a *issues*>
```

*Requisitos de este grupo: ACC-01, ACC-02, ACC-03, ACC-04, ACC-05, ACC-06, ACC-07, ACC-08, ACC-09, ACC-10, ACC-11, ACC-12. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.6 Privacidad, seguridad y terceros

Un tablero público es una superficie de exposición. Los riesgos más frecuentes son publicar datos que identifican personas (SEG-01), cargar recursos de terceros que cambian o exigen claves (SEG-03) y dejar dependencias desactualizadas (SEG-05).

La Ley 1581 de 2012 establece el régimen general de protección de datos personales (Congreso de la República, 2012). La regla por defecto es no recoger datos personales, ni siquiera con analítica. Para los riesgos técnicos, OWASP Top 10:2025 ubica los fallos de la cadena de suministro en el tercer lugar (A03) y la mala configuración en el segundo (A02) (OWASP Foundation, 2025). En un sitio estático, el control más eficaz es tener pocas dependencias, fijarlas y monitorearlas.

*Requisitos de este grupo: SEG-01, SEG-02, SEG-03, SEG-04, SEG-05, SEG-06. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.7 Documentación, citación y ciclo de vida

El tablero se documenta para responder cinco preguntas: qué es, de dónde salen los datos, cómo se reconstruye, qué cambió y cómo se cita.

- **Cambios.** Cada actualización de datos lleva una nota con lo que cambió y cuándo (Analysis Function, 2026a).
- **Retiro.** Un tablero sin mantenimiento muestra cifras desactualizadas con aspecto de vigentes. Defina criterios de retiro, avise con antelación, conserve los datos y metadatos y archive el código (Analysis Function, 2026a). Deposite la versión final en Zenodo con DOI (PRE-01 de los requisitos para datos).
- **Citación.** Cada versión tiene un DOI y un `CITATION.cff`, que GitHub muestra en el repositorio y Zenodo usa para crear el registro (Citation File Format, s. f.).

*Requisitos de este grupo: DOC-01, DOC-02, DOC-03, DOC-04, DOC-05, DOC-06, DOC-07, DOC-08. Su enunciado completo está en la lista de verificación de la Sección 3.*

## 3. Lista de verificación

La lista tiene 58 requisitos: 52 obligatorios y 6 recomendados. Los 7 requisitos **críticos** (PRO-03, DAT-01, DAT-02, REP-01, REP-02, ACC-02 y SEG-01) bloquean la publicación si no se cumplen.

**Criterio de aceptación.** Un objeto cumple los requisitos si (1) ningún requisito crítico está en incumplimiento y (2) el puntaje de requisitos obligatorios es de 90 o más, calculado como se indica en el prompt de la Sección 4.

**2.1. Propósito, alcance y responsabilidad**

- [ ] **PRO-01.** El tablero declara, en la primera pantalla o en un enlace visible, su propósito, su público y las decisiones que apoya. (Sarikaya et al., 2019; Analysis Function, 2026a)
- [ ] **PRO-02.** El repositorio documenta por qué se justifica un tablero frente a alternativas más simples (cuaderno, tabla descargable, informe) e identifica el cuaderno de la colección que contiene el método. (Analysis Function, 2026a)
- [ ] **PRO-03.** **Crítico.** El tablero no se presenta como alerta, pronóstico ni producto oficial del Sistema Nacional de Gestión del Riesgo de Desastres, salvo autorización escrita de la entidad competente, y lo indica con un aviso visible. (Requisito de esta guía)
- [ ] **PRO-04.** El tablero muestra el periodo que cubre, la fecha de la última actualización de los datos y la frecuencia de actualización prevista. (Analysis Function, 2026a)
- [ ] **PRO-05.** Una persona o dependencia figura como responsable del mantenimiento, con un medio de contacto. (Analysis Function, 2026a)

**2.2. Datos del tablero**

- [ ] **DAT-01.** **Crítico.** Todo conjunto de datos que alimenta el tablero cumple los [requisitos para datos](03-estandar-de-datos.md): licencia, metadatos y ausencia de datos personales. (Requisitos para datos, INV, LIC y PER)
- [ ] **DAT-02.** **Crítico.** Los datos de cada gráfico y de cada mapa se descargan en un archivo plano legible por máquina (CSV o GeoJSON); el tablero no es la única vía de acceso a los datos. (Analysis Function, 2026a; Analysis Function, 2026b; Requisitos para datos, EST-03)
- [ ] **DAT-03.** Un script o flujo versionado regenera los datos del tablero desde `data/raw`, sin ediciones manuales intermedias. (Requisitos para datos, EST-01)
- [ ] **DAT-04.** Cada indicador tiene definición, fórmula, unidad, fuente, periodo y nivel espacial en un glosario accesible desde el tablero. (Requisitos para datos, EST-04 y CAL-11)
- [ ] **DAT-05.** El tablero muestra la versión de los datos y el DOI del conjunto archivado del que se alimenta. (Requisitos para datos, DEP-03 y DEP-04)
- [ ] **DAT-06.** Los valores faltantes se muestran como faltantes, no como cero. (Requisitos para datos, CAL-03)
- [ ] **DAT-07.** Las cifras se agregan o se suprimen cuando un valor permitiría identificar a una persona o una vivienda. (Requisitos para datos, PER-04 y PER-07)
- [ ] **DAT-08.** Si el tablero consulta una API en vivo, conserva una copia con fecha, muestra la fecha de la última consulta exitosa y no presenta datos antiguos como vigentes cuando la consulta falla. (Requisito de esta guía)
- [ ] **DAT-09.** Las limitaciones y los sesgos conocidos de los datos (cobertura, subregistro, resolución) se muestran junto a los resultados que afectan. (Requisitos para datos, VAL-02 y VAL-04)

**2.3. Código, entorno y reproducibilidad**

- [ ] **REP-01.** **Crítico.** El código fuente completo está en un repositorio público con una licencia aprobada por la OSI (MIT o Apache-2.0) y un archivo `LICENSE`; el contenido (texto y figuras) declara CC BY 4.0. (Requisitos para datos, LIC-04; Chue Hong et al., 2022)
- [ ] **REP-02.** **Crítico.** El tablero se reconstruye desde un clon limpio con una orden documentada (por ejemplo, `quarto render`) y produce las mismas cifras; la reconstrucción se prueba en integración continua o en Binder. (Binder Project, s. f.; Requisito de esta guía)
- [ ] **REP-03.** Las dependencias están fijadas por versión en `environment.yml`, `requirements.txt` o un archivo de bloqueo. (Binder Project, s. f.; Wiggins, 2017, factor II)
- [ ] **REP-04.** El tablero se publica como sitio estático; si exige un servidor, el repositorio justifica por qué y documenta cómo ejecutarlo en local. (Quarto, s. f.)
- [ ] **REP-05.** Ninguna clave, token ni contraseña figura en el repositorio ni en su historial; la configuración sensible se lee de variables de entorno. (Wiggins, 2017, factor III; OWASP Foundation, 2025, A02)
- [ ] **REP-06.** Cada cifra y cada figura del tablero sale del mismo código y de los mismos datos que el cuaderno vinculado, o se importa de él. (Requisito de esta guía)
- [ ] **REP-07.** Cada versión publicada tiene un *release* en GitHub, un DOI de Zenodo y un `CITATION.cff` con el ORCID de cada persona autora. (Citation File Format, s. f.; Chue Hong et al., 2022; Requisitos para datos, DEP-06 y DEP-11)
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

- [ ] **SEG-01.** **Crítico.** El tablero no publica datos personales, datos de comunidades ni información pública clasificada o reservada. (Congreso de la República, 2012; Requisitos para datos, PER-02 y GOV-08)
- [ ] **SEG-02.** Si mide el uso (analítica), lo declara, no recoge datos personales y no usa cookies de terceros sin consentimiento. (Congreso de la República, 2012; Analysis Function, 2026a)
- [ ] **SEG-03.** Las bibliotecas, fuentes, mapas base y APIs de terceros figuran con su licencia y sus términos; ninguno exige pago ni una clave privada en el navegador. (Requisito de esta guía)
- [ ] **SEG-04.** El tablero se sirve solo por HTTPS y sin contenido mixto. (OWASP Foundation, 2025, A04)
- [ ] **SEG-05.** Las dependencias tienen alertas automáticas de vulnerabilidades (Dependabot o equivalente). (GitHub, s. f.; OWASP Foundation, 2025, A03)
- [ ] **SEG-06.** *(Recomendado)* Los *scripts* cargados desde redes de distribución externas están fijados por versión. (OWASP Foundation, 2025, A03 y A08)

**2.7. Documentación, citación y ciclo de vida**

- [ ] **DOC-01.** El `README` explica el propósito, cómo reconstruir el tablero, las fuentes de datos, cómo citarlo, la licencia y el contacto. (Digital Public Goods Alliance, s. f., indicador 5)
- [ ] **DOC-02.** El tablero incluye una sección «Acerca de» con las fuentes, las definiciones, las limitaciones, la versión y los enlaces al cuaderno y al repositorio. (Analysis Function, 2026a)
- [ ] **DOC-03.** Un `CHANGELOG.md` registra cada actualización de datos: qué cambió y cuándo. (Analysis Function, 2026a)
- [ ] **DOC-04.** El tablero muestra una cita sugerida con el DOI. (Requisitos para datos, DEP-07)
- [ ] **DOC-05.** Existe un plan de retiro: criterios, aviso visible con antelación (el *Analysis Function* sugiere al menos seis meses), conservación de datos y metadatos y archivo del código. (Analysis Function, 2026a)
- [ ] **DOC-06.** Hay un canal para recibir comentarios (*issues* o correo) y un registro de cómo se atendieron. (Analysis Function, 2026a)
- [ ] **DOC-07.** *(Recomendado)* El tablero se probó con personas usuarias representativas del público al que se dirige. (Analysis Function, 2026a; Analysis Function, 2026b)
- [ ] **DOC-08.** El uso de IA en el código, los textos o las figuras se declara según los [requisitos para el uso de IA](05-uso-de-ia.md). (Requisitos para el uso de IA, U04)

## 4. Prompt para validar los requisitos para tableros

Este prompt convierte la lista de verificación en una auditoría repetible. Lee el repositorio de un tablero, ejecuta comprobaciones automáticas y genera un **reporte de cumplimiento** en Markdown y JSON. Funciona con cualquier asistente de IA que pueda leer archivos y ejecutar comandos.

**Procedimiento de uso**

1. Copie el prompt completo y reemplace los valores entre `<>` de la sección ENTRADAS.
2. Ejecútelo desde un entorno con acceso a los archivos del repositorio. Para comprobar DOI, paquetes, la URL publicada o la ejecución, use el modo ampliado que indica la sección ENTRADAS.
3. Revise el reporte con una persona. Un asistente de IA puede equivocarse al leer un archivo o interpretar un criterio. El resultado es un apoyo a la revisión y no una certificación, y todo lo marcado «Requiere revisión humana» lo decide una persona.
4. Guarde el reporte en el repositorio y repita la auditoría antes de cada *release*.

:::{warning} Lo que este prompt no puede hacer
No puede probar la accesibilidad real de un tablero: Lighthouse y WAVE detectan solo una parte de los problemas, y la revisión con teclado, zoom y lector de pantalla la hace una persona. Tampoco decide si un indicador es adecuado ni si el tablero puede presentarse como un producto oficial; esos puntos se marcan «Requiere revisión humana».

Si el auditor es un servicio externo, aplíquele las mismas reglas que a cualquier IA: no le entregue datos personales, datos de comunidades ni material con restricciones de licencia (véanse los [requisitos para el uso de IA](05-uso-de-ia.md)). Si cambia la lista de verificación, actualice también los criterios del prompt.
:::

````text
Actúa como auditor de tableros (dashboards) abiertos y reproducibles en la Subdirección para el Conocimiento del Riesgo (UNGRD). Tu tarea es VERIFICAR si un tablero y su repositorio cumplen la lista de verificación de los «Requisitos para tableros» y producir un REPORTE DE CUMPLIMIENTO. Eres un revisor: NO modifiques ningún archivo.

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
5. Datos: comprueba que cada gráfico tiene datos descargables, que no hay columnas con nombres de personas, documentos o direcciones exactas, y que los faltantes no son ceros. Aplica los requisitos para datos a los conjuntos usados.
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
DAT-01 (CRÍTICO). Todo conjunto de datos que alimenta el tablero cumple los [requisitos para datos](03-estandar-de-datos.md): licencia, metadatos y ausencia de datos personales. (Requisitos para datos, INV, LIC y PER)
DAT-02 (CRÍTICO). Los datos de cada gráfico y de cada mapa se descargan en un archivo plano legible por máquina (CSV o GeoJSON); el tablero no es la única vía de acceso a los datos. (Analysis Function, 2026a; Analysis Function, 2026b; Requisitos para datos, EST-03)
DAT-03. Un script o flujo versionado regenera los datos del tablero desde `data/raw`, sin ediciones manuales intermedias. (Requisitos para datos, EST-01)
DAT-04. Cada indicador tiene definición, fórmula, unidad, fuente, periodo y nivel espacial en un glosario accesible desde el tablero. (Requisitos para datos, EST-04 y CAL-11)
DAT-05. El tablero muestra la versión de los datos y el DOI del conjunto archivado del que se alimenta. (Requisitos para datos, DEP-03 y DEP-04)
DAT-06. Los valores faltantes se muestran como faltantes, no como cero. (Requisitos para datos, CAL-03)
DAT-07. Las cifras se agregan o se suprimen cuando un valor permitiría identificar a una persona o una vivienda. (Requisitos para datos, PER-04 y PER-07)
DAT-08. Si el tablero consulta una API en vivo, conserva una copia con fecha, muestra la fecha de la última consulta exitosa y no presenta datos antiguos como vigentes cuando la consulta falla. (Requisito de esta guía)
DAT-09. Las limitaciones y los sesgos conocidos de los datos (cobertura, subregistro, resolución) se muestran junto a los resultados que afectan. (Requisitos para datos, VAL-02 y VAL-04)

### Código, entorno y reproducibilidad
REP-01 (CRÍTICO). El código fuente completo está en un repositorio público con una licencia aprobada por la OSI (MIT o Apache-2.0) y un archivo `LICENSE`; el contenido (texto y figuras) declara CC BY 4.0. (Requisitos para datos, LIC-04; Chue Hong et al., 2022)
REP-02 (CRÍTICO). El tablero se reconstruye desde un clon limpio con una orden documentada (por ejemplo, `quarto render`) y produce las mismas cifras; la reconstrucción se prueba en integración continua o en Binder. (Binder Project, s. f.; Requisito de esta guía)
REP-03. Las dependencias están fijadas por versión en `environment.yml`, `requirements.txt` o un archivo de bloqueo. (Binder Project, s. f.; Wiggins, 2017, factor II)
REP-04. El tablero se publica como sitio estático; si exige un servidor, el repositorio justifica por qué y documenta cómo ejecutarlo en local. (Quarto, s. f.)
REP-05. Ninguna clave, token ni contraseña figura en el repositorio ni en su historial; la configuración sensible se lee de variables de entorno. (Wiggins, 2017, factor III; OWASP Foundation, 2025, A02)
REP-06. Cada cifra y cada figura del tablero sale del mismo código y de los mismos datos que el cuaderno vinculado, o se importa de él. (Requisito de esta guía)
REP-07. Cada versión publicada tiene un *release* en GitHub, un DOI de Zenodo y un `CITATION.cff` con el ORCID de cada persona autora. (Citation File Format, s. f.; Chue Hong et al., 2022; Requisitos para datos, DEP-06 y DEP-11)
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
SEG-01 (CRÍTICO). El tablero no publica datos personales, datos de comunidades ni información pública clasificada o reservada. (Congreso de la República, 2012; Requisitos para datos, PER-02 y GOV-08)
SEG-02. Si mide el uso (analítica), lo declara, no recoge datos personales y no usa cookies de terceros sin consentimiento. (Congreso de la República, 2012; Analysis Function, 2026a)
SEG-03. Las bibliotecas, fuentes, mapas base y APIs de terceros figuran con su licencia y sus términos; ninguno exige pago ni una clave privada en el navegador. (Requisito de esta guía)
SEG-04. El tablero se sirve solo por HTTPS y sin contenido mixto. (OWASP Foundation, 2025, A04)
SEG-05. Las dependencias tienen alertas automáticas de vulnerabilidades (Dependabot o equivalente). (GitHub, s. f.; OWASP Foundation, 2025, A03)
SEG-06 (RECOMENDADO). Los *scripts* cargados desde redes de distribución externas están fijados por versión. (OWASP Foundation, 2025, A03 y A08)

### Documentación, citación y ciclo de vida
DOC-01. El `README` explica el propósito, cómo reconstruir el tablero, las fuentes de datos, cómo citarlo, la licencia y el contacto. (Digital Public Goods Alliance, s. f., indicador 5)
DOC-02. El tablero incluye una sección «Acerca de» con las fuentes, las definiciones, las limitaciones, la versión y los enlaces al cuaderno y al repositorio. (Analysis Function, 2026a)
DOC-03. Un `CHANGELOG.md` registra cada actualización de datos: qué cambió y cuándo. (Analysis Function, 2026a)
DOC-04. El tablero muestra una cita sugerida con el DOI. (Requisitos para datos, DEP-07)
DOC-05. Existe un plan de retiro: criterios, aviso visible con antelación (el *Analysis Function* sugiere al menos seis meses), conservación de datos y metadatos y archivo del código. (Analysis Function, 2026a)
DOC-06. Hay un canal para recibir comentarios (*issues* o correo) y un registro de cómo se atendieron. (Analysis Function, 2026a)
DOC-07 (RECOMENDADO). El tablero se probó con personas usuarias representativas del público al que se dirige. (Analysis Function, 2026a; Analysis Function, 2026b)
DOC-08. El uso de IA en el código, los textos o las figuras se declara según los [requisitos para el uso de IA](05-uso-de-ia.md). (Requisitos para el uso de IA, U04)

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
