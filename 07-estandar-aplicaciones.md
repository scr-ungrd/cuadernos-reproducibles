---
title: Requisitos para aplicaciones
subtitle: Requisitos para publicar aplicaciones abiertas, seguras y reproducibles
date: 2026-11-16
authors:
  - name: Subdirección para el Conocimiento del Riesgo
    affiliation: Unidad Nacional para la Gestión del Riesgo de Desastres (UNGRD)
    github: scr-ungrd
license: CC-BY-4.0
keywords:
  - aplicaciones
  - software abierto
  - reproducibilidad
  - seguridad
  - FAIR4RS
  - bienes públicos digitales
  - accesibilidad
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
  FAIR4RS: FAIR Principles for Research Software
---

+++ {"part": "abstract"}

Este documento establece los requisitos que debe cumplir una aplicación de conocimiento del riesgo (calculadora, visor interactivo con lógica propia, API o herramienta web) para publicarse en la colección como software abierto, seguro y reproducible. Define 62 requisitos (53 obligatorios, de ellos 11 críticos, y 9 recomendados), cada uno con un identificador y una base documental citada. Se derivan del Digital Public Goods Standard, los principios FAIR para software de investigación (FAIR4RS), la metodología de los doce factores, la lista OWASP Top 10:2025, WCAG 2.2, la Resolución 1519 de 2020 del MinTIC y la Ley 1581 de 2012. Ningún requisito exige pagos de suscripción ni de licencias. El documento incluye plantillas, una lista de verificación y un prompt que audita el cumplimiento y genera un reporte.

+++

## 1. Alcance y convenciones

### 1.1 Alcance

Estas instrucciones se aplican a toda **aplicación** que acompañe a un cuaderno de la colección o se publique como producto independiente. Una aplicación es software que recibe entradas de la persona usuaria, ejecuta cálculos o procesos con ellas y devuelve resultados. Incluye las aplicaciones web (Shiny, Streamlit, Dash, Panel, Flask, FastAPI), las que se ejecutan en el navegador (por ejemplo, con Pyodide) y las API.

Se distinguen tres objetos relacionados:

- **Cuaderno**: documenta un análisis y es la fuente del método. Se rige por la [guía](01-cuadernos-de-conocimiento.md).
- **Tablero**: muestra resultados ya calculados, sin entradas ni cálculos propios. Se rige por los [requisitos para tableros](06-estandar-tableros.md).
- **Aplicación**: calcula a partir de entradas de la persona usuaria. Se rige por este documento. El modelo que ejecuta cumple además los [requisitos para modelos](08-estandar-modelos.md).

Complementan la guía, los [requisitos para datos](03-estandar-de-datos.md) y los [requisitos para el uso de IA](05-uso-de-ia.md): los datos de la aplicación cumplen los requisitos para datos y el uso de IA, tanto en su preparación como en su ejecución, se declara según los requisitos para el uso de IA. La seguridad común a todo repositorio (secretos, datos personales y rutas locales, código no confiable, dependencias y *releases*) la cubren los [requisitos de seguridad](10-requisitos-seguridad.md); los requisitos de seguridad de este documento se aplican además.

### 1.2 Convenciones

1. **Identificador.** Cada requisito tiene un código de tres letras y dos cifras (por ejemplo, ALC-01). Los códigos se usan en la lista de verificación, en el prompt de validación y en los reportes.
2. **Nivel.** *Obligatorio* significa que el cuaderno, el tablero o la aplicación no se acepta si el requisito aplica y no se cumple. *Recomendado* significa que el cumplimiento mejora la calidad pero no condiciona la aceptación. *Crítico* es un requisito obligatorio cuyo incumplimiento bloquea la publicación, cualquiera sea la puntuación total.
3. **Base.** Entre paréntesis, cada requisito indica el documento, el año y, cuando corresponde, el criterio o el apartado del que procede. Los requisitos cuya base es «Requisito de esta guía» los establece este documento y no provienen de una fuente externa.
4. **Redacción.** Cada requisito se enuncia en el estado conforme: describe cómo es un objeto que lo cumple. Los requisitos que dicen «aplica solo si» se marcan «No aplica» cuando no corresponden.
5. **Citas y traducciones.** Las citas siguen la norma APA 7. Los textos de las fuentes en inglés se traducen al español; las traducciones son propias. Los nombres de campos, códigos y apartados de las fuentes se conservan en su idioma original.
6. **Fecha de consulta.** Las fuentes web sin fecha de publicación se consultaron el 16 de noviembre de 2026 (véanse las Referencias). Los estándares y las guías cambian: antes de publicar, confirme la versión vigente.

### 1.3 Política de costo cero

Ningún requisito de este documento exige comprar suscripciones, licencias ni servicios (COD-05). Las herramientas que se nombran (Git, Docker, Binder, Dependabot, Lighthouse, WAVE, OpenSSF Scorecard) son gratuitas. Si la aplicación usa un servicio de pago, el repositorio debe documentar una alternativa abierta (COD-04).

### 1.4 Documentos de referencia

**Tabla 1.** Documentos de los que se derivan los requisitos.

```{list-table}
:header-rows: 1

* - Documento
  - Qué establece
  - Requisitos que se derivan
* - Digital Public Goods Alliance (s. f.). DPG Standard
  - Nueve indicadores para que el software de interés público sea abierto, documentado, independiente de plataformas cerradas, respetuoso de la privacidad y no haga daño
  - ALC, COD, DAT-02, DOC
* - Chue Hong et al. (2022). Principios FAIR4RS
  - Principios para que el software de investigación sea localizable, accesible, interoperable y reutilizable
  - COD-07, REP-07, REP-08
* - Wiggins (2017). The twelve-factor app
  - Doce prácticas para aplicaciones desplegables y portables
  - REP-01 a REP-04, REP-09
* - Binder Project (s. f.); Quarto (s. f.)
  - Reconstrucción reproducible de entornos y ejecución sin servidor
  - REP
* - OWASP Foundation (2025). OWASP Top 10:2025
  - Diez categorías de riesgo de seguridad de aplicaciones web
  - DAT-05, DAT-07, SEG
* - GitHub (s. f.); OpenSSF (s. f.)
  - Alertas de dependencias y evaluación de la seguridad de proyectos de código abierto
  - SEG-05, SEG-12
* - World Wide Web Consortium (2024); MinTIC (2020); Government Analysis Function (2026)
  - Accesibilidad web (WCAG 2.2; WCAG 2.1 AA en las entidades públicas) y pruebas
  - ACC, DOC-05
* - Congreso de la República (2012). Ley 1581 de 2012
  - Régimen general de protección de datos personales
  - SEG-02, SEG-03
* - Preston-Werner (s. f.); Citation File Format (s. f.); Software Heritage (s. f.)
  - Versionado semántico, citación del software y archivo del código fuente
  - COD-07, REP-07, REP-11, DOC-04
* - [Requisitos para datos](03-estandar-de-datos.md) y [requisitos para el uso de IA](05-uso-de-ia.md) de esta colección
  - Requisitos para datos, licencias, costo cero y declaración de IA que la aplicación hereda
  - COD-05, DAT-01, DOC-08, DOC-09
```

