# Datos del cuaderno 05 — Escenarios El Niño 2026-2027

Este directorio contiene los archivos de datos necesarios para ejecutar el cuaderno
`05-visor-nino-2026-2027.ipynb`.

## Archivos requeridos

| Archivo | Descripción | Fuente |
|---------|-------------|--------|
| `datos_base_analisis.parquet` | Registros de emergencias UNGRD 2023-2024 | SCR / UNGRD |
| `colombia_departamentos.json` | GeoJSON de departamentos de Colombia (DIVIPOLA) | DANE / IGAC |
| `colombia_municipios.json` | GeoJSON de municipios de Colombia (DIVIPOLA) | DANE / IGAC |

## Instrucciones de descarga

Los archivos de datos están disponibles en el repositorio interno de la UNGRD.
Solicítelos a la Subdirección para el Conocimiento del Riesgo (SCR) o descárguelos
desde el repositorio de insumos del proyecto Plataforma Riesgos.

Una vez descargados, ubíquelos en esta carpeta (`data/`) antes de ejecutar el cuaderno.

## Verificación

Tras ubicar los archivos, puede verificar su integridad ejecutando la celda de
**Carga y preprocesamiento de datos** del cuaderno, que imprimirá el número de
registros cargados y el rango de fechas del periodo de análisis.
