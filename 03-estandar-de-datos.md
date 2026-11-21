---
title: Requisitos para datos
subtitle: Instrucciones para autores de cuadernos reproducibles
date: 2026-11-16
authors:
  - name: Subdirección para el Conocimiento del Riesgo
    affiliation: Unidad Nacional para la Gestión del Riesgo de Desastres (UNGRD)
    github: scr-ungrd
license: CC-BY-4.0
keywords:
  - requisitos para datos
  - metadatos
  - FAIR
  - CARE
  - RDLS
  - datos abiertos
  - riesgo de desastres
abbreviations:
  RDLS: Risk Data Library Standard
  GFDRR: Global Facility for Disaster Reduction and Recovery
  FAIR: Findable, Accessible, Interoperable, Reusable
  CARE: Collective benefit, Authority to control, Responsibility, Ethics
  DOI: Digital Object Identifier
  ORCID: Open Researcher and Contributor ID
  CRED: Centre for Research on the Epidemiology of Disasters
---

+++ {"part": "abstract"}

Este documento establece los requisitos que deben cumplir los datos y los metadatos de un cuaderno para publicarse en la colección. Define 92 requisitos (80 obligatorios y 12 recomendados), cada uno con un identificador, un nivel y una fuente citada. Se derivan principalmente del Risk Data Library Standard (RDLS) y los principios FAIR y CARE, entre otros. Ningún requisito exige suscripciónes o pagos de ningún tipo. Se incluye una lista de verificación y un prompt de auditoría que puede emplear en una herramienta de IA.

+++

## 1. Alcance y convenciones

### 1.1 Alcance

Estas instrucciones se aplican a todo cuaderno que se publique en la colección y a tres tipos de objetos:

- **Insumos**: datos de entrada que el cuaderno lee o descarga.
- **Datos derivados**: datos que el cuaderno produce y publica.
- **Metadatos**: la descripción de insumos y datos derivados.

Complementan la [guía para publicar un cuaderno](01-cuadernos-de-conocimiento.md), que exige que los datos cumplan los principios FAIR y se alineen con el RDLS.

### 1.2 Convenciones

1. **Identificador.** Cada requisito tiene un código de tres letras y dos cifras (por ejemplo, MET-03 o metadatos). Los códigos se usan en la lista de verificación, en el prompt de validación y en los reportes.
2. **Nivel.** *Obligatorio* significa que el cuaderno no se acepta si el requisito aplica y no se cumple. *Recomendado* significa que el cumplimiento mejora la calidad pero no condiciona la aceptación. *Crítico* es un requisito obligatorio cuyo incumplimiento bloquea la publicación, cualquiera sea la puntuación total.
3. **Base.** La columna «Base» indica el documento, el año y, cuando corresponde, el apartado del que procede el requisito. Los requisitos cuya base es «Requisito de esta guía» los establece este documento y no provienen de una fuente externa.
4. **Redacción.** Cada requisito se enuncia en el estado conforme: describe cómo es un cuaderno que lo cumple.
5. **Citas y traducciones.** Las citas siguen la norma APA 7. Los textos de las fuentes en inglés se traducen al español; las traducciones son propias. Los nombres de campos, códigos y apartados de las fuentes se conservan en su idioma original.
6. **Fecha de consulta.** Las fuentes web sin fecha de publicación se consultaron el 16 de noviembre de 2026 (véanse las Referencias).

### 1.3 Política de costo cero

Ningún requisito de este documento exige comprar suscripciones, licencias ni servicios. La política se aplica así:

1. **Insumos sin pago.** El Portal Nacional de Datos Abiertos declara que no es necesario adquirir licencias de software ni hacer pagos para acceder, reutilizar o descargar sus datos (MinTIC, 2026c, sección 7). Un insumo que exija pago para el uso que hace el cuaderno no se admite (INV-04). Por ejemplo, el uso comercial de EM-DAT requiere una suscripción anual de 10 000 euros (Université catholique de Louvain [UCLouvain], 2026, art. 6.2), de modo que un uso comercial no cumple INV-04 (véase EMD-01).
2. **Descarga sin pago.** Los datos publicados por el cuaderno se descargan sin pago (DEP-05).
3. **Herramientas libres.** Las herramientas de verificación que se nombran son software libre (Tabla 1).
4. **Fuentes abiertas.** Todos los documentos de referencia estaban disponibles en línea sin suscripción en la fecha de consulta.
5. **Sin normas de pago.** Las fechas se definen con la RFC 3339 y los países con la lista `country` del RDLS, ambas de acceso libre, de modo que el cumplimiento no depende de adquirir ninguna norma.

**Tabla 1.** Herramientas de verificación citadas en este documento.

```{list-table}
:header-rows: 1

* - Herramienta
  - Uso en este documento
  - Licencia según el Python Package Index
* - `check-jsonschema` 0.39.0 (Rosen, 2026)
  - Validar los archivos RDLS contra el esquema (MET-03)
  - Apache Software License
* - `pandera` 0.36.0 (Bantilan, 2026)
  - Escribir pruebas automáticas de datos tabulares (VAL-06)
  - MIT
```

### 1.4 Documentos de referencia

**Tabla 2.** Documentos de los que se derivan los requisitos.

```{list-table}
:header-rows: 1

* - Documento
  - Qué establece
  - Requisitos que se derivan
* - Global Facility for Disaster Reduction and Recovery [GFDRR] (2026). *Risk Data Library Standard*, versión 1.0.0
  - Estándar abierto de metadatos para describir conjuntos de datos de amenaza, exposición, vulnerabilidad y pérdidas, con un esquema JSON y listas de códigos
  - MET, EST-05, EST-06
* - Wilkinson et al. (2016). Principios FAIR
  - Quince principios para que los datos sean localizables, accesibles, interoperables y reutilizables
  - Tabla 7; DEP, MET, LIC
* - Carroll et al. (2020). Principios CARE
  - Cuatro principios para la gobernanza de datos de pueblos indígenas
  - PER-01, PER-02
* - Coalition for Publishing Data in the Earth and Space Sciences [COPDESS] (s. f.). *Commitment statement*
  - Compromisos para repositorios, editoriales, financiadores y autores sobre identificadores, citación y declaración de disponibilidad de datos
  - DEP-03, DEP-06, DEP-07, DEP-09
* - Crowley (2014). *Open Data for Resilience Initiative: Field guide*, Banco Mundial
  - Definición de dato abierto en lo legal y en lo técnico, y guía de licenciamiento y metadatos
  - INV-05, EST-02, EST-03, LIC-05
* - Scientific Data (s. f.-a, s. f.-b, s. f.-c). Políticas de datos, de repositorios y guía de envío
  - Requisitos que una revista de datos aplica a repositorios, licencias, datos humanos, citación, validación y preservación
  - INV, PER, LIC, DEP, VAL, PRE
* - Guha-Sapir et al. (2026). Artículo sobre el conjunto MERGE
  - Descripción publicada de un conjunto de datos de riesgo (MERGE) con sus insumos, limitaciones y declaraciones
  - EST-07, DEP-04, VAL-02, VAL-03
* - Centre for Research on the Epidemiology of Disasters [CRED] (2026); UCLouvain (2025, 2026). Documentación y textos legales de EM-DAT
  - Condiciones de uso, citación, criterios de entrada y sesgos de un insumo de uso frecuente
  - INV-06, VAL-04, EMD
* - Klyne y Newman (2002); Shafranovich (2005); Butler et al. (2016). RFC 3339, RFC 4180 y RFC 7946
  - Formato de fechas, de archivos CSV y de archivos GeoJSON
  - EST-02, EST-06
* - Congreso de la República de Colombia (2014). Ley 1712 de 2014
  - Define los datos abiertos y exceptúa la información pública clasificada y reservada
  - GOV-08
* - MinTIC (2024). Guía para el uso y aprovechamiento de Datos Abiertos en Colombia, versión 7; MinTIC (2026a, 2026b, 2026c). Listado de errores, catálogo e historia del portal
  - Formatos, licencia, metadatos, criterios de calidad y procedimientos del Portal Nacional de Datos Abiertos
  - EST-02, LIC-02, CAL, GOV
* - Socrata (s. f.-a, s. f.-b). Documentación de la API
  - Uso de tokens y límite de filas por solicitud
  - GOV-06
* - UNDRR e ISC (2025). Hazard Information Profiles, versión 2025; Naciones Unidas (2015). Marco de Sendai
  - Taxonomía de amenazas con códigos comunes e indicadores de daños y pérdidas
  - EST-11, EST-12
* - Departamento Administrativo Nacional de Estadística [DANE] (2025); Unidad Nacional para la Gestión del Riesgo de Desastres [UNGRD] (2026). Conjuntos del portal
  - Códigos DIVIPOLA y reportes anuales de emergencias
  - EST-09
* - Zenodo (s. f.). Políticas generales
  - Condiciones del repositorio de depósito de la colección
  - DEP-01
```

## 2. Requisitos

### 2.1 Inventario y selección de insumos

Todo insumo se registra antes de usarse. El registro permite a otra persona obtener exactamente los mismos datos (Scientific Data, s. f.-c).

```{list-table}
:header-rows: 1

* - ID
  - Nivel
  - Requisito
  - Base
* - **INV-01**
  - Obligatorio
  - Cada insumo (dato de entrada) figura en `metadata/sources.csv` con las columnas de la Tabla 3.
  - Scientific Data (s. f.-c), apartado Methods
* - **INV-02**
  - Obligatorio
  - La URL o el DOI de cada insumo apunta al archivo o al registro exacto, no a la página de inicio de la fuente.
  - Scientific Data (s. f.-c)
* - **INV-03**
  - Obligatorio
  - Si el insumo se actualiza de forma continua, `sources.csv` registra la versión o, en su defecto, los parámetros de la consulta (incluido cualquier filtro territorial o temporal) y la fecha de descarga.
  - Scientific Data (s. f.-c)
* - **INV-04**
  - Obligatorio (crítico)
  - Todo insumo puede obtenerse sin pago: ninguno exige suscripción ni licencia de pago para el uso que hace el cuaderno.
  - Requisito de esta guía (Sección 1.3)
* - **INV-05**
  - Obligatorio (crítico)
  - Los datos de terceros se copian al repositorio solo si su licencia o sus términos de uso permiten redistribuirlos; en caso contrario, el repositorio contiene el script de descarga y la cita.
  - Crowley (2014); UCLouvain (2026), art. 3.4; Scientific Data (s. f.-a)
* - **INV-06**
  - Obligatorio (crítico)
  - Los términos de uso de cada insumo se leyeron completos y sus restricciones (redistribución, combinación con otras bases de datos, cita exigida) están registradas en `sources.csv`.
  - UCLouvain (2026), arts. 3.2, 3.4 y 9.3
* - **INV-07**
  - Obligatorio
  - Si el insumo es una compilación de fuentes, cada registro lleva su fuente (DOI, URL o equivalente) y ningún registro se marca como «sin publicar» sin fuente.
  - Scientific Data (s. f.-a)
* - **INV-08**
  - Recomendado
  - Cuando el insumo tiene una versión archivada y citable, se usa esa versión y no la versión viva.
  - CRED (2026), sección 2
```

**Tabla 3.** Columnas de `metadata/sources.csv`. Cada fila corresponde a un insumo.

```{list-table}
:header-rows: 1

* - Columna
  - Contenido
* - `nombre`
  - Nombre del conjunto de datos de origen
* - `entidad`
  - Entidad que lo produce
* - `identificador_fuente`
  - Identificador del conjunto en la fuente (por ejemplo, `2343-nuqp` en datos.gov.co); vacío si la fuente no lo tiene
* - `url_o_doi`
  - Dirección del archivo o del registro exacto; no la página de inicio de la fuente
* - `version_o_consulta`
  - Versión; si el servicio se actualiza continuamente, parámetros de la consulta
* - `metodo_extraccion`
  - Descarga directa, API, SFTP u otro
* - `formato`
  - GeoTIFF, CSV, NetCDF u otro
* - `resolucion_espacial`
  - Por ejemplo, `100 m` o `país`
* - `resolucion_temporal`
  - Por ejemplo, `anual` o `evento`
* - `variables`
  - Variables que usa el cuaderno
* - `fecha_actualizacion_fuente`
  - Fecha de la última actualización de los datos declarada por la fuente, en formato AAAA-MM-DD
* - `fecha_descarga`
  - Fecha en formato AAAA-MM-DD
* - `licencia`
  - Identificador SPDX o URL de la licencia
* - `restricciones_de_uso`
  - Restricciones de redistribución, de combinación con otras bases y de cita
```

### 2.2 Estructura de archivos y formatos

```{list-table}
:header-rows: 1

* - ID
  - Nivel
  - Requisito
  - Base
* - **EST-01**
  - Obligatorio
  - Los datos están en `data/raw`, `data/interim` y `data/processed`; `raw` contiene los originales sin modificar o el script que los descarga.
  - Requisito de esta guía; nivel de procesamiento según Scientific Data (s. f.-a)
* - **EST-02**
  - Obligatorio
  - Los datos publicados tienen formatos abiertos, no propietarios y procesables por máquina (Tabla 4). Los insumos pueden conservar el formato de la fuente.
  - Crowley (2014); MinTIC (2024), sección 5.3.2
* - **EST-03**
  - Obligatorio
  - Los datos se entregan completos y en bloque, no solo como visualización.
  - Crowley (2014), definición de dato técnicamente abierto
* - **EST-04**
  - Obligatorio
  - Cada tabla tiene un diccionario de variables con nombre, descripción, tipo, unidad y valores permitidos.
  - Wilkinson et al. (2016), R1; Scientific Data (s. f.-c), apartado Data Record; MinTIC (2026a), ERR008_3
* - **EST-05**
  - Obligatorio
  - Cada recurso declara el sistema de coordenadas (código EPSG), la resolución espacial y la resolución temporal.
  - GFDRR (2026), campos de recurso
* - **EST-06**
  - Obligatorio
  - Las fechas tienen el formato AAAA-MM-DD y los países se identifican con los códigos ISO 3166-1 alfa-3 de la lista `country` del RDLS.
  - Klyne y Newman (2002), sección 5.6; GFDRR (2026), listas de códigos
* - **EST-07**
  - Obligatorio
  - `metadata/data_catalog.csv` lista cada archivo publicado con su descripción, formato, tamaño y licencia.
  - Requisito de esta guía; Guha-Sapir et al. (2026), apartado Data Records
* - **EST-08**
  - Recomendado
  - Los nombres de archivo no tienen espacios ni tildes.
  - Requisito de esta guía
* - **EST-09**
  - Obligatorio
  - Los departamentos y municipios se identifican con el código DIVIPOLA del DANE, almacenado como texto con ceros a la izquierda: dos caracteres para departamentos (por ejemplo, `05`) y cinco para municipios (por ejemplo, `05001`).
  - DANE (2025); UNGRD (2026)
* - **EST-10**
  - Obligatorio
  - Los valores numéricos usan el punto como separador decimal y no incluyen separador de miles ni texto.
  - Requisito de esta guía; MinTIC (2026a), ERR019
* - **EST-11**
  - Obligatorio
  - Si el conjunto clasifica amenazas o eventos, usa los códigos de los Hazard Information Profiles (HIPs) 2025 de UNDRR y el ISC, y `sources.csv` o el diccionario registra la equivalencia con la clasificación de la fuente (por ejemplo, EM-DAT, DesInventar o UNGRD). Aplica solo si el conjunto clasifica amenazas.
  - UNDRR e ISC (2025)
* - **EST-12**
  - Recomendado
  - Los indicadores de daños y pérdidas se definen y se nombran según los indicadores del Marco de Sendai cuando existe uno equivalente, y el diccionario de variables indica cuál.
  - Naciones Unidas (2015)
```