## 2. Requisitos

### 2.1 Propósito, alcance y no hacer daño

Una aplicación recibe entradas, calcula y devuelve un resultado que alguien puede usar para decidir. Un cuaderno documenta un análisis; un tablero muestra resultados ya calculados y se rige por los [requisitos para tableros](06-estandar-tableros.md). Si una aplicación expone una API o permite subir archivos, la sección de seguridad se aplica con todo rigor.

El Digital Public Goods Standard exige **no hacer daño por diseño**: el proyecto debe mostrar que anticipó y previno los daños posibles (Digital Public Goods Alliance, s. f., indicador 9). En gestión del riesgo, el daño más probable es el uso indebido del resultado, como tomar una calculadora de amenaza por un estudio de microzonificación. El análisis de ALC-02 nombra esos usos y dice qué hace la aplicación para impedirlos o advertirlos.

```markdown
# Análisis de no hacer daño (`DO_NO_HARM.md`)

| Uso indebido o daño posible | Quién lo sufriría | Medida adoptada | Responsable |
|---|---|---|---|
| <por ejemplo, usar el resultado como estudio de riesgo oficial> | <comunidades, autoridades> | <aviso visible, límites de validez> | <persona> |
| <por ejemplo, subir datos personales> | <personas del territorio> | <no se almacenan; aviso de privacidad> | <persona> |
```

*Requisitos de este grupo: ALC-01, ALC-02, ALC-03, ALC-04, ALC-05. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.2 Código abierto, licencias y titularidad

Publicar el código no basta. El DPG Standard pide una licencia aprobada por la OSI, la titularidad de los derechos documentada y independencia de dependencias cerradas, o una alternativa abierta identificada (Digital Public Goods Alliance, s. f., indicadores 2 a 4). La política de costo cero de los [requisitos para datos](03-estandar-de-datos.md) añade que nadie paga para usar o ejecutar la aplicación (COD-05).

Los principios FAIR4RS piden que el software tenga un identificador persistente, metadatos ricos, una licencia clara y referencias a lo que usa (Chue Hong et al., 2022). Aquí son requisitos verificables: DOI por versión (REP-07), metadatos (REP-08) y licencia (COD-01).

Use versionado semántico: quien cita una versión sabe si un cambio puede alterar los resultados (Preston-Werner, s. f.). Un cambio de método sube la versión mayor o menor, nunca solo el parche.

*Requisitos de este grupo: COD-01, COD-02, COD-03, COD-04, COD-05, COD-06, COD-07, COD-08. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.3 Reproducibilidad y despliegue

Una aplicación es reproducible si otra persona la pone en marcha y obtiene los mismos resultados con las mismas entradas.

- **Entorno declarado y fijado.** Binder recomienda fijar versiones exactas (Binder Project, s. f.). Los doce factores añaden que las dependencias se declaran y se aíslan del sistema (factor II), la configuración vive en el entorno y no en el código (factor III) y la construcción, la publicación y la ejecución están separadas (factor V) (Wiggins, 2017).
- **Pruebas con casos de referencia.** Con entradas fijas, la aplicación reproduce los valores del cuaderno. Esas pruebas se ejecutan en cada cambio y muestran si una actualización alteró los resultados (REP-05).
- **Ejecución sin el servidor de quien la escribió.** La instancia alojada puede desaparecer. La aplicación se ejecuta en local (REP-06) y, cuando es posible, en el navegador; Quarto documenta una opción con Pyodide (Quarto, s. f.).

Estructura mínima del repositorio:

```text
app-<tema>/
├── README.md              # instalar, ejecutar, probar, citar
├── LICENSE                # MIT o Apache-2.0
├── CITATION.cff           # con ORCID de cada persona autora
├── CHANGELOG.md           # cambios por versión
├── DO_NO_HARM.md          # análisis de no hacer daño (Sección 2.1)
├── SECURITY.md            # cómo reportar vulnerabilidades
├── ACCESSIBILITY.md       # declaración de accesibilidad
├── AI_USE.md              # registro de uso de IA
├── environment.yml        # versiones fijadas (o archivo de bloqueo)
├── Dockerfile             # entorno como código
├── .env.example           # variables de entorno, sin valores reales
├── src/                   # código de la aplicación
├── tests/                 # casos de referencia del cuaderno
├── examples/              # entradas y resultados esperados
├── docs/                  # guía de uso y de métodos
└── .github/workflows/     # pruebas, alertas y despliegue
```

*Requisitos de este grupo: REP-01, REP-02, REP-03, REP-04, REP-05, REP-06, REP-07, REP-08, REP-09, REP-10, REP-11. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.4 Entradas, salidas y datos

Las entradas siguen los requisitos para datos. Los resultados se exportan en un formato no propietario y con un registro de cómo se produjeron (Digital Public Goods Alliance, s. f., indicador 6). Los metadatos bastan para repetir el resultado (DAT-03 y DAT-04):

```json
{
  "aplicacion": "<nombre>",
  "version": "1.2.0",
  "doi_aplicacion": "https://doi.org/<DOI>",
  "fecha_ejecucion": "<AAAA-MM-DDThh:mm:ssZ>",
  "parametros": {"periodo_retorno": 100, "crs": "EPSG:9377"},
  "entradas": [
    {"archivo": "entrada.geojson", "sha256": "<suma de verificación>", "doi": "<DOI de la fuente>"}
  ],
  "licencia_resultado": "CC-BY-4.0",
  "aviso": "Resultado indicativo; no sustituye estudios ni productos oficiales."
}
```

Valide las entradas: es un requisito de usabilidad (mensajes claros) y de seguridad, porque OWASP Top 10:2025 incluye la inyección y los fallos de integridad de software y de datos (OWASP Foundation, 2025, A05 y A08).

*Requisitos de este grupo: DAT-01, DAT-02, DAT-03, DAT-04, DAT-05, DAT-06, DAT-07, DAT-08. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.5 Seguridad y privacidad

