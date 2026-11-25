---
title: Convocatoria
subtitle: Cuadernos reproducibles para la gestión del riesgo de desastres en Colombia
authors:
  - name: Subdirección para el Conocimiento del Riesgo
    affiliation: Unidad Nacional para la Gestión del Riesgo de Desastres (UNGRD)
    github: scr-ungrd
keywords: [convocatoria, cuadernos reproducibles, gestión del riesgo, Colombia, ciencia abierta]
date: 2026-11-16
license: CC-BY-4.0
---

+++ {"part": "abstract"}

La Subdirección para el Conocimiento del Riesgo (SCR) de la UNGRD recibe cuadernos reproducibles que documenten análisis de riesgo de desastres en Colombia. La convocatoria será abierta, gratuita y permanente, y estará dirigida a la academia, las entidades del SNGRD, las organizaciones técnicas y las personas profesionales. Este documento explica qué cuadernos aceptamos, cómo postularlos y cómo los evaluamos.

+++

:::{warning} Fase piloto
La convocatoria está en fase piloto y abrirá el 1 de marzo de 2027. Mientras tanto, esta página describe el proceso que seguiremos.
:::

## Por qué la convocatoria

Colombia está expuesta a amenazas de origen natural por su actividad tectónica, su variabilidad climática y su relieve. Entender ese riesgo requiere métodos y datos que otras personas puedan verificar y reutilizar. Hoy buena parte de ese conocimiento está en artículos o informes sin datos ni código, y es difícil de reproducir, sobre todo para los actores locales.

Queremos reunir una biblioteca de cuadernos reproducibles que documenten metodologías para el análisis de amenazas, vulnerabilidad, exposición y riesgo. Con ella buscamos:

- vincular a la comunidad técnica y científica con la plataforma de la UNGRD;
- documentar métodos reproducibles con datos y herramientas abiertas, según los principios FAIR;
- aportar a la Prioridad 1 del Marco de Sendai 2015–2030, comprender el riesgo de desastres.