**Vocabularios controlados.** Un código común permite comparar el conjunto con las bases internacionales. La actualización de 2025 de los HIPs agrupa 281 amenazas en 8 tipos y 39 clústeres (UNDRR e ISC, 2025). Cuando una fuente usa su propia clasificación, no la reemplace: conserve la clase original y agregue una columna con el código HIPs.

Estructura de carpetas del repositorio:

```text
cuaderno/
├── data/
│   ├── raw/          # Originales sin modificar, o el script que los descarga
│   ├── interim/      # Resultados intermedios regenerables
│   └── processed/    # Datos derivados que se publican
├── metadata/
│   ├── rdls/         # Un archivo JSON por conjunto de datos
│   ├── data_catalog.csv
│   ├── DATA_DICTIONARY.md
│   └── sources.csv
├── scripts/          # Descarga, procesamiento y pruebas
├── CHANGELOG.md
├── CITATION.cff
├── DATA_STATEMENT.md
├── LICENSE
└── environment.yml
```

**Tabla 4.** Formatos admitidos.

```{list-table}
:header-rows: 1

* - Formato
  - Uso
  - Base
* - CSV, codificación UTF-8
  - Datos tabulares
  - Shafranovich (2005)
* - GeoJSON
  - Vectores de tamaño pequeño o medio
  - Butler et al. (2016)
* - GeoPackage (`.gpkg`)
  - Vectores
  - Requisito de esta guía
* - GeoTIFF o GeoTIFF optimizado para la nube (`.tif`)
  - Rásteres
  - Requisito de esta guía
* - NetCDF o Zarr
  - Series multidimensionales
  - Requisito de esta guía
* - JSON
  - Metadatos RDLS
  - GFDRR (2026)
* - Shapefile (`.shp`), KML, servicios WMS y WFS
  - Se aceptan como formato de un insumo; para los datos publicados se entrega además GeoPackage o GeoJSON
  - MinTIC (2024, sección 5.3.2)
* - `.xlsx`
  - El portal lo admite como formato abierto estructurado (MinTIC, 2026c, sección 6); estos requisitos exigen además una copia en CSV
  - Requisito de esta guía
* - PDF, Word e imágenes
  - No se aceptan como formato de datos
  - MinTIC (2026a, ERR010)
```

### 2.3 Metadatos con el Risk Data Library Standard

El RDLS es un estándar abierto de metadatos para describir conjuntos de datos de riesgo usados en evaluaciones de riesgo climático y de desastres. Describe los datos; no estandariza su contenido (GFDRR, 2026). Este documento usa la versión 1.0.0.

```{list-table}
:header-rows: 1

* - ID
  - Nivel
  - Requisito
  - Base
* - **MET-01**
  - Obligatorio
  - Existe un archivo `metadata/rdls/<nombre>.json` por cada conjunto de datos publicado.
  - GFDRR (2026)
* - **MET-02**
  - Obligatorio
  - Cada archivo incluye los diez campos obligatorios del esquema (Tabla 5).
  - GFDRR (2026)
* - **MET-03**
  - Obligatorio (crítico)
  - Cada archivo valida sin errores contra el esquema canónico del RDLS 1.0.0.
  - GFDRR (2026)
* - **MET-04**
  - Obligatorio
  - Los campos con lista de códigos usan los códigos del RDLS sin traducirlos (por ejemplo, `license` usa la URL de la lista de licencias). Si no existe un código adecuado y la lista es cerrada, se abrió un *issue* en el repositorio del RDLS; si la lista es abierta, se usa un código nuevo y se propone en un *issue*.
  - GFDRR (2026), listas de códigos
* - **MET-05**
  - Obligatorio
  - El campo `id` contiene el DOI del conjunto de datos como URL (`https://doi.org/...`).
  - Wilkinson et al. (2016), F1 y F3; GFDRR (2026), campo `id`
* - **MET-06**
  - Obligatorio
  - El campo `lineage` describe la procedencia: insumos (en `lineage.sources`), transformaciones y software.
  - Wilkinson et al. (2016), R1.2; GFDRR (2026)
* - **MET-07**
  - Obligatorio
  - Por cada valor de `risk_data_type` existe el componente correspondiente (`hazard`, `exposure`, `vulnerability` o `loss`).
  - GFDRR (2026)
* - **MET-08**
  - Recomendado
  - Se completan los campos opcionales `temporal`, `spatial_resolution`, `temporal_resolution`, `attributions`, `referenced_by` y `version`.
  - Requisito de esta guía; campos definidos en GFDRR (2026)
```

**Tabla 5.** Campos obligatorios del esquema RDLS 1.0.0 (GFDRR, 2026).

```{list-table}
:header-rows: 1

* - Campo
  - Contenido
  - Observación
* - `id`
  - Identificador único del conjunto
  - Se recomienda un URI HTTP; en estos requisitos, el DOI como URL (MET-05)
* - `title`
  - Título
  - Incluye tema, lugar y año
* - `description`
  - Descripción
  - Qué contiene y qué no cubre
* - `risk_data_type`
  - Lista de tipos de dato de riesgo
  - Valores: `hazard`, `exposure`, `vulnerability`, `loss`
* - `publisher`
  - Entidad que pone el conjunto a disposición
  - `name` y, si aplica, `url`
* - `contact_point`
  - Mantenedor del conjunto
  - `name` y `email` o `url`
* - `creator`
  - Entidad que produjo el conjunto
  - `name` y `email` o `url`
* - `spatial`
  - Cobertura geográfica
  - `scale` (`global`, `regional`, `national`, `sub-national` o `urban`), `countries` y, de preferencia, `bbox`
* - `license`
  - Licencia
  - Identificador o URL
* - `resources`
  - Archivos concretos
  - Cada uno con `id`, `title` y `description`
```

**Tabla 6.** Componente específico según el tipo de dato (GFDRR, 2026).

```{list-table}
:header-rows: 1

* - `risk_data_type`
  - Qué describe el componente
* - `hazard`
  - Tipo de amenaza, medida de intensidad y conjuntos de eventos
* - `exposure`
  - Categoría de exposición (`agriculture`, `buildings`, `infrastructure`, `population`, `natural_environment`, `economic_indicator`, `development_index`) y métricas
* - `vulnerability`
  - Relación entre intensidad y daño, y enfoque con que se construyó (`analytical`, `empirical`, `hybrid` o `judgement`)
* - `loss`
  - Estimaciones modeladas, con vínculos a los datos de amenaza, exposición y vulnerabilidad usados
```

**Ejemplo.** El siguiente archivo describe una capa de exposición y valida contra el esquema JSON del RDLS 1.0.0. El DOI y el correo son marcadores de posición que deben reemplazarse por los reales.

```json
{
  "id": "https://doi.org/10.5281/zenodo.0000000",
  "title": "Población expuesta a olas de calor en Montería, 2020",
  "description": "Población por celda de 100 m en el área urbana de Montería (Córdoba), usada como capa de exposición del cuaderno CRC-001.",
  "risk_data_type": ["exposure"],
  "publisher": {
    "name": "Subdirección para el Conocimiento del Riesgo, UNGRD",
    "url": "https://scr-ungrd.github.io/cuadernos-reproducibles/"
  },
  "contact_point": {
    "name": "Subdirección para el Conocimiento del Riesgo",
    "email": "contacto@example.org"
  },
  "creator": {
    "name": "Subdirección para el Conocimiento del Riesgo, UNGRD",
    "url": "https://github.com/scr-ungrd"
  },
  "spatial": {
    "scale": "urban",
    "countries": ["COL"],
    "gazetteer_entries": [
      { "id": "23001", "scheme": "DIVIPOLA", "description": "Montería, Córdoba" }
    ]
  },
  "temporal": { "start": "2020-01-01", "end": "2020-12-31" },
  "license": "https://creativecommons.org/licenses/by/4.0/",
  "resources": [
    {
      "id": "poblacion-100m",
      "title": "Población por celda de 100 m",
      "description": "Ráster GeoTIFF de población estimada por celda.",
      "download_url": "https://zenodo.org/records/0000000/files/poblacion_monteria_100m.tif",
      "media_type": "image/tiff",
      "format": "GeoTIFF"
    }
  ],
  "exposure": [
    {
      "id": "poblacion",
      "category": "population",
      "metrics": [
        {
          "id": "personas",
          "dimension": "population",
          "measurement": { "quantity_kind": "count", "unit": "count" }
        }
      ]
    }
  ],
  "lineage": {
    "description": "Derivado de WorldPop 2020 (1 km desagregado a 100 m), recortado al perímetro urbano de Montería."
  }
}
```

**Procedimiento de validación** (requisito MET-03). El esquema canónico de la versión 1.0.0 está en `https://docs.riskdatalibrary.org/en/1__0__0/rdls_schema.json` (GFDRR, 2026). Se debe usar siempre esta dirección con versión.

```bash
pip install check-jsonschema
check-jsonschema --schemafile https://docs.riskdatalibrary.org/en/1__0__0/rdls_schema.json metadata/rdls/*.json
```

El comando verifica la estructura del archivo. No verifica que su contenido sea cierto: esa responsabilidad corresponde a quien publica.

### 2.4 Principios FAIR

Los principios FAIR son 15 enunciados sobre cómo deben ser los datos y sus metadatos (Wilkinson et al., 2016). La Tabla 7 los enlaza con los requisitos de este documento que los implementan. Un cuaderno que cumple todos los requisitos de la columna derecha cumple el principio correspondiente.

**Tabla 7.** Principios FAIR (Wilkinson et al., 2016; traducción propia) y requisitos que los implementan.

```{list-table}
:header-rows: 1

* - Principio
  - Enunciado
  - Requisitos
* - **F1**
  - Los (meta)datos tienen un identificador único y persistente a nivel global
  - DEP-03, MET-05
* - **F2**
  - Los datos se describen con metadatos ricos
  - MET-01, MET-02, MET-06, EST-04
* - **F3**
  - Los metadatos incluyen de forma clara y explícita el identificador de los datos que describen
  - MET-05
* - **F4**
  - Los (meta)datos se registran o indexan en un recurso donde se puede buscar
  - DEP-01, DEP-03
* - **A1**
  - Los (meta)datos se recuperan por su identificador con un protocolo de comunicación estandarizado
  - DEP-01, DEP-05
* - **A1.1**
  - El protocolo es abierto, gratuito y de implementación universal
  - DEP-05
* - **A1.2**
  - El protocolo permite un procedimiento de autenticación y autorización cuando sea necesario
  - PER-03, PER-05
* - **A2**
  - Los metadatos son accesibles aunque los datos ya no estén disponibles
  - PER-05, DEP-01
* - **I1**
  - Los (meta)datos usan un lenguaje formal, accesible, compartido y de amplia aplicación para representar el conocimiento
  - EST-02, MET-01
* - **I2**
  - Los (meta)datos usan vocabularios que siguen los principios FAIR
  - MET-04, EST-05, EST-06
* - **I3**
  - Los (meta)datos incluyen referencias calificadas a otros (meta)datos
  - MET-06, MET-07, INV-01
* - **R1**
  - Los (meta)datos se describen con una pluralidad de atributos precisos y relevantes
  - EST-04, MET-02, MET-08
* - **R1.1**
  - Los (meta)datos se publican con una licencia de uso clara y accesible
  - LIC-01, LIC-02
* - **R1.2**
  - Los (meta)datos se asocian con una procedencia detallada
  - MET-06, INV-01, VAL-01
* - **R1.3**
  - Los (meta)datos cumplen los estándares de la comunidad del dominio
  - MET-01, MET-03
```

La Fundación GO FAIR publica una ontología legible por máquina con un término por principio (GO FAIR Foundation, s. f.): `https://w3id.org/fair/principles`.

### 2.5 Datos sobre personas y comunidades

Los principios FAIR describen características de los datos. Los principios CARE complementan ese enfoque con la perspectiva de las personas y el propósito: reconocen que compartir más datos puede entrar en tensión con el derecho de los pueblos indígenas a controlar sus datos y sus conocimientos (Global Indigenous Data Alliance [GIDA], s. f.). Los cuatro principios son los de Carroll et al. (2020).

**Tabla 8.** Principios CARE (Carroll et al., 2020; traducción propia) y pregunta de control de esta guía.

```{list-table}
:header-rows: 1

* - Principio
  - Enunciado
  - Pregunta de control (requisito de esta guía)
* - **Beneficio colectivo** (*Collective benefit*)
  - Los datos indígenas deben facilitar un beneficio colectivo para los pueblos indígenas, para lograr un desarrollo y una innovación inclusivos
  - ¿Los resultados regresan a las comunidades de las que provienen los datos, en un formato que puedan usar?
* - **Autoridad para controlar** (*Authority to control*)
  - Los pueblos indígenas deben ser quienes determinen los protocolos de gobernanza de los datos
  - ¿Las autoridades de los territorios étnicos conocen el uso del dato y lo autorizaron?
* - **Responsabilidad** (*Responsibility*)
  - Al trabajar con datos indígenas existe la responsabilidad de cultivar relaciones respetuosas
  - ¿Quedó documentado cómo se relacionó el equipo con la comunidad y cómo se corregirán los daños?
* - **Ética** (*Ethics*)
  - Es primordial para la ética en las prácticas de datos la representación y la participación de los pueblos indígenas
  - ¿Se evaluó qué daños puede causar publicar el dato, incluso combinado con otros?
```

**Cuándo se aplica la prueba CARE.** Se aplica cuando los datos (a) se refieren a territorios, resguardos, consejos comunitarios o comunidades étnicas; (b) recogen conocimiento local o tradicional sobre amenazas; o (c) identifican personas o viviendas concretas. Este criterio es un requisito de esta guía.