OWASP Top 10:2025 es el punto de partida para decidir qué revisar; no es una norma de cumplimiento. Sus categorías son A01 control de acceso roto, A02 configuración incorrecta, A03 fallos en la cadena de suministro, A04 fallos criptográficos, A05 inyección, A06 diseño inseguro, A07 fallos de autenticación, A08 fallos de integridad de software o de datos, A09 fallos de registro y alertas y A10 mal manejo de condiciones excepcionales (OWASP Foundation, 2025).

Una aplicación científica pequeña se expone sobre todo por cinco puntos: secretos en el repositorio (A02), dependencias vulnerables (A03), entradas que se evalúan o se deserializan (A05, A08), errores que revelan rutas o datos (A02, A10) y datos personales en los registros (A09). Los requisitos de esta sección los cubren. Documente la revisión así (`SECURITY_REVIEW.md`):

```markdown
| Categoría OWASP 2025 | ¿Aplica? | Qué se revisó | Medida o razón de no aplicar |
|---|---|---|---|
| A01 Control de acceso roto | <sí/no> | <rutas, archivos accesibles> | <medida> |
| A03 Fallos en la cadena de suministro | sí | <dependencias fijadas, alertas> | <Dependabot, versiones fijas> |
| A05 Inyección | <sí/no> | <entradas, archivos subidos> | <validación, sin `eval`> |
```

**Datos personales.** La Ley 1581 de 2012 establece el régimen general de protección de datos personales (Congreso de la República, 2012). Si es posible, la aplicación no los recoge y lo declara. Si los recoge, aplican la finalidad, la autorización y el aviso de privacidad, y decide una persona con competencia jurídica.

**Entidades públicas.** La Resolución 1519 de 2020 exige condiciones mínimas de seguridad digital en las sedes electrónicas (MinTIC, 2020, art. 6). Una aplicación alojada en una sede electrónica las cumple.

*Requisitos de este grupo: SEG-01, SEG-02, SEG-03, SEG-04, SEG-05, SEG-06, SEG-07, SEG-08, SEG-09, SEG-10, SEG-11, SEG-12. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.6 Accesibilidad y usabilidad

Una aplicación tiene formularios y pasos, así que exige más que un tablero. WCAG 2.2 añade el tamaño mínimo del objetivo (2.5.8), no repetir información (3.3.7) y la autenticación accesible (3.3.8). Los formularios etiquetan sus campos, identifican los errores y sugieren cómo corregirlos (3.3.1 a 3.3.3), y los controles exponen nombre, función y valor (4.1.2) (W3C, 2024).

La Resolución 1519 de 2020 exige WCAG 2.1 AA a las entidades públicas (MinTIC, 2020, art. 3 y anexo 1); WCAG 2.2 lo incluye. La guía de pruebas del *Analysis Function* también sirve aquí: pruebas automáticas, teclado, zoom, lector de pantalla y personas usuarias (Analysis Function, 2026). Las pruebas automáticas no bastan.

**Costo cero.** Use un lector de pantalla gratuito: NVDA, VoiceOver u Orca.

*Requisitos de este grupo: ACC-01, ACC-02, ACC-03, ACC-04, ACC-05, ACC-06, ACC-07, ACC-08, ACC-09. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.7 Documentación, mantenimiento y uso de IA

El `README` permite a una persona técnica que no conoce el proyecto ejecutarlo o entenderlo (Digital Public Goods Alliance, s. f., indicador 5). La documentación también explica el método y las limitaciones: una aplicación que calcula riesgo sin explicar cómo no puede evaluarse ni reutilizarse.

**Mantenimiento.** Una aplicación abandonada acumula dependencias vulnerables y resultados desactualizados. La política de mantenimiento (DOC-05) dice quién responde, qué versiones tienen soporte y cuándo se retira. Al retirarla, se archivan el código, los datos y los metadatos (Analysis Function, 2026).

**Uso de IA.** Declárelo según los [requisitos para el uso de IA](05-uso-de-ia.md). Si la aplicación llama a un modelo al ejecutarse, fije el modelo y la versión, guarde las salidas y no envíe datos personales a una IA pública (Requisitos para el uso de IA, U11, U12 y U20). Si el modelo deja de estar disponible, la aplicación sigue funcionando o falla con claridad (DOC-09).

*Requisitos de este grupo: DOC-01, DOC-02, DOC-03, DOC-04, DOC-05, DOC-06, DOC-07, DOC-08, DOC-09. Su enunciado completo está en la lista de verificación de la Sección 3.*

## 3. Lista de verificación

La lista tiene 62 requisitos: 53 obligatorios y 9 recomendados. Los 11 requisitos **críticos** (ALC-02, COD-01, COD-05, REP-01, REP-07, DAT-01, SEG-01, SEG-02, SEG-03, ACC-02 y DOC-01) bloquean la publicación si no se cumplen.

**Criterio de aceptación.** Un objeto cumple los requisitos si (1) ningún requisito crítico está en incumplimiento y (2) el puntaje de requisitos obligatorios es de 90 o más, calculado como se indica en el prompt de la Sección 4.

**2.1. Propósito, alcance y no hacer daño**

- [ ] **ALC-01.** El repositorio documenta el propósito de la aplicación, a quién se dirige y qué decisiones o procesos apoya. (Digital Public Goods Alliance, s. f., indicador 5)
- [ ] **ALC-02.** **Crítico.** Existe un análisis de «no hacer daño» que identifica los usos indebidos y los daños posibles de los resultados (por ejemplo, tomar un resultado indicativo como una evaluación de riesgo oficial) y las medidas adoptadas. (Digital Public Goods Alliance, s. f., indicador 9)
- [ ] **ALC-03.** Cada resultado se acompaña de un aviso visible de que es indicativo, de sus supuestos y de que no sustituye los estudios ni los productos oficiales de la entidad competente. (Requisito de esta guía)
- [ ] **ALC-04.** El método que implementa la aplicación está descrito y validado en un cuaderno de la colección; la aplicación no incorpora cálculos sin documentar. (Requisito de esta guía)
- [ ] **ALC-05.** *(Recomendado)* La documentación explica por qué se necesita una aplicación y no basta un cuaderno o un tablero. (Requisito de esta guía)

**2.2. Código abierto, licencias y titularidad**

