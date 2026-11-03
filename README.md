# Cuadernos Reproducibles de Conocimiento del Riesgo de Desastres

Portada de la colección de cuadernos computacionales reproducibles sobre gestión del riesgo de desastres (GRD) en Colombia, elaborados por la Subdirección para el Conocimiento del Riesgo (SCR) de la UNGRD.

**Sitio:** <https://scr-ungrd.github.io/cuadernos-reproducibles/>

Este repositorio contiene solo la portada, la guía para publicar un cuaderno y la convocatoria. **Cada cuaderno vive en su propio repositorio** y publica su propio sitio, enlazado desde la portada.

## Cuadernos disponibles

| # | Título | Amenaza | Región | Sitio | Repositorio |
|---|--------|---------|--------|-------|-------------|
| CRC-001 | Proyección de temperatura bajo escenarios de cambio climático | Cambio climático | Montería, Córdoba | [Ver](https://scr-ungrd.github.io/cuadernos-reproducibles-crc001/) | [crc001](https://github.com/scr-ungrd/cuadernos-reproducibles-crc001) |
| CRC-002 | Riesgo por olas de calor urbano | Calor extremo | Cartagena, Bolívar | [Ver](https://scr-ungrd.github.io/cuadernos-reproducibles-crc002/) | [crc002](https://github.com/scr-ungrd/cuadernos-reproducibles-crc002) |
| CRC-003 | Simulación del tsunami de Tumaco de 1979 (versión 2) | Tsunami | Pacífico colombiano | [Ver](https://scr-ungrd.github.io/cuadernos-reproducibles-crc003/) | [crc003](https://github.com/scr-ungrd/cuadernos-reproducibles-crc003) |
| CRC-004 | Análisis de sismicidad de Colombia | Sismo | Nacional | [Ver](https://scr-ungrd.github.io/cuadernos-reproducibles-crc004/) | [crc004](https://github.com/scr-ungrd/cuadernos-reproducibles-crc004) |
| CRC-005 | Detección de inundaciones con Sentinel-1 y Google Earth Engine | Inundación | Caribe colombiano y cuenca del Magdalena | [Ver](https://scr-ungrd.github.io/cuadernos-reproducibles-crc005/) | [crc005](https://github.com/scr-ungrd/cuadernos-reproducibles-crc005) |
| CRC-006 | Escenarios de riesgo ante el fenómeno El Niño 2026–2027 | Fenómeno El Niño | Nacional | [Ver](https://scr-ungrd.github.io/cuadernos-reproducibles-crc006/) | [crc006](https://github.com/scr-ungrd/cuadernos-reproducibles-crc006) |

CRC-001 tiene DOI en Zenodo: [10.5281/zenodo.20061610](https://doi.org/10.5281/zenodo.20061610).

## Ejecución interactiva

Los cuadernos se ejecutan en la nube sin instalar nada. Cada sitio incluye sus botones de Binder y de Google Colab; también puedes abrir el repositorio del cuaderno en Binder con:

```text
https://mybinder.org/v2/gh/scr-ungrd/cuadernos-reproducibles-crc00X/HEAD
```

(sustituye `X` por el número del cuaderno).

## Qué hay en este repositorio

| Ruta | Contenido |
|------|-----------|
| `index.md` | Portada: hero con imagen satelital y lista de cuadernos |
| `01-cuadernos-de-conocimiento.md` | Guía para publicar un cuaderno |
| `02-convocatoria-cuadernos.md` | Convocatoria abierta de cuadernos |
| `footer.md` | Pie de página con logos y aviso de la Subdirección |
| `css/footer.css` | Estilos de la portada (modo día/noche, tarjetas, pie) |
| `images/` | Imágenes de la portada, logos y favicon |
| `myst.yml` | Configuración del sitio MyST |
| `binder/requirements.txt` | Dependencias de Python para Binder |

## Agregar un cuaderno a la portada

1. Publica el cuaderno en su propio repositorio (`cuadernos-reproducibles-crcNNN`) con su sitio en GitHub Pages.
2. Agrega una tarjeta `{card}` en `index.md`, ordenada por fecha de la más reciente a la más antigua, con imagen, título, resumen, autores y fecha.
3. Guarda la imagen de la tarjeta en `images/`.
4. Actualiza la tabla de este README.

## Desarrollo local

```bash
# Instalar MyST CLI
npm install -g mystmd

# Vista previa con recarga automática
myst start

# O construir el sitio HTML estático
myst build --html
```

El sitio se despliega con GitHub Actions al hacer push a `main`
(`.github/workflows`, «Deploy MyST Site to GitHub Pages»).

## Créditos de la imagen de portada

Barranquilla y el río Magdalena, imagen Sentinel-2 del 31 de marzo de 2024.
Contiene datos modificados de Copernicus Sentinel (2024), Unión Europea.
Fuente: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Barranquilla,_the_%E2%80%98Golden_Gate%E2%80%99_of_Colombia_(Copernicus_2024-12-27).png).

Los íconos de Jupyter, Markdown, Colab, GitHub, Python, R, Zenodo y Creative Commons provienen de [Simple Icons](https://simpleicons.org) (CC0). Sus nombres y logotipos son marcas de sus respectivos titulares.

## Licencia

- Contenido narrativo: [CC-BY-SA-4.0](LICENSE)
- Código fuente: MIT

---

© 2026 Subdirección para el Conocimiento del Riesgo - UNGRD. Todos los derechos reservados.