```{list-table}
:header-rows: 1

* - ID
  - Nivel
  - Requisito
  - Base
* - **PER-01**
  - Obligatorio
  - Se aplicó la prueba de la Tabla 8 (principios CARE) y su resultado está registrado en `DATA_STATEMENT.md`.
  - Carroll et al. (2020); GIDA (s. f.)
* - **PER-02**
  - Obligatorio (crítico)
  - No se publican datos personales ni datos de pueblos o comunidades sin una constancia de autorización registrada en `DATA_STATEMENT.md`.
  - Carroll et al. (2020); Scientific Data (s. f.-a), apartado Human Data; MinTIC (2026a), ERR018
* - **PER-03**
  - Obligatorio
  - Los datos sobre personas siguen una de las dos rutas de la Tabla 9: abierta o de acceso controlado.
  - Scientific Data (s. f.-a), apartado Human Data
* - **PER-04**
  - Obligatorio
  - Antes de publicar se evaluó el riesgo de reidentificación por identificadores indirectos (ubicación, género, ocupación, características de salud).
  - Scientific Data (s. f.-a), apartado Human Data
* - **PER-05**
  - Obligatorio
  - Cuando el acceso es restringido, los metadatos son públicos y se indica cómo solicitar el acceso.
  - Wilkinson et al. (2016), A1.2 y A2
* - **PER-06**
  - Obligatorio
  - Los datos de redes sociales no se indexan ni se republican sin consentimiento.
  - Scientific Data (s. f.-a), apartado Data compilations
* - **PER-07**
  - Recomendado
  - La resolución espacial se agrega o se reduce hasta que el dato no permita identificar personas o viviendas, y la transformación se documenta en `lineage`.
  - Requisito de esta guía
```

**Tabla 9.** Rutas de publicación de datos sobre personas (Scientific Data, s. f.-a, apartado Human Data; traducción propia).

```{list-table}
:header-rows: 1

* - Ruta
  - Cuándo aplica
  - Cómo se publica
* - **Datos abiertos**
  - Los datos están totalmente anonimizados o tienen un riesgo de reidentificación extremadamente bajo, y no contienen campos sensibles
  - Descarga sin controles y licencia CC BY o CC0, o equivalente
* - **Acceso controlado**
  - Los datos no están totalmente anonimizados o su divulgación puede causar daño a las personas
  - Todos los usuarios se registran y se valida su identidad; cada uno firma un acuerdo de uso de datos que fija las condiciones
```

Reglas adicionales de la misma política (Scientific Data, s. f.-a, apartado Human Data):

1. Los datos primarios sobre personas requieren consentimiento o una dispensa de un comité de ética, y la aprobación de un comité de ética para realizar el estudio y compartir los datos. Las dispensas no se admiten para menores ni para adultos vulnerables.
2. En los datos secundarios, la responsabilidad de la gestión es del tercero que los publicó. Se debe verificar, ante todo, que exista el derecho de redistribuirlos, en especial si están bajo un acuerdo de uso con cláusula de no redistribución.
3. Los acuerdos de uso razonables establecen que quien accede no intenta reidentificar a las personas, no redistribuye los datos a terceros no firmantes, los usa solo para investigación interna y los custodia de forma segura.

### 2.6 Licencias

Un dato es abierto cuando cualquier persona es libre de usarlo, reutilizarlo y redistribuirlo, sujeto, como máximo, a atribución o a compartir igual. Para ello debe ser legalmente abierto, con una licencia que permita la redistribución y la reutilización, y técnicamente abierto, disponible en bloque y en un formato procesable por máquina (Crowley, 2014).

```{list-table}
:header-rows: 1

* - ID
  - Nivel
  - Requisito
  - Base
* - **LIC-01**
  - Obligatorio (crítico)
  - Existen un archivo `LICENSE` y un campo `license` del RDLS con una licencia explícita.
  - Wilkinson et al. (2016), R1.1; GFDRR (2026)
* - **LIC-02**
  - Obligatorio (crítico)
  - Los datos publicados usan CC0 o CC BY (o equivalentes) y no tienen cláusulas `-SA` ni `-NC`, salvo que sean datos secundarios que deban conservar las condiciones de la fuente (por ejemplo, CC BY-SA 4.0 cuando el insumo tiene esa licencia).
  - Scientific Data (s. f.-b); MinTIC (2024), sección 2.2
* - **LIC-03**
  - Obligatorio
  - No se publica como conjunto nuevo ningún dato derivado de una fuente con licencia `-ND`.
  - Scientific Data (s. f.-b)
* - **LIC-04**
  - Obligatorio
  - Los datos, el código y el texto declaran su licencia por separado, y el código usa Apache-2.0 o MIT.
  - Guía de la colección, sección «Estructura del repositorio GitHub»
* - **LIC-05**
  - Obligatorio
  - La licencia de los datos es una licencia estándar reconocida, no un texto redactado para el caso.
  - Scientific Data (s. f.-b); Crowley (2014)
```

**Tabla 10.** Licencias requeridas.

```{list-table}
:header-rows: 1

* - Qué se licencia
  - Licencia
  - Base
* - Datos publicados
  - CC0 1.0 o CC BY 4.0
  - Scientific Data (s. f.-b); guía de la colección, sección «Estructura del repositorio GitHub»
* - Datos derivados de insumos con licencia CC BY-SA 4.0
  - CC BY-SA 4.0
  - MinTIC (2024, sección 2.2); Scientific Data (s. f.-b)
* - Narrativa y figuras
  - CC BY 4.0
  - Guía de la colección, sección «Estructura del repositorio GitHub»
* - Código
  - Apache-2.0 o MIT
  - Guía de la colección, sección «Estructura del repositorio GitHub»
```

Condiciones de las licencias de las fuentes (Scientific Data, s. f.-b):

- Las cláusulas `-SA` y `-NC` no se permiten en los datos publicados, salvo cuando se trata de datos secundarios generados a partir de datos primarios de terceros cuyas condiciones deban conservarse.
- Cuando el insumo tiene una cláusula `-ND`, que normalmente impide cualquier derivado, no es posible construir con él un conjunto secundario.

### 2.7 Depósito, identificadores y citación

Los datos se depositan en un repositorio que cumple los requisitos de DEP-01. Un sitio personal o una nube informal no cumplen el requisito DEP-02 (Scientific Data, s. f.-a). Para esta colección, el repositorio de depósito es Zenodo, según la [guía de la colección](01-cuadernos-de-conocimiento.md). Sus políticas generales establecen que cualquier usuario registrado puede depositar contenido sobre el que tenga derechos, que el límite es de 50 GB por registro, que los archivos públicos deben llevar una licencia, que el acceso se ofrece por HTTP y que los registros se conservan durante la vida del laboratorio anfitrión, el CERN (Zenodo, s. f.). Tras depositar, se debe abrir la página del DOI y comprobar que el archivo se descarga directamente por HTTPS (DEP-01).

```{list-table}
:header-rows: 1

* - ID
  - Nivel
  - Requisito
  - Base
* - **DEP-01**
  - Obligatorio (crítico)
  - Los datos publicados están en un repositorio que garantiza preservación a largo plazo, identificador persistente (DOI) y descarga directa por HTTPS desde la página del DOI.
  - Scientific Data (s. f.-b)
* - **DEP-02**
  - Obligatorio
  - Ningún dato publicado reside únicamente en un sitio personal, en un sitio institucional informal o en una nube informal.
  - Scientific Data (s. f.-a), apartado Repositories
* - **DEP-03**
  - Obligatorio (crítico)
  - Cada conjunto de datos publicado tiene un DOI.
  - Wilkinson et al. (2016), F1; COPDESS (s. f.)
* - **DEP-04**
  - Obligatorio
  - Cada versión de un conjunto de datos tiene un solo DOI declarado, y el DOI del concepto se distingue del DOI de la versión.
  - Requisito de esta guía; Guha-Sapir et al. (2026), apartados Data Records y Data availability
* - **DEP-05**
  - Obligatorio
  - Los datos se descargan por HTTPS sin registro y sin pago.
  - Wilkinson et al. (2016), A1.1; Scientific Data (s. f.-b)
* - **DEP-06**
  - Obligatorio
  - Cada persona autora tiene ORCID y lo declara en `CITATION.cff`.
  - COPDESS (s. f.)
* - **DEP-07**
  - Obligatorio
  - Los datos de entrada y los derivados se citan en el texto y en la lista de referencias con DOI en formato URL, autores y título tal como figuran en el repositorio, nombre del repositorio y año.
  - Scientific Data (s. f.-c), apartado Citing Data; COPDESS (s. f.)
* - **DEP-08**
  - Obligatorio
  - Si el conjunto de datos ya se publicó junto con un artículo, se citan ambos.
  - Scientific Data (s. f.-a), apartado Data citation
* - **DEP-09**
  - Obligatorio
  - Existe `DATA_STATEMENT.md` con la declaración de disponibilidad de datos (Sección 2.8).
  - COPDESS (s. f.); Scientific Data (s. f.-c)
* - **DEP-10**
  - Obligatorio
  - Existe una declaración de disponibilidad de código, incluso cuando no hay código propio.
  - Scientific Data (s. f.-c)
* - **DEP-11**
  - Obligatorio
  - Se creó un *release* en GitHub antes de archivar el repositorio en el depósito.
  - Guía de la colección
```

**Qué debe tener una cita de datos** (Scientific Data, s. f.-c, apartado Citing Data; COPDESS, s. f.):

1. Autores y título tal como están registrados en el repositorio. Si el repositorio no los registra, no se agregan.
2. Nombre del repositorio.
3. Año en que los datos estuvieron disponibles.
4. DOI en formato URL (`https://doi.org/...`).

**Plantilla de cita de datos** (formato APA 7):

```text
Apellido, N., y Apellido, N. (año). Título del conjunto de datos (versión X) [Conjunto de datos]. Zenodo. https://doi.org/10.5281/zenodo.XXXXXXX
```

**Observación sobre DEP-04.** En Guha-Sapir et al. (2026), el apartado Data Records cita el DOI `10.5281/zenodo.16837694` y el apartado Data availability cita `10.5281/zenodo.16837695` para el depósito de los datos. El texto no aclara si uno es el DOI del concepto y el otro el de una versión. Un cuaderno de la colección declara cuál es cuál.

### 2.8 Declaración de disponibilidad de datos y de código

Cada cuaderno incluye un archivo `DATA_STATEMENT.md` y copia su contenido en el apartado «Disponibilidad de datos y de código» del cuaderno. La declaración repite los puntos principales del apartado donde se describen los archivos; esa duplicación es intencional (Scientific Data, s. f.-c). Usa la plantilla siguiente.

```markdown
# Declaración de disponibilidad de datos y de código

## Datos de entrada
- <Nombre>. <Entidad productora>, <año>. <URL o DOI>. Licencia: <licencia>.
  Restricciones de uso: <redistribución, combinación, cita>.
  Descargado el <AAAA-MM-DD>. Se obtiene con `scripts/01_descarga.py`.

## Datos derivados publicados
- <Nombre>. DOI: <doi>. Licencia: <CC0 o CC BY>. Metadatos RDLS: `metadata/rdls/<archivo>.json`.

## Datos con acceso restringido
- <Nombre>. Motivo: <privacidad | autorización de la comunidad | licencia>.
  Cómo solicitar el acceso: <contacto>.

## Revisión CARE
- ¿Involucra pueblos, comunidades o conocimientos de pueblos étnicos? <Sí/No>.
  Autorización: <constancia o «No aplica»>.

## Disponibilidad de código
- Repositorio: <URL>. Versión: <vX.Y.Z>. DOI: <doi>. Licencia: <licencia>.
- Software y versiones principales: <paquete==versión>.
- Si no hay código propio, escriba: «No se usó código propio».

## Validación técnica y limitaciones
- Comprobaciones realizadas: <control de calidad, comparaciones, pruebas>.
- Limitaciones introducidas por el procesamiento: <interpolación, remuestreo, recortes>.
- Limitaciones heredadas de las fuentes: <sesgos de reporte, vacíos, cobertura>.

## Compromiso de preservación
- Responsable: <persona o dependencia, contacto>.
- Los datos se conservarán al menos cinco años después de la publicación.
```

### 2.9 Calidad mínima de los datos publicados

El Portal Nacional de Datos Abiertos mantiene un listado de errores frecuentes de calidad de los conjuntos de datos, con 25 entradas identificadas por los códigos ERR001 a ERR022 y sus subcódigos, cada una con su descripción y la solución recomendada (Ministerio de Tecnologías de la Información y las Comunicaciones [MinTIC], 2026a). Los requisitos CAL adoptan los criterios de ese listado que son aplicables a los datos derivados de un cuaderno. Los umbrales de CAL-10 (50 registros y 5 columnas) son los que el portal usa para valorar el potencial de reutilización de un conjunto (MinTIC, 2026a, ERR005 y ERR008_1).

```{list-table}
:header-rows: 1

* - ID
  - Nivel
  - Requisito
  - Base
* - **CAL-01**
  - Obligatorio
  - El título y la descripción de cada conjunto están completos y no usan siglas ni caracteres especiales sin definirlos.
  - MinTIC (2026a), ERR001; MinTIC (2024), sección 5.3.1
* - **CAL-02**
  - Obligatorio
  - Ninguna columna publicada carece de nombre ni tiene un nombre ambiguo.
  - MinTIC (2026a), ERR008_2
* - **CAL-03**
  - Obligatorio
  - Los valores faltantes se dejan vacíos y se documentan en el diccionario de variables; no se codifican con un valor (por ejemplo, `0`) que pueda confundirse con un dato.
  - MinTIC (2026a), ERR007; Requisito de esta guía
* - **CAL-04**
  - Obligatorio
  - El conjunto no contiene filas duplicadas.
  - MinTIC (2026a), ERR020
* - **CAL-05**
  - Obligatorio
  - El tipo de dato de cada columna corresponde a su contenido: las fechas son fechas, los números son números y los códigos son texto.
  - MinTIC (2026a), ERR019
* - **CAL-06**
  - Obligatorio
  - Los datos se publican con el mayor nivel de detalle disponible; los totales y los resúmenes se publican en un archivo aparte.
  - MinTIC (2026a), ERR016
* - **CAL-07**
  - Obligatorio
  - Los datos de varios periodos con la misma estructura se publican en un solo conjunto con una columna de periodo o de fecha, no en archivos separados por año.
  - MinTIC (2026a), ERR011 y ERR015
* - **CAL-08**
  - Obligatorio
  - Si el conjunto incluye direcciones o localizaciones textuales, incluye también columnas numéricas de latitud y longitud en grados decimales, con el sistema de referencia declarado (EST-05).
  - MinTIC (2026a), ERR009
* - **CAL-09**
  - Obligatorio
  - El conjunto declara su frecuencia de actualización y se actualiza conforme a ella, o declara que es una versión final sin actualizaciones previstas.
  - MinTIC (2026a), ERR014; MinTIC (2024), sección 5.3.1
* - **CAL-10**
  - Recomendado
  - El conjunto tiene al menos 50 registros y 5 columnas; si tiene menos, la descripción explica la razón.
  - MinTIC (2026a), ERR005 y ERR008_1
* - **CAL-11**
  - Obligatorio
  - La descripción y el diccionario permiten interpretar el conjunto sin contexto adicional.
  - MinTIC (2026a), ERR017
```

### 2.10 Validación técnica y limitaciones

Una descripción de datos incluye las comprobaciones que respaldan su calidad (Scientific Data, s. f.-c). Guha-Sapir et al. (2026, apartado Technical Validation) presentan las limitaciones del conjunto MERGE en dos grupos:

- **Limitaciones de la integración**, introducidas por el procesamiento. Entre las reportadas, solo el 11,8 % de los eventos de EM-DAT y el 3,3 % de los de IDMC tienen código GLIDE, de modo que los eventos sin código no pueden unirse; y el recorte de rásteres por celdas tocadas (*all-touched*) sobreestima el área de polígonos pequeños hasta en un 44 %.
- **Limitaciones heredadas de las fuentes**, que no introduce el procesamiento. Entre las reportadas, los criterios de inclusión de EM-DAT excluyen eventos pequeños, y algunos rásteres tienen celdas sin dato.

```{list-table}
:header-rows: 1

* - ID
  - Nivel
  - Requisito
  - Base
* - **VAL-01**
  - Obligatorio
  - El cuaderno describe las comprobaciones de calidad realizadas sobre los datos.
  - Scientific Data (s. f.-c), apartado Technical Validation
* - **VAL-02**
  - Obligatorio
  - Las limitaciones se presentan en dos grupos: las introducidas por el procesamiento y las heredadas de las fuentes.
  - Guha-Sapir et al. (2026), apartado Technical Validation
* - **VAL-03**
  - Obligatorio
  - Cada limitación se cuantifica cuando es posible (porcentaje de valores faltantes, de coincidencias, error estimado).
  - Guha-Sapir et al. (2026), apartado Technical Validation
* - **VAL-04**
  - Obligatorio
  - Los sesgos conocidos de cada insumo se declaran y se respetan en el análisis.
  - CRED (2026), sección 5
* - **VAL-05**
  - Obligatorio
  - La descripción de los datos se limita a su contenido técnico; si incluye un resumen de resultados, no excede un párrafo y dos figuras o tablas.
  - Scientific Data (s. f.-c), apartado Data Overview
* - **VAL-06**
  - Recomendado
  - Los datos tienen pruebas automáticas en `scripts/` (por ejemplo, con `pandera`).
  - CRED (2026), sección 6.2
```

### 2.11 Preservación y versionado

Scientific Data (s. f.-a) describe solo conjuntos terminados y no admite actualizaciones aditivas de un conjunto ya evaluado; admite correcciones. Si se planean actualizaciones, se deposita una versión estática y las siguientes se publican como versiones nuevas.

```{list-table}
:header-rows: 1

* - ID
  - Nivel
  - Requisito
  - Base
* - **PRE-01**
  - Obligatorio
  - Cada cambio sustantivo de los datos genera una versión nueva con su propio DOI, y la versión publicada no se modifica salvo para corregirla.
  - Scientific Data (s. f.-a), apartado Dataset updates
* - **PRE-02**
  - Obligatorio
  - Existe el compromiso escrito de conservar los datos al menos cinco años después de la publicación.
  - Scientific Data (s. f.-a), apartado Data preservation
* - **PRE-03**
  - Obligatorio
  - El campo `contact_point` identifica a una persona o dependencia que responde a los correos.
  - GFDRR (2026)
* - **PRE-04**
  - Obligatorio
  - Existe un `CHANGELOG.md` de los datos que registra las correcciones.
  - Requisito de esta guía
* - **PRE-05**
  - Recomendado
  - Cada tres meses se comprueba que las URL de los insumos siguen activas.
  - Requisito de esta guía
```

### 2.12 Insumos del Portal Nacional de Datos Abiertos (datos.gov.co)

**Marco legal.** La Ley 1712 de 2014 define los datos abiertos como «todos aquellos datos primarios o sin procesar, que se encuentran en formatos estándar e interoperables que facilitan su acceso y reutilización, los cuales están bajo la custodia de las entidades públicas o privadas que cumplen con funciones públicas y que son puestos a disposición de cualquier ciudadano, de forma libre y sin restricciones, con el fin de que terceros puedan reutilizarlos y crear servicios derivados de los mismos» (Congreso de la República de Colombia, 2014, art. 6, literal j). La misma ley exceptúa de la publicación la información pública clasificada, cuyo acceso puede dañar los derechos a la intimidad, a la vida, a la salud o a la seguridad, y los secretos comerciales, industriales y profesionales (art. 18), y la información pública reservada, que protege intereses públicos como la defensa y la seguridad nacional, la seguridad pública, los derechos de la infancia y la adolescencia y la salud pública, entre otros (art. 19). Los sujetos obligados mantienen un índice actualizado de la información clasificada y reservada (art. 20).

**Observación sobre la fuente.** La historia del portal (MinTIC, 2026c) ubica la definición de datos abiertos en el «Numeral 6, Artículo 6» de la Ley 1712. El texto de la ley, consultado en el sitio de la Secretaría del Senado, la ubica en el literal j) del artículo 6. Este documento cita el literal j).

**Tabla 11.** Elementos de la historia «¿Tú primera vez con Datos Abiertos?» (MinTIC, 2026c) y su uso en estos requisitos.

```{list-table}
:header-rows: 1

* - Elemento (sección de la historia)
  - Contenido
  - Uso en estos requisitos
  - Requisitos
* - Definición de datos abiertos (2)
  - Reproduce la definición del artículo 6 de la Ley 1712 de 2014
  - Se emplea para definir qué es un insumo abierto
  - GOV-08
* - Sujetos obligados (2)
  - Entidades públicas de todos los niveles y órdenes, y otras personas que ejercen funciones públicas o administran recursos públicos
  - Se emplea para identificar quién publica los insumos oficiales; la obligación de publicar no recae en quien usa los datos
  - Ninguno
* - Conjuntos obligatorios (3)
  - Registro de Activos de Información, Esquema de Publicación de Información e Índice de Información Clasificada y Reservada, publicados de forma consolidada
  - Se emplea el índice de información clasificada y reservada como control previo a la publicación de derivados
  - GOV-08
* - Qué datos abrir (4)
  - No se abren datos personales, clasificados ni reservados, según las leyes 1712 de 2014 y 1581 de 2012
  - Se emplea
  - GOV-08, PER-02
* - Estructura del conjunto (5)
  - Formato abierto (CSV, JSON), diccionario de datos e información de contacto del responsable
  - Se emplea
  - EST-02, EST-04, PRE-03
* - Validación del portal (6)
  - Formato abierto y estructurado, diccionario claro y completo, ausencia de información sensible y campos normalizados; errores comunes de rechazo
  - Se emplea como base de los requisitos CAL
  - CAL, GOV-12
* - Licencia (7)
  - Licencia CC BY-SA 4.0 con atribución y compartir igual; acceso gratuito
  - Se emplea con verificación por conjunto, porque las licencias del portal varían (Tabla 14)
  - INV-04, GOV-02 a GOV-05
* - Inventario y descarga masiva (8 y 9)
  - Inventario descargable de los conjuntos del portal
  - Se emplea para registrar los metadatos de los insumos
  - GOV-11
* - Vistas filtradas (10)
  - Una entidad territorial no duplica un conjunto nacional; crea una vista filtrada
  - Se emplea: se cita el conjunto nacional y el filtro aplicado
  - GOV-10
* - Gráficos e historias (11)
  - Herramientas del portal para visualizar datos
  - No se emplea: está fuera del alcance de estos requisitos
  - Ninguno
* - Procedimientos de publicación de las entidades (5)
  - Registro como funcionario y solicitud de permisos de publicador
  - No se emplea: aplica a las entidades que publican
  - Ninguno
* - Capacitación y curso virtual (12)
  - Videotutoriales, guías, capacitación técnica y un curso certificable
  - No se emplea como requisito
  - Ninguno
* - Hojas de ruta nacional y sectoriales (13)
  - Una hoja de ruta nacional y 25 hojas sectoriales de datos abiertos estratégicos
  - No se emplea; su contenido no se revisó
  - Ninguno
* - Avance de la iniciativa e índices internacionales (14 y 15)
  - Resultados del país en índices de apertura de datos
  - No se emplea
  - Ninguno
```

```{list-table}
:header-rows: 1

* - ID
  - Nivel
  - Requisito
  - Base
* - **GOV-01**
  - Obligatorio
  - Para cada insumo de datos.gov.co, `sources.csv` registra el identificador del conjunto en el portal (formato `xxxx-xxxx`), la URL del conjunto y la fecha de la última actualización de los datos.
  - Requisito de esta guía; metadatos del portal (MinTIC (2024), sección 5.3.1)
* - **GOV-02**
  - Obligatorio
  - La licencia de cada insumo del portal se toma del metadato de ese conjunto; no se supone que todos los conjuntos tienen la misma licencia.
  - MinTIC (2024), sección 2.2; Tabla 14
* - **GOV-03**
  - Obligatorio
  - Un insumo sin licencia declarada no se redistribuye hasta obtener confirmación escrita de la entidad productora.
  - Requisito de esta guía (aplicación de INV-05)
* - **GOV-04**
  - Obligatorio
  - Los datos derivados de insumos con licencia CC BY-SA 4.0 se publican bajo CC BY-SA 4.0.
  - MinTIC (2024), sección 2.2; Scientific Data (s. f.-b)
* - **GOV-05**
  - Obligatorio
  - La atribución de cada insumo incluye la entidad productora, el título del conjunto, la URL del conjunto en el portal y la fecha de consulta.
  - MinTIC (2024), sección 2.2
* - **GOV-06**
  - Obligatorio
  - La descarga por API usa `$limit` y `$offset` explícitos y verifica que el número de filas descargadas es igual al conteo de la fuente.
  - Socrata (s. f.-b)
* - **GOV-07**
  - Obligatorio
  - Cada descarga se conserva en `data/raw/` con su suma de verificación SHA-256 y la fecha de descarga; si el conjunto es demasiado grande para conservarlo, se conservan el extracto filtrado y la consulta que lo produjo.
  - Requisito de esta guía; MinTIC (2024), sección 5.3.1 (periodicidad)
* - **GOV-08**
  - Obligatorio
  - Antes de publicar datos derivados de insumos de entidades públicas se verificó que no contienen información pública clasificada o reservada ni datos personales, y se consultó el índice de información clasificada y reservada de la entidad.
  - Congreso de la República de Colombia (2014), arts. 6 (literales c y d), 18, 19 y 20; MinTIC (2026c), secciones 3 y 4
* - **GOV-09**
  - Obligatorio
  - Si el insumo pertenece a una serie fragmentada por periodos o por versiones, el cuaderno documenta las diferencias de columnas, de licencia y de cobertura entre las partes.
  - Requisito de esta guía; MinTIC (2026a), ERR011 y ERR015
* - **GOV-10**
  - Obligatorio
  - Si el insumo es un subconjunto territorial de un conjunto nacional, el cuaderno cita el conjunto nacional y registra el filtro aplicado.
  - MinTIC (2026c), sección 10; MinTIC (2026a), ERR012
* - **GOV-11**
  - Recomendado
  - Los metadatos de cada insumo se obtienen de la API (`/api/views/<id>.json`) o del catálogo (`/data.json`) y se guardan junto con la descarga.
  - Requisito de esta guía; MinTIC (2026b)
* - **GOV-12**
  - Recomendado
  - Los datos derivados que se publiquen además en datos.gov.co cumplen los criterios de validación del portal: formato abierto y estructurado, diccionario de datos claro y completo, ausencia de información sensible y campos normalizados.
  - MinTIC (2026c), sección 6
```

**Acceso por API.** El portal usa la plataforma Socrata. Cada conjunto se consulta en `https://www.datos.gov.co/resource/<id>.<formato>`, con los formatos `json`, `csv` o `geojson`. Los metadatos de cada conjunto están en `https://www.datos.gov.co/api/views/<id>.json` y el catálogo completo en `https://www.datos.gov.co/data.json`, que sigue el esquema Project Open Data v1.1 (comprobado el 16 de noviembre de 2026). Si no se indica `$limit`, la API devuelve 1 000 registros por solicitud (Socrata, s. f.-b). El uso de un *app token* es opcional; sin token, las solicitudes comparten un límite por dirección IP y, si se excede, la respuesta es el código 429 (Socrata, s. f.-a). El conjunto «Emergencias UNGRD V2» tiene 6 506 registros; el 16 de noviembre de 2026 una solicitud sin `$limit` devolvió solo 1 000. Para conjuntos muy grandes, como la serie «Temperatura Ambiente del Aire» del IDEAM (94 062 593 registros a esa fecha), se usan los parámetros `$select` y `$where` para descargar solo el extracto necesario (GOV-07).

El siguiente script cumple GOV-06 y GOV-07. Usa solo la biblioteca estándar de Python. Se ejecutó el 16 de noviembre de 2026 con el conjunto `2343-nuqp`: descargó 6 506 filas, igual al conteo de la fuente, y calculó su suma de verificación.

```python
"""Descarga completa y verificable de un conjunto de datos de datos.gov.co."""
import csv, hashlib, io, json, sys, urllib.parse, urllib.request
from datetime import date

DOMINIO = "https://www.datos.gov.co"
PAGINA = 1000  # filas por solicitud


def pedir(ruta, parametros=None, token=None):
    url = f"{DOMINIO}{ruta}"
    if parametros:
        url += "?" + urllib.parse.urlencode(parametros, quote_via=urllib.parse.quote)
    cabeceras = {"X-App-Token": token} if token else {}
    with urllib.request.urlopen(urllib.request.Request(url, headers=cabeceras), timeout=120) as r:
        return r.read()


def descargar(id_conjunto, destino_csv, donde=None, token=None):
    meta = json.loads(pedir(f"/api/views/{id_conjunto}.json", token=token))
    filtro = {"$where": donde} if donde else {}
    esperado = int(json.loads(pedir(f"/resource/{id_conjunto}.json",
                   {"$select": "count(*)", **filtro}, token))[0]["count"])
    filas, desplazamiento = [], 0
    while desplazamiento < esperado:
        bloque = pedir(f"/resource/{id_conjunto}.csv",
                       {"$limit": PAGINA, "$offset": desplazamiento, "$order": ":id", **filtro}, token)
        lector = list(csv.reader(io.StringIO(bloque.decode("utf-8"))))
        if desplazamiento == 0:
            encabezado = lector[0]
        filas.extend(lector[1:])
        desplazamiento += PAGINA
    assert len(filas) == esperado, f"Se descargaron {len(filas)} filas y la fuente declara {esperado}"
    with open(destino_csv, "w", newline="", encoding="utf-8") as f:
        w = csv.writer(f); w.writerow(encabezado); w.writerows(filas)
    sha = hashlib.sha256(open(destino_csv, "rb").read()).hexdigest()
    return {"id": id_conjunto, "titulo": meta["name"], "licencia": meta.get("licenseId"),
            "filas": esperado, "sha256": sha, "fecha_descarga": date.today().isoformat()}


if __name__ == "__main__":
    print(json.dumps(descargar(sys.argv[1], sys.argv[2]), ensure_ascii=False, indent=2))
```

**Tabla 12.** Correspondencia entre los metadatos del portal, `sources.csv` y el campo `lineage.sources` del RDLS.

```{list-table}
:header-rows: 1

* - Metadato del portal
  - Columna de `sources.csv`
  - Campo del RDLS
* - `name` (título)
  - `nombre`
  - `lineage.sources[].name`
* - `id`
  - `identificador_fuente`
  - `lineage.sources[].id`
* - URL `https://www.datos.gov.co/d/<id>`
  - `url_o_doi`
  - `lineage.sources[].url`