- [ ] **COD-01.** **Crítico.** El código fuente completo está en un repositorio público con una licencia aprobada por la OSI (MIT o Apache-2.0) y un archivo `LICENSE`. (Digital Public Goods Alliance, s. f., indicador 2; Requisitos para datos, LIC-04)
- [ ] **COD-02.** Están documentadas la titularidad de los derechos de autor y las contribuciones de terceros. (Digital Public Goods Alliance, s. f., indicador 3)
- [ ] **COD-03.** Todas las dependencias tienen una licencia compatible con la del código y existe un inventario de licencias. (Digital Public Goods Alliance, s. f., indicador 4)
- [ ] **COD-04.** La aplicación funciona sin servicios propietarios; si usa uno (por ejemplo, un servicio en la nube de pago), el repositorio documenta la alternativa abierta y lo que se pierde al usarla. (Digital Public Goods Alliance, s. f., indicador 4)
- [ ] **COD-05.** **Crítico.** El uso de la aplicación y su ejecución local no exigen pagos, suscripciones ni licencias. (Requisitos para datos, 1.3)
- [ ] **COD-06.** Los datos y los contenidos que acompañan al código declaran su licencia por separado (CC BY 4.0 o equivalente). (Digital Public Goods Alliance, s. f., indicador 2; Requisitos para datos, LIC-04)
- [ ] **COD-07.** Las versiones siguen el versionado semántico y cada versión publicada es un *release*. (Preston-Werner, s. f.; Chue Hong et al., 2022)
- [ ] **COD-08.** *(Recomendado)* El repositorio incluye `CONTRIBUTING.md`, un código de conducta y plantillas de *issues*. (Digital Public Goods Alliance, s. f., indicador 9c)

**2.3. Reproducibilidad y despliegue**

- [ ] **REP-01.** **Crítico.** La aplicación se instala y se ejecuta desde un clon limpio con órdenes documentadas, y esa ejecución se prueba en integración continua, en un contenedor o en Binder. (Binder Project, s. f.; Wiggins, 2017, factores I y V)
- [ ] **REP-02.** Las dependencias están fijadas por versión, con un archivo de bloqueo o `environment.yml`. (Binder Project, s. f.; Wiggins, 2017, factor II)
- [ ] **REP-03.** El entorno se define como código (Dockerfile, `environment.yml` o equivalente) y no depende de pasos manuales. (Binder Project, s. f.)
- [ ] **REP-04.** La configuración y los secretos se leen de variables de entorno; el repositorio incluye un `.env.example` sin valores reales. (Wiggins, 2017, factor III; OWASP Foundation, 2025, A02)
- [ ] **REP-05.** Hay pruebas automáticas con casos de referencia: con entradas fijas, la aplicación reproduce los valores esperados del cuaderno. (Requisito de esta guía)
- [ ] **REP-06.** La aplicación se puede ejecutar en local con herramientas abiertas; la instancia alojada no es la única forma de usarla. (Digital Public Goods Alliance, s. f., indicador 4)
- [ ] **REP-07.** **Crítico.** Cada versión publicada tiene un DOI en Zenodo y un `CITATION.cff` con el ORCID de cada persona autora. (Citation File Format, s. f.; Chue Hong et al., 2022; Requisitos para datos, DEP-06)
- [ ] **REP-08.** El repositorio tiene un archivo de metadatos del software (`CITATION.cff` o `codemeta.json`) con descripción, versión, licencia y dependencias. (Chue Hong et al., 2022)
- [ ] **REP-09.** Los procesos de la aplicación no guardan estado propio en memoria o disco local; el estado que se conserva está en un servicio declarado. (Wiggins, 2017, factor VI)
- [ ] **REP-10.** *(Recomendado)* Si es posible, la aplicación se compila para ejecutarse en el navegador (por ejemplo, con Pyodide o Shinylive) y así prescindir de un servidor. (Quarto, s. f.)
- [ ] **REP-11.** *(Recomendado)* El código se archiva también en Software Heritage. (Software Heritage, s. f.)

**2.4. Entradas, salidas y datos**

- [ ] **DAT-01.** **Crítico.** Los datos y modelos que la aplicación incluye o descarga cumplen los [requisitos para datos](03-estandar-de-datos.md): licencia, metadatos y ausencia de datos personales. (Requisitos para datos, INV, LIC y PER)
- [ ] **DAT-02.** Los resultados se exportan en un formato no propietario (CSV, GeoJSON, GeoTIFF) junto con un archivo de metadatos. (Digital Public Goods Alliance, s. f., indicador 6)
- [ ] **DAT-03.** El archivo de metadatos de cada resultado registra la versión de la aplicación, los parámetros, un resumen de las entradas (suma de verificación) y la fecha. (Requisito de esta guía)
- [ ] **DAT-04.** Un resultado puede repetirse: un archivo de parámetros o una URL contiene todas las entradas necesarias. (Requisito de esta guía)
- [ ] **DAT-05.** La aplicación valida las entradas (tipo, rango, unidades, sistema de referencia, tamaño de archivo) y devuelve mensajes de error claros. (OWASP Foundation, 2025, A05; W3C, 2024, criterio 3.3.1)
- [ ] **DAT-06.** Los datos de referencia y los modelos que usa están citados con su versión y su DOI. (Requisitos para datos, INV-01 y DEP-07)
- [ ] **DAT-07.** Si consulta APIs externas, maneja las fallas, los límites de uso y el almacenamiento temporal, y no deja claves en el navegador. (OWASP Foundation, 2025, A02 y A10)
- [ ] **DAT-08.** *(Recomendado)* La aplicación incluye un conjunto de ejemplo con entradas y resultados esperados. (Requisito de esta guía)

**2.5. Seguridad y privacidad**

- [ ] **SEG-01.** **Crítico.** Ningún secreto (clave, token, contraseña) está en el repositorio ni en su historial. (OWASP Foundation, 2025, A02)
- [ ] **SEG-02.** **Crítico.** Si la aplicación recoge o procesa datos personales, cumple la Ley 1581 de 2012 (finalidad, autorización y aviso de privacidad); si no los recoge, lo declara. (Congreso de la República, 2012; Digital Public Goods Alliance, s. f., indicador 7)
- [ ] **SEG-03.** **Crítico.** Los archivos o datos que sube una persona usuaria no se guardan ni se envían a terceros sin que la persona lo sepa y lo autorice; por defecto se eliminan al terminar la sesión. (Congreso de la República, 2012; Digital Public Goods Alliance, s. f., indicador 9)
- [ ] **SEG-04.** La aplicación se revisó contra la lista OWASP Top 10:2025 y el repositorio conserva el resultado y las medidas. (OWASP Foundation, 2025)
- [ ] **SEG-05.** Las dependencias tienen alertas automáticas de vulnerabilidades y una política de actualización. (GitHub, s. f.; OWASP Foundation, 2025, A03)
- [ ] **SEG-06.** La aplicación no evalúa ni ejecuta código ni deserializa datos que provengan de la persona usuaria, y limita el tipo y el tamaño de los archivos que acepta. (OWASP Foundation, 2025, A05 y A08)
- [ ] **SEG-07.** Se sirve solo por HTTPS y sin contenido mixto. (OWASP Foundation, 2025, A04)
- [ ] **SEG-08.** Los errores no muestran trazas, rutas ni datos internos a la persona usuaria. (OWASP Foundation, 2025, A02 y A10)
- [ ] **SEG-09.** Los registros (*logs*) no contienen datos personales y se conservan por un tiempo limitado. (OWASP Foundation, 2025, A09)
- [ ] **SEG-10.** Si hay autenticación, usa un proveedor estándar y no almacena contraseñas propias (aplica solo si hay autenticación). (OWASP Foundation, 2025, A01 y A07)
- [ ] **SEG-11.** *(Recomendado)* Hay límites de uso por solicitud o por persona para evitar el abuso de los recursos. (Requisito de esta guía)
- [ ] **SEG-12.** *(Recomendado)* El repositorio publica un `SECURITY.md` con el canal para reportar vulnerabilidades y se ejecuta OpenSSF Scorecard. (OpenSSF, s. f.)