El modelo se inspira en el [Manual de Evaluación del Riesgo Climático de CLIMAAX](https://handbook.climaax.eu/intro.html) y en las herramientas abiertas del GFDRR.

## Quién puede postular

Puede postular cualquier persona u organización, de Colombia o del exterior:

- grupos de investigación y universidades;
- entidades técnicas del SNGRD (SGC, IDEAM, DIMAR, IGAC, INVÍAS y otras);
- organizaciones no gubernamentales con trabajo técnico en gestión del riesgo;
- consultoras, profesionales independientes y equipos de gobierno;
- estudiantes de posgrado con aval de una persona directora o investigadora.

Los cuadernos pueden tener varias personas autoras y no hay límite de postulaciones. Valoramos las metodologías internacionales que se adapten al contexto colombiano.

## Qué cuadernos aceptamos

Aceptamos cuadernos de cuatro tipos: evaluación de amenazas, análisis de riesgo, indicadores de vulnerabilidad y exposición, y metodologías transversales (véase la [guía](01-cuadernos-de-conocimiento.md)). Los temas incluyen, sin limitarse a ellos:

- amenazas geológicas: sismicidad, volcanes, movimientos en masa, tsunamis;
- amenazas hidrometeorológicas y climáticas: inundaciones, avenidas torrenciales, sequías, incendios, olas de calor, cambio climático, El Niño;
- vulnerabilidad y exposición de la población y la infraestructura;
- aprendizaje automático y teledetección aplicados a la gestión del riesgo;
- datos y monitoreo: sensores remotos, series hidrometeorológicas y redes de observación.

(requisitos-tecnicos)=
### Requisitos técnicos

Cada cuaderno cumple lo siguiente:

- **Formato.** Jupyter (`.ipynb`) o MyST Markdown (`.md` con celdas `{code-cell}`). La plantilla convierte el `.md` a `.ipynb` con `jupytext`. Se ejecuta de principio a fin sin intervención manual.
- **Lenguaje.** Python 3.10 o superior. En el nivel A también aceptamos R con `renv`. No aceptamos cuadernos que requieran software de pago.
- **Datos.** Públicos, gratuitos y redistribuibles, y conformes a los [requisitos para datos](03-estandar-de-datos.md). No aceptamos datos confidenciales ni con restricciones de redistribución.
- **Dependencias.** Un archivo `environment.yml` o `requirements.txt` con versiones fijadas. Los paquetes están en PyPI o conda-forge.
- **Reproducibilidad.** Se ejecuta en Binder o Google Colab sin configuración adicional.
- **Visualización.** Al menos un mapa o un gráfico interactivo.
- **Territorio.** El análisis se refiere a Colombia o a una región del país.
- **Licencia.** Abierta: MIT o Apache-2.0 para el código, y CC BY 4.0 para los datos y el texto.
- **Idioma.** Preferimos el español. Aceptamos el inglés con un resumen en español.
- **Extensión.** Entre 500 y 3000 líneas de código. Si es más largo, divídalo en módulos.
- **Uso de IA.** Declárelo según los [requisitos para el uso de IA](05-uso-de-ia.md).
- **Seguridad.** Cumpla los [requisitos de seguridad](10-requisitos-seguridad.md): sin credenciales, datos personales ni rutas locales en el repositorio, el historial ni las salidas.

Si el cuaderno incluye un modelo, un tablero o una aplicación, cumpla además los [requisitos para modelos](08-estandar-modelos.md), los [requisitos para tableros](06-estandar-tableros.md) o los [requisitos para aplicaciones](07-estandar-aplicaciones.md). Si usa un modelo de lenguaje u otro modelo preentrenado de terceros como componente del análisis, cumpla los [requisitos para el uso de LLMs](09-uso-de-llms.md).

### Fuentes de datos recomendadas

```{list-table}
:header-rows: 1

* - Fuente
  - Datos
  - Acceso
* - USGS Earthquake Catalog
  - Sismicidad global
  - API gratuita
* - IDEAM (datos.gov.co)
  - Hidrometeorología y clima
  - Portal de datos abiertos
* - SGC
  - Geología, sismología y vulcanología
  - Descarga directa
* - NASA FIRMS
  - Incendios activos
  - API gratuita
* - Copernicus y ERA5
  - Reanálisis climático
  - API gratuita
* - CHIRPS
  - Precipitación
  - Descarga directa
* - IGAC
  - Cartografía base
  - Portal abierto
* - DANE
  - Censos y demografía
  - Portal de datos abiertos
* - Google Earth Engine
  - Imágenes satelitales
  - Gratuito con cuenta de Google
* - OpenStreetMap
  - Infraestructura y red vial
  - Descarga libre
```

Las bibliotecas más usadas son `pandas`, `numpy`, `scipy`, `xarray` y `statsmodels` para los datos; `geopandas`, `rasterio`, `folium`, `leafmap` y `cartopy` para lo geoespacial; `matplotlib`, `seaborn` y `plotly` para la visualización, y `scikit-learn` para el aprendizaje automático.

(como-postular)=
## Cómo postular

Puede postular por tres niveles, según su experiencia con GitHub. Los tres llegan al mismo punto: todo cuaderno evaluado termina en un repositorio público que cumple los [requisitos técnicos](#requisitos-tecnicos).

```{list-table}
:header-rows: 1

* - Nivel
  - Qué envía
  - Por dónde
  - Quién crea el repositorio
* - **A. Repositorio propio**
  - El enlace a su repositorio, creado desde la plantilla y verificado
  - [Formulario de postulación](https://github.com/scr-ungrd/cuadernos-reproducibles/issues/new?template=postulacion.yml)
  - Usted
* - **B. Cuaderno con acompañamiento**
  - El cuaderno, las dependencias con versiones fijas y los datos de prueba
  - [Formulario de postulación](https://github.com/scr-ungrd/cuadernos-reproducibles/issues/new?template=postulacion.yml) o correo a [conocimiento@gestiondelriesgo.gov.co](mailto:conocimiento@gestiondelriesgo.gov.co)
  - La UNGRD, con usted
* - **C. Manifestación de interés**
  - Un resumen o un documento Word con la idea, los datos y el método
  - [Formulario de manifestación de interés](https://github.com/scr-ungrd/cuadernos-reproducibles/issues/new?template=manifestacion-interes.yml) o correo a [conocimiento@gestiondelriesgo.gov.co](mailto:conocimiento@gestiondelriesgo.gov.co)
  - Nadie: no se evalúa
```

La exigencia de reproducibilidad es la misma en los tres niveles. Solo evaluamos un cuaderno cuando su repositorio cumple todos los requisitos.

### Nivel A. Repositorio propio

Usted crea el repositorio, lo verifica y lo postula. Son cuatro pasos.

1. **Cree el repositorio.** Cada cuaderno vive en su propio repositorio público. Abra la [plantilla](https://github.com/scr-ungrd/cuadernos-reproducibles-crc000), pulse **Use this template → Create a new repository** y clónelo.
2. **Ubique el cuaderno.** Copie el cuaderno en `notebooks/` y los datos de prueba en `data/`. Actualice `myst.yml` (autores, afiliaciones, palabras clave) y `environment.yml` (dependencias).
3. **Verifique.** Ejecute el cuaderno desde cero en un entorno limpio y compruebe que `myst build --html` funciona.
4. **Postule.** Llene el [formulario de postulación](https://github.com/scr-ungrd/cuadernos-reproducibles/issues/new?template=postulacion.yml) con el nivel A y el enlace al repositorio. El formulario pide el nombre del cuaderno, la autoría con ORCID, la institución, el tipo de cuaderno, la amenaza o fenómeno, la región, las fuentes de datos, una descripción del método de máximo 200 palabras, la declaración de uso de IA y las licencias.

La SCR revisa la postulación y puede pedir ajustes antes de publicar.

#### Postular con un asistente de IA

Un asistente con acceso a su equipo y a GitHub (por ejemplo, Claude Code, Codex o Copilot en modo agente) puede hacer los pasos 1 a 4. Copie este prompt y reemplace los valores entre `<>`. Revise siempre lo que genere: la responsabilidad por el contenido, los datos y las licencias es de la autoría.

````text
Quiero postular un cuaderno reproducible a la convocatoria de Cuadernos Reproducibles de Conocimiento del Riesgo de la UNGRD. Ayúdame paso a paso.

Datos del cuaderno:
- Nombre del cuaderno: <nombre>
- Autores: <nombres y ORCID>
- Institución o afiliación: <institución>
- Amenaza o fenómeno analizado: <amenaza>
- Región geográfica: <región>
- Fuentes de datos: <fuentes>
- Ruta local de mi cuaderno (.ipynb): <ruta>
- Mi usuario de GitHub: <usuario>

Tareas:
1. Crea un repositorio público en mi cuenta de GitHub a partir de la plantilla https://github.com/scr-ungrd/cuadernos-reproducibles-crc000 (nombre sugerido: cuadernos-reproducibles-<codigo-o-tema>) y clónalo.
2. Copia mi cuaderno a notebooks/ y los datos de prueba a data/. Si el cuaderno descarga datos abiertos, deja la descarga automática y documenta el acceso.
3. Actualiza myst.yml (título, autores, afiliaciones, palabras clave, licencia), environment.yml (versiones fijas) y README.md (título, descripción, instalación, datos de entrada y ejemplo de ejecución). Conserva una licencia abierta.
4. Verifica que el cuaderno se ejecute completo en un entorno limpio creado desde environment.yml y que `myst build --html` funcione. Si falla, corrígelo o dime qué necesitas.
5. Muéstrame un resumen de los cambios y espera mi confirmación antes de hacer commit y push.
6. Con mi confirmación, haz commit y push, y prepara el texto del formulario de postulación (https://github.com/scr-ungrd/cuadernos-reproducibles/issues/new?template=postulacion.yml) para el nivel A: enlace a mi repositorio, nombre del cuaderno, autoría con ORCID, institución, tipo de cuaderno, amenaza, región, fuentes de datos, descripción del método de máximo 200 palabras, declaración de uso de IA y licencias. Yo reviso y envío el formulario.

Reglas:
- No inventes datos, resultados ni referencias; si falta información, pregúntame.
- No publiques nada (push, repositorio público o issue) sin mi confirmación.
- No incluyas credenciales, tokens ni datos personales en el repositorio.
````

### Nivel B. Cuaderno con acompañamiento

Use este nivel si su cuaderno ya se ejecuta, pero no quiere o no puede armar el repositorio. Envíe:

- el cuaderno, en `.ipynb` o en `.md` de MyST con celdas `{code-cell}`;
- un `requirements.txt` o un `environment.yml` con las versiones fijas de todas las dependencias;
- los datos de prueba, o los enlaces exactos para descargarlos.

Envíelo por el [formulario de postulación](https://github.com/scr-ungrd/cuadernos-reproducibles/issues/new?template=postulacion.yml), con el nivel B y el enlace a los archivos, o por correo a [conocimiento@gestiondelriesgo.gov.co](mailto:conocimiento@gestiondelriesgo.gov.co). En este nivel el código debe estar en Python.

La UNGRD crea el repositorio desde la plantilla, en su organización de GitHub [`scr-ungrd`](https://github.com/scr-ungrd), con usted. Usted sigue siendo responsable del contenido, los datos y las licencias. La evaluación empieza solo cuando el repositorio cumple los mismos requisitos del nivel A: el cuaderno se ejecuta de principio a fin en un entorno limpio y `myst build --html` funciona.

### Nivel C. Manifestación de interés

Use este nivel si tiene una idea o un análisis en curso y quiere orientación antes de escribir el cuaderno. Envíe un resumen o un documento Word con la idea, los datos y el método, por el [formulario de manifestación de interés](https://github.com/scr-ungrd/cuadernos-reproducibles/issues/new?template=manifestacion-interes.yml) o por correo a [conocimiento@gestiondelriesgo.gov.co](mailto:conocimiento@gestiondelriesgo.gov.co).

La manifestación de interés no se evalúa. Sirve para recibir orientación y pasar luego al nivel A o al B. Un documento Word no se acepta como cuaderno, porque no se ejecuta.

## Cómo evaluamos

El equipo técnico de la SCR y un comité de pares externo evalúan cada cuaderno con estos criterios. Antes, una persona del comité verifica la reproducibilidad: ejecuta el cuaderno en un entorno limpio y publica un informe de verificación junto al cuaderno (véase la [guía](01-cuadernos-de-conocimiento.md)).

```{list-table}
:header-rows: 1

* - Criterio
  - Peso
* - Relevancia para la gestión del riesgo en Colombia
  - 25 %
* - Calidad técnica y reproducibilidad
  - 25 %
* - Claridad de la narrativa y de la documentación
  - 20 %
* - Innovación metodológica
  - 15 %
* - Uso de datos y herramientas abiertas
  - 15 %
```

## Qué ofrecemos

- **Publicación** en la plataforma oficial de la UNGRD, con un DOI y el reconocimiento de la autoría.
- **Difusión** de los mejores cuadernos en eventos técnicos, publicaciones y espacios de formación.
- **Colaboración**: las personas autoras pueden ser convocadas a proyectos de investigación aplicada con la UNGRD y el SNGRD, y su método puede incorporarse a los procesos de la entidad.

Puede actualizar su cuaderno después de publicado: actualice el repositorio y avise en el *issue* de la postulación. El historial queda en git.

## Marco de política

La convocatoria se inscribe en la Ley 1523 de 2012 (política nacional de gestión del riesgo y SNGRD), el Marco de Sendai 2015–2030, los ODS 11 y 13 de la Agenda 2030 y la política nacional de ciencia, tecnología e innovación, que promueve la ciencia abierta.

## Cuaderno de ejemplo

El cuaderno [Análisis de sismicidad de Colombia](https://scr-ungrd.github.io/cuadernos-reproducibles-crc003) (CRC-003) muestra el estilo esperado: usa el catálogo público del USGS 2000–2026, estima la magnitud de completitud y la relación de Gutenberg-Richter, y presenta mapas interactivos de epicentros.

## Contacto

Para consultas sobre la convocatoria, llene el [formulario de consulta](https://github.com/scr-ungrd/cuadernos-reproducibles/issues/new?template=consulta.yml) o escriba a [conocimiento@gestiondelriesgo.gov.co](mailto:conocimiento@gestiondelriesgo.gov.co).