* - `attribution`
  - `entidad`
  - Primera parte de `lineage.sources[].citation`
* - `licenseId` y `license.termsLink`
  - `licencia`
  - `lineage.sources[].license`, con la URL de la lista de licencias del RDLS
* - `rowsUpdatedAt`
  - `fecha_actualizacion_fuente`
  - Se menciona en `lineage.description`
* - Campos personalizados «Frecuencia de Actualización» y «Cobertura Geográfica»
  - `version_o_consulta` (con el filtro aplicado)
  - `lineage.description`
* - «Cobertura Geográfica» del insumo
  - Sin columna
  - `spatial.scale` del conjunto derivado: Nacional equivale a `national`; Departamental y Municipal equivalen a `sub-national`
* - «DIVIPOLA Municipio»
  - Sin columna
  - `spatial.gazetteer_entries` con `scheme` igual a `DIVIPOLA`, un código nuevo de una lista abierta (MET-04)
```

Los valores «Centro poblado» e «Internacional» de «Cobertura Geográfica» no tienen equivalente directo en `spatial.scale` y se asignan caso por caso. Fragmento de `lineage` con un insumo del portal (valida contra el esquema del RDLS 1.0.0):

```json
"lineage": {
  "description": "Conteo de eventos de emergencia por municipio en 2025, a partir de la serie Emergencias UNGRD V2. Los códigos DIVIPOLA se normalizaron a cinco caracteres de texto.",
  "sources": [
    {
      "id": "ungrd-emergencias-v2",
      "name": "Emergencias UNGRD V2",
      "url": "https://www.datos.gov.co/d/2343-nuqp",
      "citation": "Unidad Nacional para la Gestión del Riesgo de Desastres. (2026). Emergencias UNGRD V2 [Conjunto de datos]. Portal Nacional de Datos Abiertos. https://www.datos.gov.co/d/2343-nuqp",
      "type": "dataset",
      "license": "https://creativecommons.org/licenses/by/4.0/"
    }
  ]
}
```

**Conjuntos del portal de interés para el análisis del riesgo.** La Tabla 13 reúne conjuntos publicados por el IDEAM, el DANE y la UNGRD que se consultaron el 16 de noviembre de 2026 (MinTIC, 2026b). Las búsquedas de «sismicidad», «catálogo sísmico», «sismológica», «tsunami», «maremoto», «volcán» y «huracán ciclón» en el catálogo no devolvieron ningún conjunto, y la búsqueda de «terremoto» devolvió dos conjuntos que no son catálogos sísmicos. Los catálogos de sismicidad y de tsunamis se obtienen, por tanto, de otras fuentes.

**Tabla 13.** Conjuntos del portal de interés para el análisis del riesgo (consulta del 16 de noviembre de 2026).

```{list-table}
:header-rows: 1

* - Identificador
  - Título en el portal
  - Entidad
  - Licencia
  - Registros
  - Última actualización
* - `2343-nuqp`
  - Emergencias UNGRD V2
  - UNGRD
  - CC BY 4.0
  - 6 506
  - 2026-11-06
* - `hp9r-jxuu`
  - Catálogo Nacional de Estaciones del IDEAM
  - IDEAM
  - CC BY-SA 4.0
  - 29 320
  - 2026-11-16
* - `sbwg-7ju4`
  - Temperatura Ambiente del Aire
  - IDEAM
  - CC BY-SA 4.0
  - 94 062 593
  - 2026-11-15
* - `bdmn-sqnh`
  - Nivel Instantáneo del Rio
  - IDEAM
  - CC BY-SA 4.0
  - 21 837 924
  - 2026-11-15
* - `jrp4-7gmb`
  - Amenaza de Inundación Período de Retorno 2 Años 79 Centros Poblados
  - IDEAM
  - CC BY-SA 4.0
  - 47 969
  - 2025-08-04
* - `gdxc-w37w`
  - DIVIPOLA- Códigos municipios
  - DANE
  - CC BY-SA 4.0
  - 1 122
  - 2025-01-24
```

**Tabla 14.** Serie «Emergencias UNGRD» en el portal (UNGRD, 2026; consulta del 16 de noviembre de 2026).

```{list-table}
:header-rows: 1

* - Identificador
  - Título en el portal
  - Columnas
  - Licencia
  - Última actualización
* - `4fd8-ptcr`
  - Emergencias UNGRD 2019
  - 73
  - CC BY-SA 4.0
  - 2020-07-29
* - `4t8v-ywmw`
  - Emergencias 2020
  - 74
  - CC BY-SA 4.0
  - 2021-06-09
* - `wwkg-r6te`
  - Emergencias UNGRD.
  - 71
  - CC BY-SA 4.0
  - 2023-09-07
* - `rgre-6ak4`
  - Emergencias UNGRD2023 - 2024
  - 69
  - CC BY-SA 4.0
  - 2025-07-21
* - `2343-nuqp`
  - Emergencias UNGRD V2
  - 61
  - CC BY 4.0
  - 2026-11-06
```

La serie está fragmentada por periodos, con entre 61 y 74 columnas y dos licencias distintas. La descripción de «Emergencias UNGRD V2» indica que se publica el reporte de 2025 «y posibles vigencias futuras» (UNGRD, 2026). La revisión de ese conjunto el 16 de noviembre de 2026 produjo los hallazgos siguientes, que los requisitos CAL y EST-09 convierten en comprobaciones:

1. Contiene 6 506 registros, del 1 de enero al 31 de diciembre de 2025, y sus 61 columnas tienen descripción.
2. En 6 504 registros (99,97 %), la columna `coordenadas` contiene el texto `0`. Los otros dos registros usan formatos distintos: un par decimal y grados, minutos y segundos escritos como texto (CAL-03, CAL-08).
3. La columna `codificaci_n_segun_divipola` es numérica. En 242 registros el código tiene menos de cinco dígitos porque perdió el cero inicial; por ejemplo, el valor `5001` en lugar de `05001` para Medellín, que es el código del DANE (2025). Un registro tiene el código `5`, de un solo carácter (EST-09).
4. El conjunto «DIVIPOLA- Códigos municipios» (DANE, 2025) guarda la longitud y la latitud como texto con coma decimal, por ejemplo `-75,581775` (EST-10).

### 2.13 Insumos con condiciones propias: EM-DAT

EM-DAT es una base de datos de desastres de uso frecuente. Su documentación (CRED, 2026) y sus textos legales (UCLouvain, 2025, 2026) fijan condiciones que un cuaderno debe cumplir. Los requisitos EMD aplican solo a los cuadernos que usan EM-DAT; en los demás, su estado es «No aplica».

```{list-table}
:header-rows: 1

* - ID
  - Nivel
  - Requisito
  - Base
* - **EMD-01**
  - Obligatorio (crítico)
  - Si el cuaderno usa EM-DAT, quien lo usa es una entidad no comercial y el uso no tiene fines de lucro.
  - UCLouvain (2026), arts. 1 a 3, 5 y 6
* - **EMD-02**
  - Obligatorio
  - EM-DAT se cita con el año de acceso, la sigla EM-DAT con el producto usado y la URL o el DOI.
  - UCLouvain (2025)
* - **EMD-03**
  - Obligatorio (crítico)
  - El repositorio no contiene los datos de EM-DAT ni una parte sustancial de ellos; contiene el script de descarga.
  - UCLouvain (2026), arts. 3.2 y 3.4
* - **EMD-04**
  - Obligatorio
  - Si el análisis une registros de EM-DAT con otra base de datos, el repositorio guarda la autorización escrita de CRED.
  - UCLouvain (2026), art. 9.3
* - **EMD-05**
  - Recomendado
  - Los análisis de tendencia no incluyen registros de EM-DAT anteriores al año 2000.
  - CRED (2026), sección 5.2
* - **EMD-06**
  - Obligatorio
  - Las celdas vacías de EM-DAT no se reemplazan por cero.
  - CRED (2026), sección 3.3
* - **EMD-07**
  - Recomendado
  - Se usa el EM-DAT Archive en lugar de la base viva.
  - CRED (2026), sección 2
```

**Tabla 15.** Condiciones de EM-DAT y requisito que las implementa.

```{list-table}
:header-rows: 1

* - Aspecto
  - Contenido de la fuente
  - Requisito
* - **Productos y acceso**
  - La base viva se actualiza cada semana. El EM-DAT Archive es una copia validada, alojada en el repositorio de datos de UCLouvain bajo licencia CC BY-NC-ND 4.0, y la documentación lo señala como la opción preferida para investigación. La documentación lista la versión 2.0 (30 de abril de 2026; registros 1900–2024) (CRED, 2026, secciones 2 y 6.2). El registro del Archive muestra la versión 2.1, publicada el 2 de noviembre de 2026 (Delforge et al., 2026).
  - INV-08, EMD-07
* - **Licencia**
  - El acceso es gratuito para entidades no comerciales, entre las que se incluyen los gobiernos nacionales, y requiere registro. Las entidades con fines de lucro pagan una suscripción anual de 10 000 euros. No se redistribuye la base ni una parte sustancial de ella. Salvo acuerdo escrito, no se fusiona con otras bases de datos (UCLouvain, 2026, arts. 1, 3, 5, 6 y 9.3).
  - EMD-01, EMD-03, EMD-04
* - **Cita**
  - La cita mínima incluye el año de acceso, la sigla EM-DAT con la especificación del producto y la URL o el DOI del producto (UCLouvain, 2025).
  - EMD-02
* - **Criterios de entrada**
  - Un desastre entra si cumple al menos uno de estos criterios: 10 o más muertos (incluidos desaparecidos), 100 o más afectados, o una declaración de emergencia o un llamado a la ayuda internacional. Se hace público cuando al menos dos fuentes lo confirman (CRED, 2026, secciones 4.1 y 4.2).
  - VAL-04
* - **Sesgos**
  - La documentación describe sesgos de tiempo, de amenaza, de umbral, de contabilidad y geográficos. Para análisis de tendencia recomienda excluir los datos anteriores al año 2000 (CRED, 2026, sección 5.2). Menciona que los eventos pequeños pueden tener un impacto acumulado alto, con el caso de Colombia estudiado por Marulanda et al. (2010).
  - VAL-04, EMD-05
* - **Celdas vacías**
  - Una celda vacía puede significar «sin impacto» o «impacto desconocido» (CRED, 2026, sección 3.3).
  - EMD-06
* - **Unidades económicas**
  - Los daños se expresan en miles de dólares estadounidenses del momento del evento. El ajuste por inflación usa el índice de precios al consumidor de Estados Unidos de la OCDE y no existe para el año en curso (CRED, 2026, sección 4.3).
  - EST-04
* - **Identificadores y territorios**
  - Cada desastre tiene un identificador único (`DisNo.`) y se registra por país con códigos ISO-3. La georreferenciación usa unidades GADM 4.1; antes de 2026 usaba GAUL 2015 (CRED, 2026, secciones 3.2, 3.3, 3.8 y 4.2). El número GLIDE se usa para vincular registros entre bases de datos (CRED, 2026, sección 6.2).
  - EST-06
* - **Validación**
  - El equipo de EM-DAT publica EM-TEST, un marco de pruebas con `pandas` y `pandera` que valida los archivos y la compatibilidad entre versiones (CRED, 2026, sección 6.2).
  - VAL-06
* - **Descargo**
  - Los datos se entregan en el estado en que se encuentran (*as is*), sin garantía de completitud ni de exactitud (CRED, 2026, sección 1).
  - VAL-04