**2.6. Accesibilidad y usabilidad**

- [ ] **ACC-01.** La aplicación se probó contra WCAG 2.2 niveles A y AA, que incluye los criterios de WCAG 2.1 nivel AA que la Resolución 1519 de 2020 exige a las entidades públicas. (W3C, 2024; MinTIC, 2020, art. 3 y anexo 1)
- [ ] **ACC-02.** **Crítico.** Todas las funciones se operan con teclado, con foco visible y orden lógico. (W3C, 2024, criterios 2.1.1 y 2.4.7; MinTIC, 2020, anexo 1)
- [ ] **ACC-03.** Los formularios tienen etiquetas e instrucciones, identifican los errores y sugieren cómo corregirlos, y exponen nombre, función y valor a las tecnologías de apoyo. (W3C, 2024, criterios 3.3.1, 3.3.2, 3.3.3 y 4.1.2)
- [ ] **ACC-04.** Los resultados en mapas o gráficos tienen una alternativa en texto o tabla, y el color no es el único medio de transmitir información. (W3C, 2024, criterios 1.1.1 y 1.4.1)
- [ ] **ACC-05.** El contenido se amplía al 200 % sin pérdida y se puede usar en un teléfono. (W3C, 2024, criterios 1.4.4 y 1.4.10)
- [ ] **ACC-06.** Se hicieron pruebas automáticas y una revisión manual con teclado y un lector de pantalla gratuito (NVDA, VoiceOver u Orca), y se publicó una declaración de accesibilidad. (Analysis Function, 2026)
- [ ] **ACC-07.** Los pasos que exigen repetir información o autenticarse tienen alternativas accesibles (aplica solo si hay autenticación o procesos de varios pasos). (W3C, 2024, criterios 3.3.7 y 3.3.8)
- [ ] **ACC-08.** *(Recomendado)* La interfaz está en español y su texto está separado del código para poder traducirlo. (Requisito de esta guía)
- [ ] **ACC-09.** *(Recomendado)* La aplicación es usable con conectividad limitada: la carga inicial es liviana y los procesos largos informan su avance. (Requisito de esta guía)

**2.7. Documentación, mantenimiento y uso de IA**

- [ ] **DOC-01.** **Crítico.** El `README` permite a una persona técnica que no conoce el proyecto instalarlo, ejecutarlo, configurarlo, probarlo y citarlo. (Digital Public Goods Alliance, s. f., indicador 5)
- [ ] **DOC-02.** Existe una guía de uso con ejemplos de entradas y de resultados esperados. (Digital Public Goods Alliance, s. f., indicador 5)
- [ ] **DOC-03.** La documentación explica los métodos, las ecuaciones, los supuestos, la validación y las limitaciones, con referencias. (Requisito de esta guía)
- [ ] **DOC-04.** Un `CHANGELOG.md` registra los cambios de cada versión. (Preston-Werner, s. f.)
- [ ] **DOC-05.** Existe una política de mantenimiento: responsable, versiones con soporte, tiempos de respuesta y criterio de retiro, con archivo del código y de los datos al retirarla. (Analysis Function, 2026)
- [ ] **DOC-06.** Hay un canal para reportar errores y recibir contribuciones (*issues* o correo). (Requisito de esta guía)
- [ ] **DOC-07.** Se declaran los estándares y las buenas prácticas que sigue (por ejemplo, formatos OGC, GeoJSON o una especificación OpenAPI si ofrece una API). (Digital Public Goods Alliance, s. f., indicador 8)
- [ ] **DOC-08.** El uso de IA en la preparación del código, los textos o los datos se declara según los [requisitos para el uso de IA](05-uso-de-ia.md). (Requisitos para el uso de IA, U04)
- [ ] **DOC-09.** Si la aplicación llama a un modelo de IA al ejecutarse, el modelo y la versión están fijados y documentados, la aplicación avisa a la persona usuaria, no le envía datos personales, ofrece un modo sin IA o una salida guardada y etiqueta las salidas generadas (aplica solo si la aplicación llama a un modelo de IA). (Requisitos para el uso de IA, U11, U12 y U20)

## 4. Prompt para validar los requisitos para aplicaciones

Este prompt convierte la lista de verificación en una auditoría repetible. Lee el repositorio de una aplicación, instala y prueba el código en una copia limpia, ejecuta comprobaciones automáticas y genera un **reporte de cumplimiento** en Markdown y JSON. Funciona con cualquier asistente de IA que pueda leer archivos y ejecutar comandos.

**Procedimiento de uso**

1. Copie el prompt completo y reemplace los valores entre `<>` de la sección ENTRADAS.
2. Ejecútelo desde un entorno con acceso a los archivos del repositorio. Para comprobar DOI, paquetes, la URL publicada o la ejecución, use el modo ampliado que indica la sección ENTRADAS.
3. Revise el reporte con una persona. Un asistente de IA puede equivocarse al leer un archivo o interpretar un criterio. El resultado es un apoyo a la revisión y no una certificación, y todo lo marcado «Requiere revisión humana» lo decide una persona.
4. Guarde el reporte en el repositorio y repita la auditoría antes de cada *release*.

:::{warning} Lo que este prompt no puede hacer
No es una auditoría de seguridad ni una prueba de penetración: busca patrones de riesgo y fallas de configuración, y no puede garantizar que la aplicación sea segura. Tampoco decide cuestiones de datos personales, de derechos de terceros ni de uso indebido de los resultados; esos puntos se marcan «Requiere revisión humana». Para ejecutar el código del repositorio, hágalo en un entorno aislado.

