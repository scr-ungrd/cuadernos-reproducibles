# Datos del cuaderno 05 — Escenarios El Niño 2026-2027

Este directorio contiene los archivos de datos necesarios para ejecutar el cuaderno
`05-visor-nino-2026-2027.ipynb`, tanto localmente como en Binder.

## Archivos incluidos

| Archivo | Tamaño | Descripción | Fuente |
| ------- | ------ | ----------- | ------ |
| `datos_base_analisis.parquet` | 0.24 MB | Registros de emergencias UNGRD 2023-2024 con variables de impacto, tipo de evento, clasificación climática y codificación DIVIPOLA | SCR / UNGRD |
| `colombia_departamentos.json` | 0.41 MB | GeoJSON de departamentos de Colombia (DIVIPOLA) | DANE / IGAC |
| `colombia_municipios.json` | 2.91 MB | GeoJSON de municipios de Colombia (DIVIPOLA) | DANE / IGAC |

Los tres archivos están versionados en el repositorio. Al clonar el repositorio o
lanzarlo en Binder, estarán disponibles automáticamente en esta carpeta.

## Ejecutar en Binder (sin instalación local)

Haz clic en el badge del `README.md` o en el enlace del frontmatter del cuaderno.
Binder construirá el entorno desde `requirements.txt` y abrirá el cuaderno
directamente en JupyterLab en la nube.

## Ejecutar localmente

```bash
git clone https://github.com/scr-ungrd/cuadernos-reproducibles.git
cd cuadernos-reproducibles
pip install -r requirements.txt
jupyter lab 05-visor-nino-2026-2027.ipynb
```
