---
title: Cuadernos Reproducibles de Conocimiento del Riesgo de Desastres
site:
  hide_title_block: true
  hide_toc: true
  hide_outline: true
---

:::::{div}
:class: hero col-screen

```{image} ./images/hero-barranquilla-sentinel2.jpg
:alt: Imagen satelital Sentinel-2 de Barranquilla y la desembocadura del río Magdalena
:class: hero-bg
```

::::{div}
:class: hero-content

SUBDIRECCIÓN PARA EL CONOCIMIENTO DEL RIESGO · UNGRD

# Cuadernos Reproducibles de Conocimiento del Riesgo

Publicamos cuadernos abiertos, ejecutables e interactivos que muestran cómo realizar análisis en los tres procesos de la gestión del riesgo de desastres en Colombia: conocimiento del riesgo, reducción del riesgo y manejo de desastres. Se promueve el uso de datos públicos, flujos de trabajo con código y resultados que cualquiera puede reproducir.

{button}`Cuadernos recientes <#cuadernos>`
::::

::::{div}
:class: hero-credit

Imagen: Barranquilla y el río Magdalena, 31 de marzo de 2024. Contiene datos modificados de Copernicus Sentinel (2024), Unión Europea.
::::
:::::

:::{warning} Proyecto en fase piloto
Este proyecto está en fase piloto, por lo que la convocatoria no está abierta. El proyecto se presenta únicamente con fines de demostración y prueba, ya que los cuadernos no se han validado por expertos.
:::

:::{div}
:class: intro

**Cuadernos Reproducibles de Conocimiento del Riesgo de Desastres** es una colección de la Unidad Nacional para la Gestión del Riesgo de Desastres (UNGRD). Cada cuaderno es **interactivo**: contiene un marco teórico, código y resultados en un mismo documento, el cual puede ejecutarse en la nube, sin necesidad de instalar nada localmente.

Los cuadernos cubren todo tipo de temáticas y se dirigen a equipos profesionales, autoridades territoriales, academia y quienes toman decisiones en **gestión del riesgo de desastres**. Todo se publica bajo principios de **ciencia abierta**.

Este modelo de publicación busca resolver dos problemas centrales de los análisis de riesgo de desastres: la falta de transparencia y reproducibilidad de los resultados, y la desconexión entre el texto narrativo de un trabajo (artículo científico, capítulo de libro, artefacto, aplicación, etc.) y el código, los datos y los parámetros que realmente sustentan sus conclusiones y usos, lo que dificulta verificarlas y reutilizarlas ([Caprarelli et al., 2023](https://doi.org/10.1029/2023EA003458)).

:::

(cuadernos)=
## Cuadernos recientes

::::{card}
:url: https://scr-ungrd.github.io/cuadernos-reproducibles-crc001

![Mapa de riesgo por olas de calor urbano en Montería](./images/olas-calor-monteria.png)

**Riesgo por olas de calor urbano en Montería, Córdoba, bajo escenarios de cambio climático**

Proyección del cambio climático, olas de calor y riesgo relativo por calor urbano en Montería, en seis fases y con tres escenarios del CMIP6, según el marco del IPCC AR6. Usa datos abiertos de IDEAM, ERA5-Land, NEX-GDDP-CMIP6, Landsat, ESA WorldCover, WorldPop y OpenStreetMap. Incluye declaración de datos, uso de IA documentado y DOI en Zenodo. Ejercicio sin validar.

Subdirección para el Conocimiento del Riesgo · v2.0.0 · 16 nov 2026
::::

::::{card}
:url: https://scr-ungrd.github.io/cuadernos-reproducibles-crc002

![Fotografía del tsunami de Tumaco de 1979](./images/tsunami-1.avif)

**Simulación del Tsunami de Tumaco de 1979 con Google Colab**

Propagación del tsunami del 12 de diciembre de 1979 (Mw 8,3) en el Pacífico colombiano, con una fuente de Okada y aguas someras no lineales con fricción de Manning y celda seca (versión 3.0.0, en desarrollo; las ecuaciones lineales de la 2.2.2 se conservan como comparación), en tres cuadernos que corren en CPU. Contrasta la simulación con las observaciones de Herd et al. (1981) y de NOAA/NGDC, que no coinciden entre sí, e incluye ficha del modelo y límites explícitos. Ejercicio sin validar.

Subdirección para el Conocimiento del Riesgo · v2.2.2 (3.0.0 en desarrollo) · 17 nov 2026
::::

::::{card}
:url: https://scr-ungrd.github.io/cuadernos-reproducibles-crc003

![Mapa de sismicidad de Colombia](./images/crc003-sismicidad.png)

**Análisis de sismicidad de Colombia**

Sismicidad de Colombia con el catálogo del USGS (2000–2026): magnitud de completitud, relación de Gutenberg-Richter por máxima verosimilitud (b = 1,22, valor corregido en la versión 0.1.1, en desarrollo; la 0.1.0 publicada daba 1,07), profundidad focal, cortes transversales, mapas interactivos y una ficha piloto de Córdoba. Describe amenaza, no riesgo. Incluye ficha del modelo. Ejercicio sin validar.

Subdirección para el Conocimiento del Riesgo · v0.1.0 (0.1.1 en desarrollo) · 17 nov 2026
::::


:::{div}
:class: see-all

[Guía para publicar un cuaderno](01-cuadernos-de-conocimiento.md) · [Convocatoria](02-convocatoria-cuadernos.md) · [Requisitos para datos](03-estandar-de-datos.md) · [Requisitos para el uso de IA](05-uso-de-ia.md) · [Requisitos para tableros](06-estandar-tableros.md) · [Requisitos para aplicaciones](07-estandar-aplicaciones.md) · [Requisitos para modelos](08-estandar-modelos.md) · [Requisitos para el uso de LLMs](09-uso-de-llms.md) · [Requisitos de seguridad](10-requisitos-seguridad.md)
:::