Si el auditor es un servicio externo, aplíquele las mismas reglas que a cualquier IA: no le entregue datos personales, datos de comunidades ni material con restricciones de licencia (véanse los [requisitos para el uso de IA](05-uso-de-ia.md)). Si cambia la lista de verificación, actualice también los criterios del prompt.
:::

````text
Actúa como auditor de aplicaciones abiertas y reproducibles en la Subdirección para el Conocimiento del Riesgo (UNGRD). Tu tarea es VERIFICAR si una aplicación y su repositorio cumplen la lista de verificación de los «Requisitos para aplicaciones» y producir un REPORTE DE CUMPLIMIENTO. Eres un revisor: NO modifiques ningún archivo.

## ENTRADAS
- RUTA_REPO: <ruta local del repositorio de la aplicación>
- URL_APP (opcional): <URL de la instancia alojada>
- CUADERNO (opcional): <ruta o enlace del cuaderno que contiene el método>
- MODO: "estatico" (solo leer archivos, historial y ejecutar pruebas locales) o "con_red" (además puedes comprobar DOI, paquetes y la URL alojada). Si no lo indico, usa "estatico".
- SALIDA: carpeta donde escribir `reporte_aplicacion.md` y `reporte_aplicacion.json`; si no la indico, imprime el reporte.

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
1. Inventario de archivos: `README.md`, `LICENSE`, `CITATION.cff`, `CHANGELOG.md`, `DO_NO_HARM.md`, `SECURITY.md`, `ACCESSIBILITY.md`, `AI_USE.md`, `environment.yml` o archivo de bloqueo, `Dockerfile`, `.env.example`, `tests/` y `.github/workflows/`.
2. Instalación y pruebas: en una copia limpia, sigue las órdenes del `README` y ejecuta las pruebas. Reporta el resultado. Si el `README` no permite instalarla, REP-01 y DOC-01 son «No cumple».
3. Dependencias: comprueba que las versiones están fijadas y reúne las licencias; en modo "con_red", ejecuta el auditor de vulnerabilidades del ecosistema (por ejemplo, `pip-audit` o `npm audit`) y comprueba que cada paquete existe.
4. Secretos: busca claves, tokens y contraseñas en los archivos y en el historial (`git log -p`); reporta solo archivo y línea, nunca el valor.
5. Código riesgoso: busca `eval`, `exec`, `pickle.load`, `yaml.load` sin cargador seguro, `subprocess` con `shell=True`, SQL armado con texto y archivos subidos sin límite de tipo o tamaño.
6. Configuración: comprueba que la configuración se lee de variables de entorno, que `.env.example` no tiene valores reales y que los errores no devuelven trazas.
7. Datos y resultados: comprueba que los resultados se exportan en formatos abiertos con metadatos (versión, parámetros, entradas) y que existe un conjunto de ejemplo.
8. Privacidad: busca recolección de datos personales, analítica, cookies, registros con datos personales y envío de archivos de la persona usuaria a terceros.
9. IA: busca llamadas a modelos de IA en ejecución (`openai`, `anthropic`, `transformers`, `langchain`) y revisa si el modelo y la versión están fijados y si hay una alternativa sin IA.
10. Accesibilidad: en la interfaz revisa etiquetas, mensajes de error, `lang` y orden del foco; en modo "con_red" y con URL_APP, ejecuta Lighthouse y WAVE. Los resultados automáticos no sustituyen la prueba con teclado ni con lector de pantalla: márcalos «Requiere prueba manual».

### Paso C. Evaluación de criterios
Evalúa los 62 criterios. Para cada uno asigna exactamente un estado: Cumple, Parcial, No cumple, No aplica o No verificable. Los marcados (CRÍTICO) son compuertas bloqueantes y los marcados (RECOMENDADO) no condicionan la aceptación.

### Propósito, alcance y no hacer daño
ALC-01. El repositorio documenta el propósito de la aplicación, a quién se dirige y qué decisiones o procesos apoya. (Digital Public Goods Alliance, s. f., indicador 5)
ALC-02 (CRÍTICO). Existe un análisis de «no hacer daño» que identifica los usos indebidos y los daños posibles de los resultados (por ejemplo, tomar un resultado indicativo como una evaluación de riesgo oficial) y las medidas adoptadas. (Digital Public Goods Alliance, s. f., indicador 9)
ALC-03. Cada resultado se acompaña de un aviso visible de que es indicativo, de sus supuestos y de que no sustituye los estudios ni los productos oficiales de la entidad competente. (Requisito de esta guía)
ALC-04. El método que implementa la aplicación está descrito y validado en un cuaderno de la colección; la aplicación no incorpora cálculos sin documentar. (Requisito de esta guía)
ALC-05 (RECOMENDADO). La documentación explica por qué se necesita una aplicación y no basta un cuaderno o un tablero. (Requisito de esta guía)

### Código abierto, licencias y titularidad
COD-01 (CRÍTICO). El código fuente completo está en un repositorio público con una licencia aprobada por la OSI (MIT o Apache-2.0) y un archivo `LICENSE`. (Digital Public Goods Alliance, s. f., indicador 2; Requisitos para datos, LIC-04)
COD-02. Están documentadas la titularidad de los derechos de autor y las contribuciones de terceros. (Digital Public Goods Alliance, s. f., indicador 3)
COD-03. Todas las dependencias tienen una licencia compatible con la del código y existe un inventario de licencias. (Digital Public Goods Alliance, s. f., indicador 4)
COD-04. La aplicación funciona sin servicios propietarios; si usa uno (por ejemplo, un servicio en la nube de pago), el repositorio documenta la alternativa abierta y lo que se pierde al usarla. (Digital Public Goods Alliance, s. f., indicador 4)
COD-05 (CRÍTICO). El uso de la aplicación y su ejecución local no exigen pagos, suscripciones ni licencias. (Requisitos para datos, 1.3)
COD-06. Los datos y los contenidos que acompañan al código declaran su licencia por separado (CC BY 4.0 o equivalente). (Digital Public Goods Alliance, s. f., indicador 2; Requisitos para datos, LIC-04)
COD-07. Las versiones siguen el versionado semántico y cada versión publicada es un *release*. (Preston-Werner, s. f.; Chue Hong et al., 2022)
COD-08 (RECOMENDADO). El repositorio incluye `CONTRIBUTING.md`, un código de conducta y plantillas de *issues*. (Digital Public Goods Alliance, s. f., indicador 9c)