```

El RDLS reconoce estos identificadores: su lista abierta `classification_scheme` incluye `EMDAT` y `GLIDE` como esquemas de identificación de desastres (GFDRR, 2026, listas de códigos).

**Filas de ejemplo para `sources.csv`.** Los valores entre `<>` son marcadores.

```text
nombre,entidad,identificador_fuente,url_o_doi,version_o_consulta,metodo_extraccion,formato,resolucion_espacial,resolucion_temporal,variables,fecha_actualizacion_fuente,fecha_descarga,licencia,restricciones_de_uso
EM-DAT Archive,CRED/UCLouvain,DVN/I0LTPH,https://doi.org/10.14428/DVN/I0LTPH,<versión del Archive>,descarga manual tras aceptar la licencia,xlsx,país (ISO-3),evento,"DisNo., Total Deaths, Total Affected, Total Damage",<AAAA-MM-DD>,<AAAA-MM-DD>,CC BY-NC-ND 4.0,"no redistribuir; autorización escrita para combinar con otras bases"
Emergencias UNGRD V2,UNGRD,2343-nuqp,https://www.datos.gov.co/d/2343-nuqp,descarga completa de 6506 filas,API SODA en csv,csv,municipio (DIVIPOLA),evento,"fecha, municipio, evento, muertos, personas",2026-11-06,2026-11-16,CC BY 4.0,"atribución a la entidad productora"
```

**Plantilla de cita de EM-DAT** (UCLouvain, 2025):

```text
EM-DAT data, <año de acceso>, <URL o DOI del producto usado>
```

:::{note} Datos construidos con modelos de lenguaje
La documentación de EM-DAT enlaza conjuntos aumentados que usan modelos de lenguaje para extraer información de noticias o de Wikipedia (CRED, 2026, sección 6.2). Los cuadernos que usen o produzcan datos así aplican, además, las reglas de la sección {ref}`uso-de-ia-datos`.
:::

## 3. Lista de verificación

La lista tiene 92 requisitos: 80 obligatorios y 12 recomendados. Los 11 requisitos **críticos** (INV-04, INV-05, INV-06, MET-03, PER-02, LIC-01, LIC-02, DEP-01, DEP-03, EMD-01, EMD-03) bloquean la publicación si no se cumplen.

**Criterio de aceptación.** Un cuaderno cumple los requisitos para datos si (1) ningún requisito crítico está en incumplimiento y (2) el puntaje de requisitos obligatorios es de 90 o más, calculado como se indica en el prompt de la Sección 4.

**2.1. Inventario y selección de insumos**

- [ ] **INV-01.** Cada insumo (dato de entrada) figura en `metadata/sources.csv` con las columnas de la Tabla 3.
- [ ] **INV-02.** La URL o el DOI de cada insumo apunta al archivo o al registro exacto, no a la página de inicio de la fuente.
- [ ] **INV-03.** Si el insumo se actualiza de forma continua, `sources.csv` registra la versión o, en su defecto, los parámetros de la consulta (incluido cualquier filtro territorial o temporal) y la fecha de descarga.
- [ ] **INV-04.** **Crítico.** Todo insumo puede obtenerse sin pago: ninguno exige suscripción ni licencia de pago para el uso que hace el cuaderno.
- [ ] **INV-05.** **Crítico.** Los datos de terceros se copian al repositorio solo si su licencia o sus términos de uso permiten redistribuirlos; en caso contrario, el repositorio contiene el script de descarga y la cita.
- [ ] **INV-06.** **Crítico.** Los términos de uso de cada insumo se leyeron completos y sus restricciones (redistribución, combinación con otras bases de datos, cita exigida) están registradas en `sources.csv`.
- [ ] **INV-07.** Si el insumo es una compilación de fuentes, cada registro lleva su fuente (DOI, URL o equivalente) y ningún registro se marca como «sin publicar» sin fuente.
- [ ] **INV-08.** *(Recomendado)* Cuando el insumo tiene una versión archivada y citable, se usa esa versión y no la versión viva.

**2.2. Estructura de archivos y formatos**

- [ ] **EST-01.** Los datos están en `data/raw`, `data/interim` y `data/processed`; `raw` contiene los originales sin modificar o el script que los descarga.
- [ ] **EST-02.** Los datos publicados tienen formatos abiertos, no propietarios y procesables por máquina (Tabla 4). Los insumos pueden conservar el formato de la fuente.
- [ ] **EST-03.** Los datos se entregan completos y en bloque, no solo como visualización.
- [ ] **EST-04.** Cada tabla tiene un diccionario de variables con nombre, descripción, tipo, unidad y valores permitidos.
- [ ] **EST-05.** Cada recurso declara el sistema de coordenadas (código EPSG), la resolución espacial y la resolución temporal.
- [ ] **EST-06.** Las fechas tienen el formato AAAA-MM-DD y los países se identifican con los códigos ISO 3166-1 alfa-3 de la lista `country` del RDLS.
- [ ] **EST-07.** `metadata/data_catalog.csv` lista cada archivo publicado con su descripción, formato, tamaño y licencia.
- [ ] **EST-08.** *(Recomendado)* Los nombres de archivo no tienen espacios ni tildes.
- [ ] **EST-09.** Los departamentos y municipios se identifican con el código DIVIPOLA del DANE, almacenado como texto con ceros a la izquierda: dos caracteres para departamentos (por ejemplo, `05`) y cinco para municipios (por ejemplo, `05001`).
- [ ] **EST-10.** Los valores numéricos usan el punto como separador decimal y no incluyen separador de miles ni texto.
- [ ] **EST-11.** Si el conjunto clasifica amenazas o eventos, usa los códigos HIPs 2025 y registra la equivalencia con la clasificación de la fuente (aplica solo si el conjunto clasifica amenazas).
- [ ] **EST-12.** *(Recomendado)* Los indicadores de daños y pérdidas se definen según los indicadores del Marco de Sendai cuando existe uno equivalente.

**2.3. Metadatos con el Risk Data Library Standard**

- [ ] **MET-01.** Existe un archivo `metadata/rdls/<nombre>.json` por cada conjunto de datos publicado.
- [ ] **MET-02.** Cada archivo incluye los diez campos obligatorios del esquema (Tabla 5).
- [ ] **MET-03.** **Crítico.** Cada archivo valida sin errores contra el esquema canónico del RDLS 1.0.0.
- [ ] **MET-04.** Los campos con lista de códigos usan los códigos del RDLS sin traducirlos (por ejemplo, `license` usa la URL de la lista de licencias). Si no existe un código adecuado y la lista es cerrada, se abrió un *issue* en el repositorio del RDLS; si la lista es abierta, se usa un código nuevo y se propone en un *issue*.
- [ ] **MET-05.** El campo `id` contiene el DOI del conjunto de datos como URL (`https://doi.org/...`).
- [ ] **MET-06.** El campo `lineage` describe la procedencia: insumos (en `lineage.sources`), transformaciones y software.
- [ ] **MET-07.** Por cada valor de `risk_data_type` existe el componente correspondiente (`hazard`, `exposure`, `vulnerability` o `loss`).
- [ ] **MET-08.** *(Recomendado)* Se completan los campos opcionales `temporal`, `spatial_resolution`, `temporal_resolution`, `attributions`, `referenced_by` y `version`.

**2.5. Datos sobre personas y comunidades**

- [ ] **PER-01.** Se aplicó la prueba de la Tabla 8 (principios CARE) y su resultado está registrado en `DATA_STATEMENT.md`.
- [ ] **PER-02.** **Crítico.** No se publican datos personales ni datos de pueblos o comunidades sin una constancia de autorización registrada en `DATA_STATEMENT.md`.
- [ ] **PER-03.** Los datos sobre personas siguen una de las dos rutas de la Tabla 9: abierta o de acceso controlado.
- [ ] **PER-04.** Antes de publicar se evaluó el riesgo de reidentificación por identificadores indirectos (ubicación, género, ocupación, características de salud).
- [ ] **PER-05.** Cuando el acceso es restringido, los metadatos son públicos y se indica cómo solicitar el acceso.
- [ ] **PER-06.** Los datos de redes sociales no se indexan ni se republican sin consentimiento.
- [ ] **PER-07.** *(Recomendado)* La resolución espacial se agrega o se reduce hasta que el dato no permita identificar personas o viviendas, y la transformación se documenta en `lineage`.

**2.6. Licencias**

- [ ] **LIC-01.** **Crítico.** Existen un archivo `LICENSE` y un campo `license` del RDLS con una licencia explícita.
- [ ] **LIC-02.** **Crítico.** Los datos publicados usan CC0 o CC BY (o equivalentes) y no tienen cláusulas `-SA` ni `-NC`, salvo que sean datos secundarios que deban conservar las condiciones de la fuente (por ejemplo, CC BY-SA 4.0 cuando el insumo tiene esa licencia).
- [ ] **LIC-03.** No se publica como conjunto nuevo ningún dato derivado de una fuente con licencia `-ND`.
- [ ] **LIC-04.** Los datos, el código y el texto declaran su licencia por separado, y el código usa Apache-2.0 o MIT.
- [ ] **LIC-05.** La licencia de los datos es una licencia estándar reconocida, no un texto redactado para el caso.

**2.7. Depósito, identificadores y citación**

- [ ] **DEP-01.** **Crítico.** Los datos publicados están en un repositorio que garantiza preservación a largo plazo, identificador persistente (DOI) y descarga directa por HTTPS desde la página del DOI.
- [ ] **DEP-02.** Ningún dato publicado reside únicamente en un sitio personal, en un sitio institucional informal o en una nube informal.
- [ ] **DEP-03.** **Crítico.** Cada conjunto de datos publicado tiene un DOI.
- [ ] **DEP-04.** Cada versión de un conjunto de datos tiene un solo DOI declarado, y el DOI del concepto se distingue del DOI de la versión.
- [ ] **DEP-05.** Los datos se descargan por HTTPS sin registro y sin pago.
- [ ] **DEP-06.** Cada persona autora tiene ORCID y lo declara en `CITATION.cff`.
- [ ] **DEP-07.** Los datos de entrada y los derivados se citan en el texto y en la lista de referencias con DOI en formato URL, autores y título tal como figuran en el repositorio, nombre del repositorio y año.
- [ ] **DEP-08.** Si el conjunto de datos ya se publicó junto con un artículo, se citan ambos.
- [ ] **DEP-09.** Existe `DATA_STATEMENT.md` con la declaración de disponibilidad de datos (Sección 2.8).
- [ ] **DEP-10.** Existe una declaración de disponibilidad de código, incluso cuando no hay código propio.
- [ ] **DEP-11.** Se creó un *release* en GitHub antes de archivar el repositorio en el depósito.

**2.9. Calidad mínima de los datos publicados**

- [ ] **CAL-01.** El título y la descripción de cada conjunto están completos y no usan siglas ni caracteres especiales sin definirlos.
- [ ] **CAL-02.** Ninguna columna publicada carece de nombre ni tiene un nombre ambiguo.
- [ ] **CAL-03.** Los valores faltantes se dejan vacíos y se documentan en el diccionario de variables; no se codifican con un valor (por ejemplo, `0`) que pueda confundirse con un dato.
- [ ] **CAL-04.** El conjunto no contiene filas duplicadas.
- [ ] **CAL-05.** El tipo de dato de cada columna corresponde a su contenido: las fechas son fechas, los números son números y los códigos son texto.
- [ ] **CAL-06.** Los datos se publican con el mayor nivel de detalle disponible; los totales y los resúmenes se publican en un archivo aparte.
- [ ] **CAL-07.** Los datos de varios periodos con la misma estructura se publican en un solo conjunto con una columna de periodo o de fecha, no en archivos separados por año.
- [ ] **CAL-08.** Si el conjunto incluye direcciones o localizaciones textuales, incluye también columnas numéricas de latitud y longitud en grados decimales, con el sistema de referencia declarado (EST-05).
- [ ] **CAL-09.** El conjunto declara su frecuencia de actualización y se actualiza conforme a ella, o declara que es una versión final sin actualizaciones previstas.
- [ ] **CAL-10.** *(Recomendado)* El conjunto tiene al menos 50 registros y 5 columnas; si tiene menos, la descripción explica la razón.
- [ ] **CAL-11.** La descripción y el diccionario permiten interpretar el conjunto sin contexto adicional.

**2.10. Validación técnica y limitaciones**

- [ ] **VAL-01.** El cuaderno describe las comprobaciones de calidad realizadas sobre los datos.
- [ ] **VAL-02.** Las limitaciones se presentan en dos grupos: las introducidas por el procesamiento y las heredadas de las fuentes.
- [ ] **VAL-03.** Cada limitación se cuantifica cuando es posible (porcentaje de valores faltantes, de coincidencias, error estimado).
- [ ] **VAL-04.** Los sesgos conocidos de cada insumo se declaran y se respetan en el análisis.
- [ ] **VAL-05.** La descripción de los datos se limita a su contenido técnico; si incluye un resumen de resultados, no excede un párrafo y dos figuras o tablas.
- [ ] **VAL-06.** *(Recomendado)* Los datos tienen pruebas automáticas en `scripts/` (por ejemplo, con `pandera`).

**2.11. Preservación y versionado**

- [ ] **PRE-01.** Cada cambio sustantivo de los datos genera una versión nueva con su propio DOI, y la versión publicada no se modifica salvo para corregirla.
- [ ] **PRE-02.** Existe el compromiso escrito de conservar los datos al menos cinco años después de la publicación.
- [ ] **PRE-03.** El campo `contact_point` identifica a una persona o dependencia que responde a los correos.
- [ ] **PRE-04.** Existe un `CHANGELOG.md` de los datos que registra las correcciones.
- [ ] **PRE-05.** *(Recomendado)* Cada tres meses se comprueba que las URL de los insumos siguen activas.

**2.12. Insumos del Portal Nacional de Datos Abiertos (datos.gov.co)**

- [ ] **GOV-01.** Para cada insumo de datos.gov.co, `sources.csv` registra el identificador del conjunto en el portal (formato `xxxx-xxxx`), la URL del conjunto y la fecha de la última actualización de los datos.
- [ ] **GOV-02.** La licencia de cada insumo del portal se toma del metadato de ese conjunto; no se supone que todos los conjuntos tienen la misma licencia.
- [ ] **GOV-03.** Un insumo sin licencia declarada no se redistribuye hasta obtener confirmación escrita de la entidad productora.
- [ ] **GOV-04.** Los datos derivados de insumos con licencia CC BY-SA 4.0 se publican bajo CC BY-SA 4.0.
- [ ] **GOV-05.** La atribución de cada insumo incluye la entidad productora, el título del conjunto, la URL del conjunto en el portal y la fecha de consulta.
- [ ] **GOV-06.** La descarga por API usa `$limit` y `$offset` explícitos y verifica que el número de filas descargadas es igual al conteo de la fuente.
- [ ] **GOV-07.** Cada descarga se conserva en `data/raw/` con su suma de verificación SHA-256 y la fecha de descarga; si el conjunto es demasiado grande para conservarlo, se conservan el extracto filtrado y la consulta que lo produjo.
- [ ] **GOV-08.** Antes de publicar datos derivados de insumos de entidades públicas se verificó que no contienen información pública clasificada o reservada ni datos personales, y se consultó el índice de información clasificada y reservada de la entidad.
- [ ] **GOV-09.** Si el insumo pertenece a una serie fragmentada por periodos o por versiones, el cuaderno documenta las diferencias de columnas, de licencia y de cobertura entre las partes.
- [ ] **GOV-10.** Si el insumo es un subconjunto territorial de un conjunto nacional, el cuaderno cita el conjunto nacional y registra el filtro aplicado.
- [ ] **GOV-11.** *(Recomendado)* Los metadatos de cada insumo se obtienen de la API (`/api/views/<id>.json`) o del catálogo (`/data.json`) y se guardan junto con la descarga.
- [ ] **GOV-12.** *(Recomendado)* Los datos derivados que se publiquen además en datos.gov.co cumplen los criterios de validación del portal: formato abierto y estructurado, diccionario de datos claro y completo, ausencia de información sensible y campos normalizados.

**2.13. Insumos con condiciones propias: EM-DAT**

- [ ] **EMD-01.** **Crítico.** Si el cuaderno usa EM-DAT, quien lo usa es una entidad no comercial y el uso no tiene fines de lucro.
- [ ] **EMD-02.** EM-DAT se cita con el año de acceso, la sigla EM-DAT con el producto usado y la URL o el DOI.
- [ ] **EMD-03.** **Crítico.** El repositorio no contiene los datos de EM-DAT ni una parte sustancial de ellos; contiene el script de descarga.
- [ ] **EMD-04.** Si el análisis une registros de EM-DAT con otra base de datos, el repositorio guarda la autorización escrita de CRED.
- [ ] **EMD-05.** *(Recomendado)* Los análisis de tendencia no incluyen registros de EM-DAT anteriores al año 2000.
- [ ] **EMD-06.** Las celdas vacías de EM-DAT no se reemplazan por cero.
- [ ] **EMD-07.** *(Recomendado)* Se usa el EM-DAT Archive en lugar de la base viva.

## 4. Prompt para validar los requisitos para datos

Este prompt convierte la lista de verificación en una auditoría repetible. Lee el repositorio de un cuaderno, ejecuta comprobaciones automáticas y genera un **reporte de cumplimiento y calidad** en Markdown y JSON. Funciona con cualquier asistente de IA que pueda leer archivos y ejecutar comandos.

**Procedimiento de uso**

1. Copie el prompt completo y reemplace los valores entre `<>` de la sección ENTRADAS.
2. Instale `check-jsonschema` (Tabla 1) y ejecute el prompt desde un entorno con acceso a los archivos del repositorio. Para comprobar DOI, use el modo `con_red`.
3. Revise el reporte con una persona. Un asistente de IA puede equivocarse al leer un archivo o al interpretar una cláusula. El resultado es un apoyo a la revisión y no una certificación, y todo lo marcado «Requiere revisión humana» lo decide una persona.
4. Guarde el reporte en `metadata/` y repita la auditoría antes de cada *release*.

:::{warning} Límites del prompt
El prompt no sustituye la consulta con las comunidades (Sección 2.5), no certifica la corrección jurídica de una licencia y no evalúa el mérito científico del cuaderno. Si se usa un servicio de IA externo, no se le deben entregar datos personales, datos de comunidades ni datos con restricciones de licencia. Véanse los [requisitos para el uso de IA](05-uso-de-ia.md).
:::

