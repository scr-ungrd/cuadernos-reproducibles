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

La Subdirección para el Conocimiento del Riesgo (SCR) de la UNGRD recibe cuadernos reproducibles que documenten análisis de riesgo de desastres en Colombia. La convocatoria es abierta, gratuita y permanente, y está dirigida a la academia, las entidades del SNGRD, las organizaciones técnicas y las personas profesionales. Este documento explica qué cuadernos aceptamos, cómo postularlos y cómo los evaluamos.

+++

:::{warning} Fase piloto
La convocatoria aún no está abierta. Prevemos abrirla en el segundo semestre de 2026. Mientras tanto, esta página describe el proceso que seguiremos.
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

### Requisitos técnicos

Cada cuaderno cumple lo siguiente:

- **Formato.** Jupyter (`.ipynb`) o MyST Markdown con código. Se ejecuta de principio a fin sin intervención manual.
- **Lenguaje.** Python 3.10 o superior. Aceptamos R con `renv`. No aceptamos cuadernos que requieran software de pago.
- **Datos.** Públicos, gratuitos y redistribuibles, y conformes al [estándar de datos](03-estandar-de-datos.md). No aceptamos datos confidenciales ni con restricciones de redistribución.
- **Dependencias.** Un archivo `environment.yml` o `requirements.txt` con versiones fijadas. Los paquetes están en PyPI o conda-forge.
- **Reproducibilidad.** Se ejecuta en Binder o Google Colab sin configuración adicional.
- **Visualización.** Al menos un mapa o un gráfico interactivo.
- **Territorio.** El análisis se refiere a Colombia o a una región del país.
- **Licencia.** Abierta: MIT o Apache-2.0 para el código, y CC BY 4.0 para los datos y el texto.
- **Idioma.** Preferimos el español. Aceptamos el inglés con un resumen en español.
- **Extensión.** Entre 500 y 3000 líneas de código. Si es más largo, divídalo en módulos.
- **Uso de IA.** Declárelo según el [instructivo de uso de IA](05-uso-de-ia.md).

Si el cuaderno incluye un modelo, un tablero o una aplicación, cumpla además el [estándar de modelos](08-estandar-modelos.md), el [estándar de tableros](06-estandar-tableros.md) o el [estándar de aplicaciones](07-estandar-aplicaciones.md).

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

## Cómo postular

La postulación tiene cuatro pasos.

1. **Cree el repositorio.** Cada cuaderno vive en su propio repositorio público. Abra la [plantilla](https://github.com/scr-ungrd/cuadernos-reproducibles-crc000), pulse **Use this template → Create a new repository** y clónelo.
2. **Ubique el cuaderno.** Copie el cuaderno en `notebooks/` y los datos de prueba en `data/`. Actualice `myst.yml` (autores, afiliaciones, palabras clave) y `environment.yml` (dependencias).
3. **Verifique.** Ejecute el cuaderno desde cero en un entorno limpio y compruebe que `myst build --html` funciona.
4. **Postule.** Abra un *issue* en el [repositorio de la plataforma](https://github.com/scr-ungrd/cuadernos-reproducibles/issues) con el enlace al repositorio y estos datos: nombre del cuaderno y autoría, institución, amenaza o fenómeno, región, fuentes de datos y una descripción del método de máximo 200 palabras.

La SCR revisa la postulación y puede pedir ajustes antes de publicar. Si no tiene cuenta de GitHub, escriba al equipo de la SCR y lo acompañamos en el proceso.

### Postular con un asistente de IA

Un asistente con acceso a su equipo y a GitHub (por ejemplo, Claude Code, Codex o Copilot en modo agente) puede hacer los pasos 1 a 4. Copie este prompt y reemplace los valores entre `<>`. Revise siempre lo que genere: la responsabilidad por el contenido, los datos y las licencias es de la autoría.

````text
Quiero postular un cuaderno reproducible a la convocatoria de Cuadernos Reproducibles de Conocimiento del Riesgo de la UNGRD. Ayúdame paso a paso.

Datos del cuaderno:
- Nombre del cuaderno: <nombre>
- Autores: <nombres>
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
6. Con mi confirmación, haz commit y push, y abre un issue en https://github.com/scr-ungrd/cuadernos-reproducibles/issues con el enlace a mi repositorio y los datos de la postulación (nombre y autores, institución, amenaza, región, fuentes y una descripción del método de máximo 200 palabras).

Reglas:
- No inventes datos, resultados ni referencias; si falta información, pregúntame.
- No publiques nada (push, repositorio público o issue) sin mi confirmación.
- No incluyas credenciales, tokens ni datos personales en el repositorio.
````

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

Para consultas sobre la convocatoria, escriba a la SCR abriendo un *issue* en [`scr-ungrd/cuadernos-reproducibles`](https://github.com/scr-ungrd/cuadernos-reproducibles/issues).
