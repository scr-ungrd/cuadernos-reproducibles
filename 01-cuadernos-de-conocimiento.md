---
title: Guía para publicar un cuaderno
subtitle: Cómo preparar y enviar un cuaderno reproducible de conocimiento del riesgo
date: 2026-11-16
license: CC-BY-4.0
keywords:
  - cuadernos reproducibles
  - Python
  - amenaza
  - vulnerabilidad
  - exposición
  - riesgo de desastres
  - FAIR
abbreviations:
  UNGRD: Unidad Nacional para la Gestión del Riesgo de Desastres
  SCR: Subdirección para el Conocimiento del Riesgo
  FAIR: Findable, Accessible, Interoperable, Reusable
  RDLS: Risk Data Library Standard
  DOI: Digital Object Identifier
---

+++ {"part": "abstract"}

Un cuaderno reproducible reúne en un solo repositorio la narrativa, el código y los resultados de un análisis de riesgo, de modo que otra persona pueda ejecutarlo y obtener los mismos resultados. Esta guía explica cómo preparar y enviar uno a la colección de la Subdirección para el Conocimiento del Riesgo (SCR) de la UNGRD. Cubre el tipo de cuaderno, el repositorio, la estructura del texto y el control de calidad previo al envío.

+++

## Pasos clave

1. **Elija el tipo de cuaderno** (Sección 1).
2. **Prepare el repositorio** en GitHub (Sección 2).
3. **Prepare los datos** según los [requisitos para datos](03-estandar-de-datos.md).
4. **Escriba el cuaderno** con la estructura de la Sección 3.
5. **Declare el uso de IA** según los [requisitos para el uso de IA](05-uso-de-ia.md).
6. **Revise la seguridad del repositorio** según los [requisitos de seguridad](10-requisitos-seguridad.md).
7. **Verifique el cuaderno** en un entorno limpio (Sección 4).
8. **Envíe el repositorio** según la [convocatoria](02-convocatoria-cuadernos.md).

Si el cuaderno incluye un modelo, un tablero o una aplicación, cumpla además los [requisitos para modelos](08-estandar-modelos.md), los [requisitos para tableros](06-estandar-tableros.md) o los [requisitos para aplicaciones](07-estandar-aplicaciones.md). Si usa un modelo de lenguaje u otro modelo preentrenado de terceros (por ejemplo, de Hugging Face) como componente del análisis, cumpla los [requisitos para el uso de LLMs](09-uso-de-llms.md).

:::{note} Qué son los requisitos de esta colección
Los requisitos de esta guía y de sus documentos de apoyo son propios de la Subdirección para el Conocimiento del Riesgo. Cada uno tiene un identificador, un nivel (obligatorio, recomendado o crítico) y una base documental; los que dicen «Requisito de esta guía» son criterio de la SCR. No son normas técnicas emitidas por un organismo de normalización, como ICONTEC o ISO, ni una certificación: cumplirlos es una condición para publicar en la colección y no una acreditación externa.
:::

## 1. Elija el tipo de cuaderno

Un cuaderno reproducible no es un script con comentarios. Es un documento ejecutable que combina texto, código verificable, datos accesibles y resultados interpretables. Cada cuaderno corresponde a una de cuatro líneas, que siguen el Marco de Sendai 2015–2030 y la Ley 1523 de 2012.

```{list-table}
:header-rows: 1

* - Tipo
  - Qué documenta
  - Qué esperamos
* - **Evaluación de amenazas**
  - Caracterización, modelación o cartografía de amenazas naturales, socionaturales o antrópicas en Colombia
  - Series históricas de fuentes institucionales (UNGRD, IDEAM, SGC, IGAC). Valoramos los enfoques probabilísticos y los escenarios de cambio climático.
* - **Análisis de riesgo**
  - Combinación de amenaza, exposición y vulnerabilidad para estimar el riesgo municipal, departamental o de cuenca
  - Cuadernos encadenados que separan la evaluación de la amenaza del análisis del riesgo.
* - **Indicadores de vulnerabilidad y exposición**
  - Construcción, validación o comparación de indicadores de vulnerabilidad social, física o funcional y de exposición
  - Datos abiertos (DANE, Registro Único de Damnificados, catastro multipropósito) y criterios documentados de selección, normalización y ponderación.
* - **Metodologías transversales**
  - Herramientas, flujos de procesamiento o marcos aplicables a más de una amenaza o escala
  - Un valor que resida en la generalidad del método y no en el caso de aplicación.
```

**Tecnología.** Todos los cuadernos usan la misma base:

- **MyST Markdown** para el texto, las referencias cruzadas y los metadatos.
- **Python 3.10 o superior** para todo el código. Recomendamos `xarray`, `geopandas`, `rasterio`, `pandas`, `matplotlib`, `cartopy` y `numpy`; puede usar otras si las justifica.
- **Jupyter** para la ejecución. El cuaderno debe correr de principio a fin sin intervención manual, salvo la descarga de datos externos cuando sea inevitable.
- **GitHub** para el control de versiones. No evaluamos cuadernos sin un repositorio público.

Si el cuaderno usa o produce datos de riesgo, descríbalos con el Risk Data Library Standard (RDLS) del GFDRR. Así se pueden combinar con otras colecciones abiertas.

## 2. Prepare el repositorio

El repositorio contiene como mínimo:

- `README.md` con el título, una descripción breve, las instrucciones de instalación, los datos de entrada y un ejemplo de ejecución.
- `environment.yml` o `requirements.txt` con todas las dependencias y sus versiones fijadas.
- `notebooks/` con los cuadernos `.ipynb` numerados en orden de ejecución.
- `data/` con los datos de ejemplo para una versión mínima, o instrucciones para descargarlos.
- `LICENSE` con una licencia abierta. Recomendamos Apache-2.0 o MIT para el código y CC BY 4.0 para los datos y el texto.
- `CITATION.cff` con el ORCID de cada persona autora.
- `AUTHORS.md` (opcional) con el rol de cada persona según la taxonomía CRediT (por ejemplo, conceptualización, curaduría de datos, software, validación) y la institución con su identificador ROR.

Añada un botón de Binder al `README` para que cualquier persona ejecute el cuaderno en la nube sin instalar nada.

**Principios FAIR.** El repositorio cumple los cuatro principios así:

- **Encontrable.** Registre el repositorio en Zenodo para obtener un DOI antes de la evaluación final. El `README` incluye título, autores, institución, palabras clave (amenaza, departamento, escala) y el DOI.
- **Accesible.** El repositorio es público. Los datos de entrada están en formatos abiertos (GeoTIFF, GeoJSON, CSV, NetCDF) y sin restricciones que impidan reutilizarlos. Si provienen de una fuente restringida, explique cómo solicitarlos e incluya una muestra o datos sintéticos que permitan ejecutar todo el flujo.
- **Interoperable.** Los formatos funcionan con las bibliotecas estándar de Python científico. Declare en el código las unidades, el sistema de coordenadas y los nombres de las variables.
- **Reutilizable.** El código está en funciones con *docstrings*. El texto explica por qué se tomó cada decisión (parámetros, umbrales, fuentes). Una persona técnica debe poder adaptar el cuaderno a otro municipio o amenaza sin contactar a quien lo escribió.

## 3. Escriba el cuaderno

El cuaderno tiene seis secciones, en este orden, escritas en celdas de texto MyST entre el código.

**Contexto y objetivo.** Describa el problema, la escala territorial y por qué eligió el método. No incluya resultados.

**Datos de entrada.** Indique la fuente, el formato, la resolución espaciotemporal y las limitaciones de cada dato. Enlace al archivo o registro exacto, no a la página de inicio de la fuente. Si el dato se actualiza de forma continua, registre la versión o los parámetros de la consulta.

**Metodología.** Explique cada bloque de código paso a paso y comente las operaciones no triviales. No incluya resultados ni descripciones generales de la herramienta.

**Resultados e interpretación.** Presente visualizaciones comentadas e interprételas en términos de gestión del riesgo. Genere cada figura con código, a partir de los datos.

**Limitaciones y recomendaciones.** Declare los supuestos, las incertidumbres no cuantificadas y cómo ampliar el análisis. Sea específico: una limitación genérica no ayuda a quien reutiliza el cuaderno.

**Referencias.** Use la directiva `{bibliography}` de MyST con un archivo `.bib` en el repositorio.

## 4. Verifique el cuaderno

Antes del envío, compruebe que:

- el cuaderno se ejecuta de principio a fin en un entorno limpio creado desde `environment.yml` o `requirements.txt`;
- ninguna celda depende de variables definidas fuera de orden;
- las rutas son relativas al repositorio;
- el repositorio tiene al menos un *release* en GitHub y la versión correspondiente en Zenodo tiene un DOI activo.

**Verificación independiente.** Una persona del comité evaluador ejecuta el cuaderno en un entorno limpio y comprueba que reproduce las figuras y las tablas, siguiendo el proceso de CODECHECK (Nüst y Eglen, 2021). Pedimos esta comprobación porque la reproducibilidad solo se puede certificar cuando alguien distinto de quien escribió el cuaderno lo ejecuta sin ayuda. El informe de verificación (fecha, entorno, resultado y diferencias) se publica junto al cuaderno. Verificar no es replicar: el informe confirma que el código y los datos regeneran los resultados, no que estos sean correctos.

**Transparencia.** La colección sigue las directrices TOP 2025 (*Transparency and Openness Promotion*), que piden declarar, compartir y citar los datos, el código y los materiales de un estudio (Center for Open Science, 2025). Los requisitos de esta guía las concretan: datos, código, modelos, uso de IA y seguridad.

## Ejemplos de referencia

Esta guía adapta el modelo de colecciones abiertas como el [Manual de Evaluación del Riesgo Climático de CLIMAAX](https://handbook.climaax.eu/intro.html), la [Risk Data Library del GFDRR](https://gfdrr.github.io/CCDR-tools/home.html), [DesignSafe](https://www.designsafe-ci.org/), [Probability of Fire del ECMWF](https://ecmwf.github.io/AI-Probability-of-Fire), el [Proyecto Pythia](https://projectpythia.org/) y [EM-DAT](https://github.com/em-dat/).

## Referencias

Center for Open Science. (2025). *TOP 2025: An update to the Transparency and Openness Promotion guidelines*. https://doi.org/10.31222/osf.io/nmfs6

Nüst, D., y Eglen, S. J. (2021). CODECHECK: An open science initiative for the independent execution of computations underlying research articles during peer review to improve reproducibility. *F1000Research, 10*, Artículo 253. https://doi.org/10.12688/f1000research.51738.2