````text
Actúa como auditor de datos de la Subdirección para el Conocimiento del Riesgo (UNGRD). Tu tarea es VALIDAR si el repositorio de un cuaderno reproducible cumple los «Requisitos para datos» y producir un REPORTE DE CUMPLIMIENTO Y CALIDAD. Eres un revisor, no un autor: NO modifiques ningún archivo del cuaderno.

## ENTRADAS
- RUTA_REPO: <ruta local del repositorio del cuaderno>
- MODO: "estatico" (solo leer archivos) o "con_red" (además puedes comprobar DOI y URL). Si no lo indico, usa "estatico".
- CONTEXTO (opcional): tipo de datos (amenaza, exposición, vulnerabilidad, pérdidas); si hay datos sobre personas o comunidades; si el cuaderno usa EM-DAT.
- SALIDA: carpeta donde escribir `reporte_estandar_datos.md` y `reporte_estandar_datos.json`. Si no la indico, imprime el reporte en la conversación.

## REGLAS DE CONDUCTA (obligatorias)
1. Toda afirmación cita su evidencia: ruta del archivo y línea, campo del RDLS, o salida de un comando. Sin evidencia, el estado es «No verificable».
2. No inventes. Si no puedes comprobar algo (por ejemplo, un DOI en modo estático), el estado es «No verificable» y explicas qué faltó. Nunca supongas que algo cumple.
3. Distingue «No aplica» (el requisito no corresponde a este cuaderno; explica la razón) de «No cumple» (corresponde y falta).
4. Solo lectura. No ejecutes código del cuaderno que no hayas leído completo. No envíes datos ni rutas a servicios externos. No abras ni copies valores de columnas que parezcan datos personales: reporta solo los nombres de las columnas.
5. Las decisiones éticas y legales (consentimiento, datos de comunidades, interpretación de una licencia) no son tuyas: márcalas «Requiere revisión humana» y describe la duda.
6. No evalúes el mérito científico del cuaderno. Evalúa datos, metadatos, licencias, citación y documentación.
7. No propongas ninguna acción que implique un pago (suscripciones, licencias o servicios de pago). Si una acción correctiva solo es posible con un pago, repórtalo como incumplimiento del requisito INV-04.

## PROCEDIMIENTO
### Paso A. Inventario
Lista los archivos de `data/`, `metadata/`, `scripts/` y la raíz. Identifica `sources.csv`, `data_catalog.csv`, `metadata/rdls/*.json`, `DATA_STATEMENT.md`, `CITATION.cff`, `LICENSE`, `environment.yml` o `requirements.txt`, y `CHANGELOG.md`. Anota los que faltan.

### Paso B. Comprobaciones automáticas (ejecuta las que apliquen y conserva la salida)
1. RDLS: valida cada `metadata/rdls/*.json` con `check-jsonschema --schemafile https://docs.riskdatalibrary.org/en/1__0__0/rdls_schema.json <archivo>`. Si no hay red, usa una copia local del esquema si existe; si no, «No verificable». Confirma que están los diez campos obligatorios: id, title, description, risk_data_type, publisher, contact_point, creator, spatial, license, resources.
2. Cobertura: cada archivo de `data/processed/` debe aparecer en algún `resources` del RDLS, y cada recurso del RDLS debe corresponder a un archivo o a una URL. Reporta archivos huérfanos y recursos sin archivo.
3. `sources.csv`: columnas nombre, entidad, identificador_fuente, url_o_doi, version_o_consulta, metodo_extraccion, formato, resolucion_espacial, resolucion_temporal, variables, fecha_actualizacion_fuente, fecha_descarga, licencia, restricciones_de_uso. Reporta celdas vacías, URL que son solo páginas de inicio y fechas que no sean AAAA-MM-DD.
4. Formatos: señala `.xlsx` y `.shp` cuando son el único formato de un dato. Verifica que los CSV estén en UTF-8.
5. Fechas y países: columnas de fecha en AAAA-MM-DD; códigos de país ISO 3166-1 alfa-3.
6. Licencias: lee `LICENSE`, el campo `license` del RDLS y la columna `licencia` de `sources.csv`. Marca cláusulas NC, SA o ND, y datos de terceros copiados al repositorio.
7. Costo: revisa si algún insumo, herramienta o servicio exige pago, suscripción o licencia comercial.
8. DOI y enlaces (solo modo "con_red"): comprueba con una petición HEAD que cada DOI de `id`, `CITATION.cff` y `DATA_STATEMENT.md` resuelve, y que el DOI del concepto y el de la versión no estén confundidos. Comprueba que el archivo se descarga por HTTPS desde la página del DOI.
9. `CITATION.cff`: estructura válida y ORCID con formato 0000-0000-0000-0000 para cada persona autora.
10. Datos personales: busca nombres de columna como nombre, cédula, documento, dirección, teléfono, correo y coordenadas de viviendas. Reporta solo los nombres y el archivo.
11. Calidad de los datos (si son grandes, toma una muestra y dilo): porcentaje de valores faltantes por columna, filas duplicadas, valores fuera de rango o imposibles, unidades inconsistentes, sistema de coordenadas declarado, y coherencia entre la cobertura temporal y espacial declarada en el RDLS y la observada en los datos.
12. Diccionario de variables: cada columna publicada está descrita con tipo y unidad.
13. Insumos de datos.gov.co (solo si el cuaderno los usa): comprueba que cada insumo tiene identificador con formato `xxxx-xxxx`; que la licencia registrada coincide con el campo `licenseId` de `https://www.datos.gov.co/api/views/<id>.json` (solo en modo "con_red"); que el código de descarga usa `$limit` y `$offset` explícitos y compara las filas descargadas con el conteo de la fuente; que existe la suma de verificación SHA-256; que los códigos DIVIPOLA son texto de dos (departamento) o cinco (municipio) caracteres; y que las columnas numéricas y de coordenadas no usan `0`, `-1`, `9999` ni `NA` como marcador de valor faltante.
14. EM-DAT (solo si el cuaderno lo usa): confirma que `data/` no contiene archivos de EM-DAT, que `sources.csv` registra versión y fecha de acceso, y que no hay análisis de tendencia con registros anteriores a 2000.

### Paso C. Evaluación de requisitos
Evalúa los 92 requisitos de abajo (80 obligatorios y 12 recomendados). A cada uno asígnale exactamente un estado: Cumple, Parcial, No cumple, No aplica o No verificable. Los marcados (CRÍTICO) son compuertas bloqueantes.

### 2.1. Inventario y selección de insumos
INV-01. Cada insumo (dato de entrada) figura en metadata/sources.csv con las columnas de la Tabla 3.
INV-02. La URL o el DOI de cada insumo apunta al archivo o al registro exacto, no a la página de inicio de la fuente.
INV-03. Si el insumo se actualiza de forma continua, sources.csv registra la versión o, en su defecto, los parámetros de la consulta (incluido cualquier filtro territorial o temporal) y la fecha de descarga.
INV-04 (CRÍTICO). Todo insumo puede obtenerse sin pago: ninguno exige suscripción ni licencia de pago para el uso que hace el cuaderno.
INV-05 (CRÍTICO). Los datos de terceros se copian al repositorio solo si su licencia o sus términos de uso permiten redistribuirlos; en caso contrario, el repositorio contiene el script de descarga y la cita.
INV-06 (CRÍTICO). Los términos de uso de cada insumo se leyeron completos y sus restricciones (redistribución, combinación con otras bases de datos, cita exigida) están registradas en sources.csv.
INV-07. Si el insumo es una compilación de fuentes, cada registro lleva su fuente (DOI, URL o equivalente) y ningún registro se marca como «sin publicar» sin fuente.
INV-08 (RECOMENDADO). Cuando el insumo tiene una versión archivada y citable, se usa esa versión y no la versión viva.

### 2.2. Estructura de archivos y formatos
EST-01. Los datos están en data/raw, data/interim y data/processed; raw contiene los originales sin modificar o el script que los descarga.
EST-02. Los datos publicados tienen formatos abiertos, no propietarios y procesables por máquina (Tabla 4). Los insumos pueden conservar el formato de la fuente.
EST-03. Los datos se entregan completos y en bloque, no solo como visualización.
EST-04. Cada tabla tiene un diccionario de variables con nombre, descripción, tipo, unidad y valores permitidos.
EST-05. Cada recurso declara el sistema de coordenadas (código EPSG), la resolución espacial y la resolución temporal.
EST-06. Las fechas tienen el formato AAAA-MM-DD y los países se identifican con los códigos ISO 3166-1 alfa-3 de la lista country del RDLS.
EST-07. metadata/data_catalog.csv lista cada archivo publicado con su descripción, formato, tamaño y licencia.
EST-08 (RECOMENDADO). Los nombres de archivo no tienen espacios ni tildes.
EST-09. Los departamentos y municipios se identifican con el código DIVIPOLA del DANE, almacenado como texto con ceros a la izquierda: dos caracteres para departamentos (por ejemplo, 05) y cinco para municipios (por ejemplo, 05001).
EST-10. Los valores numéricos usan el punto como separador decimal y no incluyen separador de miles ni texto.
EST-11. Si el conjunto clasifica amenazas o eventos, usa los códigos HIPs 2025 y registra la equivalencia con la clasificación de la fuente (aplica solo si el conjunto clasifica amenazas).
EST-12 (RECOMENDADO). Los indicadores de daños y pérdidas se definen según los indicadores del Marco de Sendai cuando existe uno equivalente.