### Reproducibilidad y despliegue
REP-01 (CRÍTICO). La aplicación se instala y se ejecuta desde un clon limpio con órdenes documentadas, y esa ejecución se prueba en integración continua, en un contenedor o en Binder. (Binder Project, s. f.; Wiggins, 2017, factores I y V)
REP-02. Las dependencias están fijadas por versión, con un archivo de bloqueo o `environment.yml`. (Binder Project, s. f.; Wiggins, 2017, factor II)
REP-03. El entorno se define como código (Dockerfile, `environment.yml` o equivalente) y no depende de pasos manuales. (Binder Project, s. f.)
REP-04. La configuración y los secretos se leen de variables de entorno; el repositorio incluye un `.env.example` sin valores reales. (Wiggins, 2017, factor III; OWASP Foundation, 2025, A02)
REP-05. Hay pruebas automáticas con casos de referencia: con entradas fijas, la aplicación reproduce los valores esperados del cuaderno. (Requisito de esta guía)
REP-06. La aplicación se puede ejecutar en local con herramientas abiertas; la instancia alojada no es la única forma de usarla. (Digital Public Goods Alliance, s. f., indicador 4)
REP-07 (CRÍTICO). Cada versión publicada tiene un DOI en Zenodo y un `CITATION.cff` con el ORCID de cada persona autora. (Citation File Format, s. f.; Chue Hong et al., 2022; Requisitos para datos, DEP-06)
REP-08. El repositorio tiene un archivo de metadatos del software (`CITATION.cff` o `codemeta.json`) con descripción, versión, licencia y dependencias. (Chue Hong et al., 2022)
REP-09. Los procesos de la aplicación no guardan estado propio en memoria o disco local; el estado que se conserva está en un servicio declarado. (Wiggins, 2017, factor VI)
REP-10 (RECOMENDADO). Si es posible, la aplicación se compila para ejecutarse en el navegador (por ejemplo, con Pyodide o Shinylive) y así prescindir de un servidor. (Quarto, s. f.)
REP-11 (RECOMENDADO). El código se archiva también en Software Heritage. (Software Heritage, s. f.)

### Entradas, salidas y datos
DAT-01 (CRÍTICO). Los datos y modelos que la aplicación incluye o descarga cumplen los [requisitos para datos](03-estandar-de-datos.md): licencia, metadatos y ausencia de datos personales. (Requisitos para datos, INV, LIC y PER)
DAT-02. Los resultados se exportan en un formato no propietario (CSV, GeoJSON, GeoTIFF) junto con un archivo de metadatos. (Digital Public Goods Alliance, s. f., indicador 6)
DAT-03. El archivo de metadatos de cada resultado registra la versión de la aplicación, los parámetros, un resumen de las entradas (suma de verificación) y la fecha. (Requisito de esta guía)
DAT-04. Un resultado puede repetirse: un archivo de parámetros o una URL contiene todas las entradas necesarias. (Requisito de esta guía)
DAT-05. La aplicación valida las entradas (tipo, rango, unidades, sistema de referencia, tamaño de archivo) y devuelve mensajes de error claros. (OWASP Foundation, 2025, A05; W3C, 2024, criterio 3.3.1)
DAT-06. Los datos de referencia y los modelos que usa están citados con su versión y su DOI. (Requisitos para datos, INV-01 y DEP-07)
DAT-07. Si consulta APIs externas, maneja las fallas, los límites de uso y el almacenamiento temporal, y no deja claves en el navegador. (OWASP Foundation, 2025, A02 y A10)
DAT-08 (RECOMENDADO). La aplicación incluye un conjunto de ejemplo con entradas y resultados esperados. (Requisito de esta guía)

### Seguridad y privacidad
SEG-01 (CRÍTICO). Ningún secreto (clave, token, contraseña) está en el repositorio ni en su historial. (OWASP Foundation, 2025, A02)
SEG-02 (CRÍTICO). Si la aplicación recoge o procesa datos personales, cumple la Ley 1581 de 2012 (finalidad, autorización y aviso de privacidad); si no los recoge, lo declara. (Congreso de la República, 2012; Digital Public Goods Alliance, s. f., indicador 7)
SEG-03 (CRÍTICO). Los archivos o datos que sube una persona usuaria no se guardan ni se envían a terceros sin que la persona lo sepa y lo autorice; por defecto se eliminan al terminar la sesión. (Congreso de la República, 2012; Digital Public Goods Alliance, s. f., indicador 9)
SEG-04. La aplicación se revisó contra la lista OWASP Top 10:2025 y el repositorio conserva el resultado y las medidas. (OWASP Foundation, 2025)
SEG-05. Las dependencias tienen alertas automáticas de vulnerabilidades y una política de actualización. (GitHub, s. f.; OWASP Foundation, 2025, A03)
SEG-06. La aplicación no evalúa ni ejecuta código ni deserializa datos que provengan de la persona usuaria, y limita el tipo y el tamaño de los archivos que acepta. (OWASP Foundation, 2025, A05 y A08)
SEG-07. Se sirve solo por HTTPS y sin contenido mixto. (OWASP Foundation, 2025, A04)
SEG-08. Los errores no muestran trazas, rutas ni datos internos a la persona usuaria. (OWASP Foundation, 2025, A02 y A10)
SEG-09. Los registros (*logs*) no contienen datos personales y se conservan por un tiempo limitado. (OWASP Foundation, 2025, A09)
SEG-10. Si hay autenticación, usa un proveedor estándar y no almacena contraseñas propias (aplica solo si hay autenticación). (OWASP Foundation, 2025, A01 y A07)
SEG-11 (RECOMENDADO). Hay límites de uso por solicitud o por persona para evitar el abuso de los recursos. (Requisito de esta guía)
SEG-12 (RECOMENDADO). El repositorio publica un `SECURITY.md` con el canal para reportar vulnerabilidades y se ejecuta OpenSSF Scorecard. (OpenSSF, s. f.)