### 2.3. Metadatos con el Risk Data Library Standard
MET-01. Existe un archivo metadata/rdls/<nombre>.json por cada conjunto de datos publicado.
MET-02. Cada archivo incluye los diez campos obligatorios del esquema (Tabla 5).
MET-03 (CRÍTICO). Cada archivo valida sin errores contra el esquema canónico del RDLS 1.0.0.
MET-04. Los campos con lista de códigos usan los códigos del RDLS sin traducirlos (por ejemplo, license usa la URL de la lista de licencias). Si no existe un código adecuado y la lista es cerrada, se abrió un *issue* en el repositorio del RDLS; si la lista es abierta, se usa un código nuevo y se propone en un *issue*.
MET-05. El campo id contiene el DOI del conjunto de datos como URL (https://doi.org/...).
MET-06. El campo lineage describe la procedencia: insumos (en lineage.sources), transformaciones y software.
MET-07. Por cada valor de risk_data_type existe el componente correspondiente (hazard, exposure, vulnerability o loss).
MET-08 (RECOMENDADO). Se completan los campos opcionales temporal, spatial_resolution, temporal_resolution, attributions, referenced_by y version.

### 2.5. Datos sobre personas y comunidades
PER-01. Se aplicó la prueba de la Tabla 8 (principios CARE) y su resultado está registrado en DATA_STATEMENT.md.
PER-02 (CRÍTICO). No se publican datos personales ni datos de pueblos o comunidades sin una constancia de autorización registrada en DATA_STATEMENT.md.
PER-03. Los datos sobre personas siguen una de las dos rutas de la Tabla 9: abierta o de acceso controlado.
PER-04. Antes de publicar se evaluó el riesgo de reidentificación por identificadores indirectos (ubicación, género, ocupación, características de salud).
PER-05. Cuando el acceso es restringido, los metadatos son públicos y se indica cómo solicitar el acceso.
PER-06. Los datos de redes sociales no se indexan ni se republican sin consentimiento.
PER-07 (RECOMENDADO). La resolución espacial se agrega o se reduce hasta que el dato no permita identificar personas o viviendas, y la transformación se documenta en lineage.

### 2.6. Licencias
LIC-01 (CRÍTICO). Existen un archivo LICENSE y un campo license del RDLS con una licencia explícita.
LIC-02 (CRÍTICO). Los datos publicados usan CC0 o CC BY (o equivalentes) y no tienen cláusulas -SA ni -NC, salvo que sean datos secundarios que deban conservar las condiciones de la fuente (por ejemplo, CC BY-SA 4.0 cuando el insumo tiene esa licencia).
LIC-03. No se publica como conjunto nuevo ningún dato derivado de una fuente con licencia -ND.
LIC-04. Los datos, el código y el texto declaran su licencia por separado, y el código usa Apache-2.0 o MIT.
LIC-05. La licencia de los datos es una licencia estándar reconocida, no un texto redactado para el caso.

### 2.7. Depósito, identificadores y citación
DEP-01 (CRÍTICO). Los datos publicados están en un repositorio que garantiza preservación a largo plazo, identificador persistente (DOI) y descarga directa por HTTPS desde la página del DOI.
DEP-02. Ningún dato publicado reside únicamente en un sitio personal, en un sitio institucional informal o en una nube informal.
DEP-03 (CRÍTICO). Cada conjunto de datos publicado tiene un DOI.
DEP-04. Cada versión de un conjunto de datos tiene un solo DOI declarado, y el DOI del concepto se distingue del DOI de la versión.
DEP-05. Los datos se descargan por HTTPS sin registro y sin pago.
DEP-06. Cada persona autora tiene ORCID y lo declara en CITATION.cff.
DEP-07. Los datos de entrada y los derivados se citan en el texto y en la lista de referencias con DOI en formato URL, autores y título tal como figuran en el repositorio, nombre del repositorio y año.
DEP-08. Si el conjunto de datos ya se publicó junto con un artículo, se citan ambos.
DEP-09. Existe DATA_STATEMENT.md con la declaración de disponibilidad de datos (Sección 2.8).
DEP-10. Existe una declaración de disponibilidad de código, incluso cuando no hay código propio.
DEP-11. Se creó un *release* en GitHub antes de archivar el repositorio en el depósito.

### 2.9. Calidad mínima de los datos publicados
CAL-01. El título y la descripción de cada conjunto están completos y no usan siglas ni caracteres especiales sin definirlos.
CAL-02. Ninguna columna publicada carece de nombre ni tiene un nombre ambiguo.
CAL-03. Los valores faltantes se dejan vacíos y se documentan en el diccionario de variables; no se codifican con un valor (por ejemplo, 0) que pueda confundirse con un dato.
CAL-04. El conjunto no contiene filas duplicadas.
CAL-05. El tipo de dato de cada columna corresponde a su contenido: las fechas son fechas, los números son números y los códigos son texto.
CAL-06. Los datos se publican con el mayor nivel de detalle disponible; los totales y los resúmenes se publican en un archivo aparte.
CAL-07. Los datos de varios periodos con la misma estructura se publican en un solo conjunto con una columna de periodo o de fecha, no en archivos separados por año.
CAL-08. Si el conjunto incluye direcciones o localizaciones textuales, incluye también columnas numéricas de latitud y longitud en grados decimales, con el sistema de referencia declarado (EST-05).
CAL-09. El conjunto declara su frecuencia de actualización y se actualiza conforme a ella, o declara que es una versión final sin actualizaciones previstas.
CAL-10 (RECOMENDADO). El conjunto tiene al menos 50 registros y 5 columnas; si tiene menos, la descripción explica la razón.
CAL-11. La descripción y el diccionario permiten interpretar el conjunto sin contexto adicional.

### 2.10. Validación técnica y limitaciones
VAL-01. El cuaderno describe las comprobaciones de calidad realizadas sobre los datos.
VAL-02. Las limitaciones se presentan en dos grupos: las introducidas por el procesamiento y las heredadas de las fuentes.
VAL-03. Cada limitación se cuantifica cuando es posible (porcentaje de valores faltantes, de coincidencias, error estimado).
VAL-04. Los sesgos conocidos de cada insumo se declaran y se respetan en el análisis.
VAL-05. La descripción de los datos se limita a su contenido técnico; si incluye un resumen de resultados, no excede un párrafo y dos figuras o tablas.
VAL-06 (RECOMENDADO). Los datos tienen pruebas automáticas en scripts/ (por ejemplo, con pandera).

### 2.11. Preservación y versionado
PRE-01. Cada cambio sustantivo de los datos genera una versión nueva con su propio DOI, y la versión publicada no se modifica salvo para corregirla.
PRE-02. Existe el compromiso escrito de conservar los datos al menos cinco años después de la publicación.
PRE-03. El campo contact_point identifica a una persona o dependencia que responde a los correos.
PRE-04. Existe un CHANGELOG.md de los datos que registra las correcciones.
PRE-05 (RECOMENDADO). Cada tres meses se comprueba que las URL de los insumos siguen activas.

### 2.12. Insumos del Portal Nacional de Datos Abiertos (datos.gov.co) (aplica solo si el cuaderno usa insumos de datos.gov.co; si no, «No aplica»)
GOV-01. Para cada insumo de datos.gov.co, sources.csv registra el identificador del conjunto en el portal (formato xxxx-xxxx), la URL del conjunto y la fecha de la última actualización de los datos.
GOV-02. La licencia de cada insumo del portal se toma del metadato de ese conjunto; no se supone que todos los conjuntos tienen la misma licencia.
GOV-03. Un insumo sin licencia declarada no se redistribuye hasta obtener confirmación escrita de la entidad productora.
GOV-04. Los datos derivados de insumos con licencia CC BY-SA 4.0 se publican bajo CC BY-SA 4.0.
GOV-05. La atribución de cada insumo incluye la entidad productora, el título del conjunto, la URL del conjunto en el portal y la fecha de consulta.
GOV-06. La descarga por API usa $limit y $offset explícitos y verifica que el número de filas descargadas es igual al conteo de la fuente.
GOV-07. Cada descarga se conserva en data/raw/ con su suma de verificación SHA-256 y la fecha de descarga; si el conjunto es demasiado grande para conservarlo, se conservan el extracto filtrado y la consulta que lo produjo.
GOV-08. Antes de publicar datos derivados de insumos de entidades públicas se verificó que no contienen información pública clasificada o reservada ni datos personales, y se consultó el índice de información clasificada y reservada de la entidad.
GOV-09. Si el insumo pertenece a una serie fragmentada por periodos o por versiones, el cuaderno documenta las diferencias de columnas, de licencia y de cobertura entre las partes.
GOV-10. Si el insumo es un subconjunto territorial de un conjunto nacional, el cuaderno cita el conjunto nacional y registra el filtro aplicado.
GOV-11 (RECOMENDADO). Los metadatos de cada insumo se obtienen de la API (/api/views/<id>.json) o del catálogo (/data.json) y se guardan junto con la descarga.
GOV-12 (RECOMENDADO). Los datos derivados que se publiquen además en datos.gov.co cumplen los criterios de validación del portal: formato abierto y estructurado, diccionario de datos claro y completo, ausencia de información sensible y campos normalizados.

### 2.13. Insumos con condiciones propias: EM-DAT (aplica solo si el cuaderno usa EM-DAT; si no, «No aplica»)
EMD-01 (CRÍTICO). Si el cuaderno usa EM-DAT, quien lo usa es una entidad no comercial y el uso no tiene fines de lucro.
EMD-02. EM-DAT se cita con el año de acceso, la sigla EM-DAT con el producto usado y la URL o el DOI.
EMD-03 (CRÍTICO). El repositorio no contiene los datos de EM-DAT ni una parte sustancial de ellos; contiene el script de descarga.
EMD-04. Si el análisis une registros de EM-DAT con otra base de datos, el repositorio guarda la autorización escrita de CRED.
EMD-05 (RECOMENDADO). Los análisis de tendencia no incluyen registros de EM-DAT anteriores al año 2000.
EMD-06. Las celdas vacías de EM-DAT no se reemplazan por cero.
EMD-07 (RECOMENDADO). Se usa el EM-DAT Archive en lugar de la base viva.

### Paso D. Puntuación
- Cumple = 1, Parcial = 0,5, No cumple = 0. «No aplica» y «No verificable» no entran en el denominador, pero se reportan con su conteo.
- Puntaje de cumplimiento obligatorio = suma de puntos de los requisitos obligatorios evaluables ÷ requisitos obligatorios evaluables × 100, con un decimal. Calcúlalo por sección y en total.
- Los requisitos recomendados se reportan aparte, sin entrar en el puntaje.
- Nivel: 90 o más, «Alto»; de 75 a 89,9, «Aceptable»; de 50 a 74,9, «Mejorable»; menos de 50, «Insuficiente».
- Compuertas: si algún requisito CRÍTICO está en «No cumple», el resultado global es «NO APTO PARA PUBLICAR», aunque el puntaje sea alto. Si alguno está en «No verificable», es «PENDIENTE DE VERIFICACIÓN». Lista las compuertas con su estado.

### Paso E. Redacta el reporte con esta estructura exacta
1. **Resumen ejecutivo**: resultado global (compuertas), puntaje y nivel, y las tres prioridades más urgentes, en menos de 150 palabras.
2. **Alcance y método**: ruta auditada, modo, fecha, versión de los requisitos y del esquema RDLS, y qué no se pudo revisar.
3. **Resultados por requisito**: tabla con ID, requisito, estado, evidencia, acción recomendada y prioridad (Alta, Media o Baja).
4. **Puntaje por sección**: tabla con sección, requisitos evaluables, puntos y porcentaje.
5. **Comprobaciones automáticas**: resultado de cada comprobación del Paso B, con la salida relevante resumida.
6. **Calidad de los datos**: hallazgos del punto B.11, con cifras.
7. **Riesgos éticos y legales**: dudas sobre consentimiento, datos de comunidades, licencias y términos de uso de insumos, cada una marcada «Requiere revisión humana».
8. **Plan de mejora**: acciones ordenadas por prioridad, con esfuerzo estimado (S, M o L), el requisito que resuelven y sin costo económico.
9. **Limitaciones de esta auditoría**: lo que no se verificó y por qué.

### Paso F. Versión legible por máquina
Escribe también `reporte_estandar_datos.json` con esta forma:
{"repositorio": "...", "fecha": "AAAA-MM-DD", "modo": "...", "version_estandar": "...", "resultado_global": "...", "puntaje_obligatorios": 0.0, "nivel": "...", "compuertas": [{"id": "XXX-00", "estado": "..."}], "secciones": [{"nombre": "...", "puntaje": 0.0}], "requisitos": [{"id": "XXX-00", "estado": "...", "evidencia": "...", "accion": "...", "prioridad": "..."}], "no_verificables": ["XXX-00"]}

Termina con un resumen de cinco líneas y la ruta de los archivos generados.

````

Si cambia la lista de verificación, el prompt debe actualizarse con los mismos requisitos.

## Referencias

Bantilan, N. (2026). *pandera* (Versión 0.36.0) [Software]. Python Package Index. https://pypi.org/project/pandera/

Butler, H., Daly, M., Doyle, A., Gillies, S., Hagen, S., y Schaub, T. (2016). *The GeoJSON format* (RFC 7946). RFC Editor. https://doi.org/10.17487/RFC7946

Carroll, S. R., Garba, I., Figueroa-Rodríguez, O. L., Holbrook, J., Lovett, R., Materechera, S., Parsons, M., Raseroka, K., Rodriguez-Lonebear, D., Rowe, R., Sara, R., Walker, J. D., Anderson, J., y Hudson, M. (2020). The CARE Principles for Indigenous Data Governance. *Data Science Journal, 19*, Artículo 43. https://doi.org/10.5334/dsj-2020-043

Centre for Research on the Epidemiology of Disasters. (2026). *EM-DAT documentation* (Versión 2026.11) [Documentación en línea]. Université catholique de Louvain. https://doc.emdat.be/

Coalition for Publishing Data in the Earth and Space Sciences. (s. f.). *Commitment statement in the Earth, space, and environmental sciences*. COPDESS. Recuperado el 16 de noviembre de 2026, de https://copdess.org/enabling-fair-data-project/commitment-statement-in-the-earth-space-and-environmental-sciences/

Congreso de la República de Colombia. (2014, 6 de marzo). *Ley 1712 de 2014 por medio de la cual se crea la Ley de Transparencia y del Derecho de Acceso a la Información Pública Nacional y se dictan otras disposiciones* (Diario Oficial 49.084). http://www.secretariasenado.gov.co/senado/basedoc/ley_1712_2014.html

Crowley, J. (2014). *Open Data for Resilience Initiative: Field guide*. World Bank. https://doi.org/10.1596/17840

Delforge, D., Wathelet, V., Below, R., Lanfredi Sofia, C., Tonnelier, M., van Loenhout, J. A. F., y Speybroeck, N. (2026). *The EM-DAT Emergency Events Database Archive* (Versión 2.1) [Conjunto de datos]. Open Data @ UCLouvain. https://doi.org/10.14428/DVN/I0LTPH

Departamento Administrativo Nacional de Estadística. (2025). *DIVIPOLA- Códigos municipios* [Conjunto de datos]. Portal Nacional de Datos Abiertos. https://www.datos.gov.co/d/gdxc-w37w

Global Facility for Disaster Reduction and Recovery. (2026). *Risk Data Library Standard* (Versión 1.0.0) [Estándar de metadatos]. https://docs.riskdatalibrary.org/en/1__0__0/

Global Indigenous Data Alliance. (s. f.). *The CARE Principles for Indigenous Data Governance*. Recuperado el 16 de noviembre de 2026, de https://www.gida-global.org/careprinciples

GO FAIR Foundation. (s. f.). *FAIR principles*. Recuperado el 16 de noviembre de 2026, de https://www.gofair.foundation/fair-principles

Guha-Sapir, D., Scales, S. E., Gans, F., Ndugwa, J., Huang, P., Torres, Á. J. G., Doocy, S., Reichstein, M., Smits, J., Tollefsen, A. F., Urdal, H., Zaitchik, B., y Enenkel, M. (2026). The MERGE dataset: A harmonized global resource for climate disaster impacts and human vulnerability. *Scientific Data, 13*, Artículo 1292. https://doi.org/10.1038/s41597-026-07522-7

Klyne, G., y Newman, C. (2002). *Date and time on the Internet: Timestamps* (RFC 3339). RFC Editor. https://doi.org/10.17487/RFC3339

Marulanda, M. C., Cardona, O. D., y Barbat, A. H. (2010). Revealing the socioeconomic impact of small disasters in Colombia using the DesInventar database. *Disasters, 34*(2), 552–570. https://doi.org/10.1111/j.1467-7717.2009.01143.x

Ministerio de Tecnologías de la Información y las Comunicaciones. (2024). *Guía para el uso y aprovechamiento de Datos Abiertos en Colombia* (Versión 7). https://drive.google.com/file/d/1jiuxTrsXyz_rEtkTpG9MR3qC-yTGUhw_/view

Ministerio de Tecnologías de la Información y las Comunicaciones. (2026a). *Listado de errores frecuentes de calidad de datos abiertos* [Conjunto de datos]. Portal Nacional de Datos Abiertos. https://www.datos.gov.co/d/xbc7-65j4

Ministerio de Tecnologías de la Información y las Comunicaciones. (2026b). *Portal Nacional de Datos Abiertos: catálogo de conjuntos de datos* [Archivo data.json]. Recuperado el 16 de noviembre de 2026, de https://www.datos.gov.co/data.json

Ministerio de Tecnologías de la Información y las Comunicaciones. (2026c). *¿Tú primera vez con Datos Abiertos? Aquí te contamos por dónde empezar - 2026* [Historia]. Portal Nacional de Datos Abiertos. https://www.datos.gov.co/stories/s/nc93-tzp2

Naciones Unidas. (2015). *Marco de Sendai para la Reducción del Riesgo de Desastres 2015-2030*. Oficina de las Naciones Unidas para la Reducción del Riesgo de Desastres. https://www.undrr.org/publication/sendai-framework-disaster-risk-reduction-2015-2030

Rosen, S. (2026). *check-jsonschema* (Versión 0.39.0) [Software]. Python Package Index. https://pypi.org/project/check-jsonschema/

Scientific Data. (s. f.-a). *Data policies*. Springer Nature. Recuperado el 16 de noviembre de 2026, de https://www.nature.com/sdata/policies/data-policies

Scientific Data. (s. f.-b). *Data repository guidance*. Springer Nature. Recuperado el 16 de noviembre de 2026, de https://www.nature.com/sdata/policies/repositories

Scientific Data. (s. f.-c). *Submission guidelines*. Springer Nature. Recuperado el 16 de noviembre de 2026, de https://www.nature.com/sdata/publish/submission-guidelines

Shafranovich, Y. (2005). *Common format and MIME type for comma-separated values (CSV) files* (RFC 4180). RFC Editor. https://doi.org/10.17487/RFC4180

Socrata. (s. f.-a). *Application tokens*. Recuperado el 16 de noviembre de 2026, de https://dev.socrata.com/docs/app-tokens.html

Socrata. (s. f.-b). *The LIMIT clause*. Recuperado el 16 de noviembre de 2026, de https://dev.socrata.com/docs/queries/limit.html

Unidad Nacional para la Gestión del Riesgo de Desastres. (2026). *Emergencias UNGRD V2* [Conjunto de datos]. Portal Nacional de Datos Abiertos. https://www.datos.gov.co/d/2343-nuqp

Université catholique de Louvain. (2025). *EM-DAT attribution and citation policy*. https://doc.emdat.be/docs/legal/citation-policy/

Université catholique de Louvain. (2026). *EM-DAT database license agreement* (Versión del 16 de noviembre de 2026). https://doc.emdat.be/docs/legal/database-license-agreement/

United Nations Office for Disaster Risk Reduction y International Science Council. (2025). *Hazard Information Profiles (HIPs): 2025 version*. https://www.undrr.org/publication/documents-and-publications/hazard-information-profiles-hips-2025-version

Wilkinson, M. D., Dumontier, M., Aalbersberg, I. J., Appleton, G., Axton, M., Baak, A., Blomberg, N., Boiten, J.-W., da Silva Santos, L. B., Bourne, P. E., Bouwman, J., Brookes, A. J., Clark, T., Crosas, M., Dillo, I., Dumon, O., Edmunds, S., Evelo, C. T., Finkers, R., . . . Mons, B. (2016). The FAIR Guiding Principles for scientific data management and stewardship. *Scientific Data, 3*, Artículo 160018. https://doi.org/10.1038/sdata.2016.18

Zenodo. (s. f.). *General policies* (v1.0). CERN. Recuperado el 16 de noviembre de 2026, de https://about.zenodo.org/policies/