### Accesibilidad y usabilidad
ACC-01. La aplicación se probó contra WCAG 2.2 niveles A y AA, que incluye los criterios de WCAG 2.1 nivel AA que la Resolución 1519 de 2020 exige a las entidades públicas. (W3C, 2024; MinTIC, 2020, art. 3 y anexo 1)
ACC-02 (CRÍTICO). Todas las funciones se operan con teclado, con foco visible y orden lógico. (W3C, 2024, criterios 2.1.1 y 2.4.7; MinTIC, 2020, anexo 1)
ACC-03. Los formularios tienen etiquetas e instrucciones, identifican los errores y sugieren cómo corregirlos, y exponen nombre, función y valor a las tecnologías de apoyo. (W3C, 2024, criterios 3.3.1, 3.3.2, 3.3.3 y 4.1.2)
ACC-04. Los resultados en mapas o gráficos tienen una alternativa en texto o tabla, y el color no es el único medio de transmitir información. (W3C, 2024, criterios 1.1.1 y 1.4.1)
ACC-05. El contenido se amplía al 200 % sin pérdida y se puede usar en un teléfono. (W3C, 2024, criterios 1.4.4 y 1.4.10)
ACC-06. Se hicieron pruebas automáticas y una revisión manual con teclado y un lector de pantalla gratuito (NVDA, VoiceOver u Orca), y se publicó una declaración de accesibilidad. (Analysis Function, 2026)
ACC-07. Los pasos que exigen repetir información o autenticarse tienen alternativas accesibles (aplica solo si hay autenticación o procesos de varios pasos). (W3C, 2024, criterios 3.3.7 y 3.3.8)
ACC-08 (RECOMENDADO). La interfaz está en español y su texto está separado del código para poder traducirlo. (Requisito de esta guía)
ACC-09 (RECOMENDADO). La aplicación es usable con conectividad limitada: la carga inicial es liviana y los procesos largos informan su avance. (Requisito de esta guía)

### Documentación, mantenimiento y uso de IA
DOC-01 (CRÍTICO). El `README` permite a una persona técnica que no conoce el proyecto instalarlo, ejecutarlo, configurarlo, probarlo y citarlo. (Digital Public Goods Alliance, s. f., indicador 5)
DOC-02. Existe una guía de uso con ejemplos de entradas y de resultados esperados. (Digital Public Goods Alliance, s. f., indicador 5)
DOC-03. La documentación explica los métodos, las ecuaciones, los supuestos, la validación y las limitaciones, con referencias. (Requisito de esta guía)
DOC-04. Un `CHANGELOG.md` registra los cambios de cada versión. (Preston-Werner, s. f.)
DOC-05. Existe una política de mantenimiento: responsable, versiones con soporte, tiempos de respuesta y criterio de retiro, con archivo del código y de los datos al retirarla. (Analysis Function, 2026)
DOC-06. Hay un canal para reportar errores y recibir contribuciones (*issues* o correo). (Requisito de esta guía)
DOC-07. Se declaran los estándares y las buenas prácticas que sigue (por ejemplo, formatos OGC, GeoJSON o una especificación OpenAPI si ofrece una API). (Digital Public Goods Alliance, s. f., indicador 8)
DOC-08. El uso de IA en la preparación del código, los textos o los datos se declara según los [requisitos para el uso de IA](05-uso-de-ia.md). (Requisitos para el uso de IA, U04)
DOC-09. Si la aplicación llama a un modelo de IA al ejecutarse, el modelo y la versión están fijados y documentados, la aplicación avisa a la persona usuaria, no le envía datos personales, ofrece un modo sin IA o una salida guardada y etiqueta las salidas generadas (aplica solo si la aplicación llama a un modelo de IA). (Requisitos para el uso de IA, U11, U12 y U20)

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
Escribe `reporte_aplicacion.json` con esta forma:
{"repositorio": "...", "fecha": "AAAA-MM-DD", "modo": "...", "resultado_global": "...", "puntaje_total": 0.0, "nivel": "...", "criterios": [{"id": "XXX-00", "estado": "...", "evidencia": "...", "accion": "...", "prioridad": "..."}], "revision_humana": ["..."], "no_verificables": ["XXX-00"]}

Termina con un resumen de cinco líneas y la ruta de los archivos generados.
````

**Compuertas críticas.** El prompt trata como bloqueantes los 11 criterios críticos y exige además un puntaje de 90 o más en los obligatorios. Estas reglas son criterios propios de la SCR.

## Referencias

Binder Project. (s. f.). *Ensure reproducibility for your Binder*. The Binder Project. Recuperado el 16 de noviembre de 2026, de https://mybinder.readthedocs.io/en/latest/tutorials/reproducibility.html

Chue Hong, N. P., Katz, D. S., Barker, M., y FAIR4RS Working Group. (2022). *FAIR Principles for Research Software (FAIR4RS Principles)* (Versión 1.0) [Recomendación del Research Data Alliance]. https://doi.org/10.15497/RDA00068

Citation File Format. (s. f.). *Citation File Format*. Recuperado el 16 de noviembre de 2026, de https://citation-file-format.github.io/

Congreso de la República de Colombia. (2012). *Ley 1581 de 2012, por la cual se dictan disposiciones generales para la protección de datos personales*.

Digital Public Goods Alliance. (s. f.). *DPG Standard* [Especificación en línea]. GitHub. Recuperado el 16 de noviembre de 2026, de https://github.com/DPGAlliance/DPG-Standard

Government Analysis Function. (2026). *Data visualisation: testing dashboards for design and accessibility*. Gobierno del Reino Unido. https://analysisfunction.civilservice.gov.uk/policy-store/data-visualisation-testing-dashboards-for-design-and-accessibility

GitHub. (s. f.). *Dependabot quickstart guide*. GitHub Docs. Recuperado el 16 de noviembre de 2026, de https://docs.github.com/en/code-security/getting-started/dependabot-quickstart-guide

Ministerio de Tecnologías de la Información y las Comunicaciones. (2020). *Resolución 1519 de 2020, por la cual se definen los estándares y directrices para publicar la información señalada en la Ley 1712 del 2014 y se definen los requisitos materia de acceso a la información pública, accesibilidad web, seguridad digital y datos abiertos* (Diario Oficial n.º 51.521 de 7 de diciembre de 2020). https://normas.cra.gov.co/gestor/docs/resolucion_mintic_1519_2020.htm

OpenSSF. (s. f.). *OpenSSF Scorecard*. Open Source Security Foundation. Recuperado el 16 de noviembre de 2026, de https://github.com/ossf/scorecard

OWASP Foundation. (2025). *OWASP Top 10:2025*. https://top10.owasp.org/2025

Preston-Werner, T. (s. f.). *Semantic Versioning 2.0.0*. Recuperado el 16 de noviembre de 2026, de https://semver.org/lang/es/

Quarto. (s. f.). *Dashboard deployment*. Posit. Recuperado el 16 de noviembre de 2026, de https://quarto.org/docs/dashboards/deployment.html

Software Heritage. (s. f.). *Software Heritage: the universal source code archive*. Recuperado el 16 de noviembre de 2026, de https://www.softwareheritage.org/

World Wide Web Consortium. (2024). *Web Content Accessibility Guidelines (WCAG) 2.2* [Recomendación del W3C, 12 de diciembre de 2024]. https://www.w3.org/TR/WCAG22/

Wiggins, A. (2017). *The twelve-factor app*. https://12factor.net/
