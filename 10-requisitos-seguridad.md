---
title: Requisitos de seguridad
subtitle: Requisitos de seguridad y privacidad del repositorio de un cuaderno reproducible, sobre secretos, datos personales, código no confiable, dependencias, automatización y publicación
date: 2026-11-19
authors:
  - name: Subdirección para el Conocimiento del Riesgo
    affiliation: Unidad Nacional para la Gestión del Riesgo de Desastres (UNGRD)
    github: scr-ungrd
license: CC-BY-4.0
keywords:
  - seguridad
  - secretos
  - privacidad
  - cadena de suministro
  - GitHub Actions
  - reproducibilidad
  - ciencia abierta
  - riesgo de desastres
abbreviations:
  UNGRD: Unidad Nacional para la Gestión del Riesgo de Desastres
  SCR: Subdirección para el Conocimiento del Riesgo
  API: interfaz de programación de aplicaciones
  CI: integración continua
  DOI: Digital Object Identifier
  GPS: Global Positioning System
  OWASP: Open Worldwide Application Security Project
---

+++ {"part": "abstract"}

Este documento establece los requisitos de seguridad y privacidad que debe cumplir el repositorio de un cuaderno reproducible de la colección, sea o no un tablero, una aplicación o un modelo. Define 36 requisitos (32 obligatorios, de ellos 5 críticos, y 4 recomendados), cada uno con un identificador y una base documental citada. Cubren los secretos y las credenciales, los datos personales y las rutas locales, la ejecución de código no confiable, las dependencias, la automatización (GitHub Actions, Binder y Colab) y la publicación de versiones en Zenodo. Se apoyan en la documentación de GitHub, en la lista OWASP Top 10:2025 y en la de Zenodo. Ningún requisito exige pagos. El documento incluye una lista de verificación y un prompt que audita el cumplimiento y genera un reporte.

+++

## 1. Alcance y convenciones

### 1.1 Alcance

Estas instrucciones se aplican a **todo repositorio** que se envíe a la colección. Un cuaderno es código que otra persona va a ejecutar y un repositorio público que se archiva con un DOI, y esos dos hechos crean riesgos que ninguno de los otros requisitos de la colección cubría para el cuaderno en sí: una clave olvidada en el historial, una ruta con el nombre de usuario dentro de una salida guardada, un `%pip install` desde una dirección desconocida o un archivo ejecutable dentro de los datos.

Se distinguen los requisitos así:

- **Seguridad del repositorio** (este documento): lo que es común a cualquier cuaderno.
- **[Requisitos de datos](03-estandar-de-datos.md)**: licencias, metadatos y datos personales de los conjuntos de datos.
- **[Requisitos de tableros](06-estandar-tableros.md)** y **[de aplicaciones](07-estandar-aplicaciones.md)**: lo específico de un sitio o de un servicio que se despliega. Los requisitos de secretos de una aplicación (`SEG-01` de aplicaciones) y de un modelo de lenguaje (`SEG-05` de uso de LLMs) son casos particulares de `CRE-01` a `CRE-03`.
- **[Requisitos de uso de IA](05-uso-de-ia.md)** y **[de uso de LLMs](09-uso-de-llms.md)**: la responsabilidad por el uso de asistentes y la cadena de suministro de modelos preentrenados.

Estos requisitos no sustituyen una auditoría de seguridad profesional. Un cuaderno de análisis tiene una superficie de ataque pequeña, y los requisitos se limitan a lo que una persona científica puede cumplir y comprobar con herramientas gratuitas.

### 1.2 Convenciones

1. **Identificador.** Cada requisito tiene un código de tres letras y dos cifras (por ejemplo, CRE-01). Los códigos se usan en la lista de verificación, en el prompt de validación y en los reportes.
2. **Nivel.** *Obligatorio* significa que el cuaderno no se acepta si el requisito aplica y no se cumple. *Recomendado* significa que el cumplimiento mejora la calidad pero no condiciona la aceptación. *Crítico* es un requisito obligatorio cuyo incumplimiento bloquea la publicación, cualquiera sea la puntuación total.
3. **Base.** Entre paréntesis, cada requisito indica el documento, el año y, cuando corresponde, el criterio o el apartado del que procede. Los requisitos cuya base es «Requisito de esta guía» los establece este documento y no provienen de una fuente externa.
4. **Redacción.** Cada requisito se enuncia en el estado conforme: describe cómo es un repositorio que lo cumple. Los requisitos que dicen «aplica solo» se marcan «No aplica» cuando no corresponden.
5. **Citas y traducciones.** Las citas siguen la norma APA 7. Los textos de las fuentes en inglés se traducen al español; las traducciones son propias. Los nombres de parámetros, archivos y herramientas se conservan en su idioma original.
6. **Fecha de consulta.** Las fuentes web sin fecha de publicación se consultaron el 19 de noviembre de 2026 (véanse las Referencias). Las plataformas y las herramientas cambian: antes de publicar, confirme la versión vigente.

### 1.3 Política de costo cero

Ningún requisito de este documento exige comprar herramientas ni servicios. El escaneo de secretos de GitHub corre gratis en los repositorios públicos (GitHub, s. f.-b), `gitleaks` tiene licencia MIT (Gitleaks, s. f.) y `pip-audit` tiene licencia Apache 2.0 (Python Packaging Authority, s. f.).

### 1.4 Documentos de referencia

**Tabla 1.** Documentos de los que se derivan los requisitos.

```{list-table}
:header-rows: 1

* - Documento
  - Qué establece
  - Requisitos que se derivan
* - GitHub (s. f.-b). Secret scanning
  - Búsqueda de credenciales en todo el historial y en todas las ramas, gratis en repositorios públicos; rotar la credencial expuesta
  - CRE-02, CRE-05, CRE-07, REL-04
* - GitHub (s. f.-c). Secure use reference
  - Permisos mínimos de `GITHUB_TOKEN`, acciones fijadas por hash, inyección de scripts, disparadores privilegiados y manejo de secretos
  - CRE-06, FLU-01 a FLU-05
* - GitHub (s. f.-a, s. f.-d). Política de seguridad y correo de los commits
  - `SECURITY.md`; la dirección de un commit es visible y cambiarla no reescribe el historial
  - REL-03, FUG-04
* - OWASP Foundation (2025). OWASP Top 10:2025
  - Configuración insegura (A02), fallos de la cadena de suministro (A03) y de integridad de software y datos (A08)
  - CRE-01, CRE-04, EJC-01, EJC-03, EJC-05, EJC-06, DEP-01 a DEP-03
* - Python Software Foundation (s. f.). `pickle`; Python Packaging Authority (s. f.). `pip-audit`; Gitleaks (s. f.)
  - Riesgo de deserializar datos no confiables; auditoría de vulnerabilidades y escaneo de secretos con herramientas gratuitas
  - EJC-03, DEP-03, CRE-07
* - Zenodo (s. f.). Manage records
  - Un registro publicado se puede borrar en 30 días; después, solo con justificación, y queda una página de memoria con la cita
  - REL-01, REL-04
* - [Requisitos de datos](03-estandar-de-datos.md), [de uso de IA](05-uso-de-ia.md), [de tableros](06-estandar-tableros.md) y [de aplicaciones](07-estandar-aplicaciones.md)
  - Datos personales, dependencias sugeridas por IA, alertas de dependencias y secretos que estos requisitos generalizan
  - FUG-01, DEP-02, DEP-04, CRE-04
```

## 2. Requisitos

### 2.1 Credenciales y secretos

Un secreto publicado debe darse por comprometido, porque cualquiera puede leerlo y copiarlo. El escaneo de secretos de GitHub revisa todo el historial de git en todas las ramas, además de los issues y los *pull requests*, y en repositorios públicos corre gratis (GitHub, s. f.-b). Por eso el requisito no es solo que el archivo actual esté limpio: el historial, las ramas, las etiquetas y las salidas guardadas del cuaderno también lo están (CRE-02 y CRE-03).

:::{important} CRE-05: revocar, no solo borrar
Si una clave se expuso, rótela o revóquela en el proveedor. GitHub indica que rotar la credencial es lo inmediato y que limpiar el historial es lento y, a menudo, innecesario cuando ya se revocó (GitHub, s. f.-b). Borrar el archivo o reescribir el historial no deshace una exposición.
:::

Lea las credenciales de variables de entorno, deje un `.env.example` sin valores y excluya `.env` en `.gitignore` (CRE-04). Dé a cada token solo los permisos que la tarea necesita (CRE-06; GitHub, s. f.-c). Para comprobarlo con herramientas gratuitas, use el escaneo de GitHub o `gitleaks`: `gitleaks dir` revisa los archivos y `gitleaks git` el historial (Gitleaks, s. f.). Su README indica que la herramienta está completa y solo recibe parches de seguridad, así que conviene combinarla con el escaneo de GitHub.

*Requisitos de este grupo: CRE-01, CRE-02, CRE-03, CRE-04, CRE-05, CRE-06, CRE-07. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.2 Datos personales y rutas locales

La información personal se filtra por rutas poco evidentes. Las más frecuentes son:

- **Las salidas guardadas.** Una traza de error o un `print` de una variable del entorno puede dejar `/Users/<nombre>` o el nombre de la máquina dentro del `.ipynb` y, de ahí, en el sitio publicado. Ejecute el cuaderno en un entorno limpio antes de guardar las salidas (FUG-02).
- **El historial de git.** La dirección de correo de cada commit queda visible, y cambiarla no reescribe los commits anteriores (GitHub, s. f.-d). Configure una dirección institucional o la *noreply* de GitHub antes del primer commit (FUG-04).
- **Los metadatos de los archivos.** Las fotografías pueden incluir coordenadas y los PDF, el nombre del autor y la ruta de origen (FUG-03).

Los datos personales de los conjuntos de datos se rigen por los [requisitos de datos](03-estandar-de-datos.md); aquí se exige que tampoco aparezcan en las salidas, los metadatos ni el historial (FUG-01).

*Requisitos de este grupo: FUG-01, FUG-02, FUG-03, FUG-04, FUG-05, FUG-06. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.3 Ejecución de código no confiable

Quien ejecuta un cuaderno ajeno ejecuta código ajeno. La guía exige que una persona del comité lo ejecute para certificar la reproducibilidad, y esa persona necesita saber qué puede encontrar. Tres reglas lo limitan.

1. **El cuaderno no trae código de fuera.** No hay `curl | bash`, `eval` sobre contenido descargado ni instalaciones desde direcciones sin versión (EJC-01 y EJC-02).
2. **Los datos no ejecutan nada.** La documentación de Python advierte que `pickle` no es seguro y que puede ejecutar código arbitrario al deserializar datos que podrían provenir de una fuente no confiable (Python Software Foundation, s. f.). Use formatos de datos abiertos (EJC-03 y EJC-07), y descargue con HTTPS y una suma de verificación (EJC-06; OWASP Foundation, 2025, A08).
3. **El arranque está a la vista.** Los scripts que se ejecutan al abrir el entorno (`postBuild` y `start` de Binder, `.devcontainer`, ganchos de git) se revisan y se explican (EJC-05). El repositorio no contiene ejecutables ni archivos con macros salvo los declarados (EJC-04).

:::{important} EJC-08: quien verifica aísla el entorno
Antes de ejecutar un cuaderno ajeno, léalo y córralo en un entorno desechable (contenedor, máquina virtual, Binder o Codespace), sin sus credenciales ni acceso a sus carpetas personales. Si encuentra descargas ocultas, código ofuscado o envíos de datos a servidores desconocidos, detenga la verificación y repórtelo al comité.
:::

*Requisitos de este grupo: EJC-01, EJC-02, EJC-03, EJC-04, EJC-05, EJC-06, EJC-07, EJC-08. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.4 Dependencias

Cada paquete es código de terceros que se instala con los privilegios de quien ejecuta el cuaderno. La lista OWASP Top 10:2025 incluye los fallos de la cadena de suministro entre sus riesgos (OWASP Foundation, 2025, A03). Tres medidas bastan para un cuaderno: fijar las versiones (DEP-01), instalar solo de índices oficiales y comprobar que el nombre es el del paquete previsto, en especial si lo sugirió una IA (DEP-02), y auditar el entorno con una herramienta como `pip-audit`, que consulta la base de vulnerabilidades del Python Packaging Authority (DEP-03; Python Packaging Authority, s. f.).

*Requisitos de este grupo: DEP-01, DEP-02, DEP-03, DEP-04. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.5 Automatización: Actions, Binder y Colab

Un flujo de GitHub Actions corre código con acceso al repositorio y, a veces, a secretos. La documentación de GitHub recomienda que `GITHUB_TOKEN` sea de solo lectura por defecto y que cada trabajo eleve solo lo que necesita (FLU-01), que las acciones de terceros se fijen a un hash de commit completo porque una etiqueta puede moverse o borrarse (FLU-02), que se evite `pull_request_target` salvo que sea imprescindible (FLU-03) y que las entradas no confiables pasen por variables de entorno intermedias y no directamente a un paso `run:` (FLU-04). Los secretos no se guardan en texto plano en los flujos y la ocultación automática en los registros no está garantizada (FLU-05; GitHub, s. f.-c).

*Requisitos de este grupo: FLU-01, FLU-02, FLU-03, FLU-04, FLU-05, FLU-06. Su enunciado completo está en la lista de verificación de la Sección 3.*

### 2.6 Releases y respuesta a incidentes

Cada *release* de la colección se archiva en Zenodo con un DOI. Un propietario puede borrar un registro dentro de los 30 días posteriores a la publicación; después, Zenodo solo permite el borrado en casos justificados (por ejemplo, la exposición de datos personales) y cualquier borrado deja una página de memoria con la cita. Como alternativas, el propietario puede restringir el acceso a los archivos o subir una versión corregida (Zenodo, s. f.). Por eso el escaneo previo al *release* es un requisito crítico: es más barato que retirar un registro (REL-01).

Tenga un `SECURITY.md` que diga cómo reportar una vulnerabilidad o una filtración (REL-03; GitHub, s. f.-a), y un procedimiento escrito para actuar (REL-04). Use esta plantilla (`SECURITY.md`):

```markdown
# Política de seguridad

## Versiones compatibles
<versión actual y las anteriores que se mantienen>

## Cómo reportar una vulnerabilidad o una filtración
Escriba a <correo institucional> o abra un aviso de seguridad privado en este repositorio.
No publique el detalle en un issue. Respondemos en <plazo>.

## Si se filtra un secreto o un dato personal
1. Revocar o rotar la credencial en el proveedor.
2. Retirar el contenido del repositorio y, si procede, pedir a Zenodo la retirada del registro.
3. Avisar a las personas afectadas.
4. Registrar el incidente en `CHANGELOG.md`.
```

*Requisitos de este grupo: REL-01, REL-02, REL-03, REL-04, REL-05. Su enunciado completo está en la lista de verificación de la Sección 3.*

## 3. Lista de verificación

La lista tiene 36 requisitos: 32 obligatorios y 4 recomendados. Los 5 requisitos **críticos** (CRE-01, CRE-02, FUG-01, EJC-01 y REL-01) bloquean la publicación si no se cumplen.

**Criterio de aceptación.** Un repositorio cumple los requisitos si (1) ningún requisito crítico está en incumplimiento y (2) el puntaje de requisitos obligatorios es de 90 o más, calculado como se indica en el prompt de la Sección 4.

**2.1. Credenciales y secretos**

- [ ] **CRE-01.** **Crítico.** Ningún secreto (clave de API, token, contraseña, clave privada o cadena de conexión) está en los archivos del repositorio. (OWASP Foundation, 2025, A02; Requisito de esta guía)
- [ ] **CRE-02.** **Crítico.** Ningún secreto está en el historial de git, incluidas todas las ramas, las etiquetas y los archivos que se borraron después. (GitHub, s. f.-b; Requisito de esta guía)
- [ ] **CRE-03.** Ningún secreto aparece en las salidas guardadas del cuaderno, en sus metadatos ni en los registros (encabezados HTTP, variables de entorno, trazas de error). (Requisito de esta guía)
- [ ] **CRE-04.** Las credenciales se leen de variables de entorno o de un gestor de secretos; el repositorio incluye un `.env.example` sin valores reales y `.gitignore` excluye `.env` (aplica solo si el cuaderno usa credenciales). (OWASP Foundation, 2025, A02; Requisitos de aplicaciones, REP-04)
- [ ] **CRE-05.** Si un secreto se expuso alguna vez, se revocó o se rotó en el proveedor y el incidente se documentó; borrar el archivo o reescribir el historial no basta. (GitHub, s. f.-b)
- [ ] **CRE-06.** Los tokens y las claves tienen los permisos mínimos que la tarea necesita (aplica solo si el cuaderno usa credenciales). (GitHub, s. f.-c)
- [ ] **CRE-07.** *(Recomendado)* Un escaneo automático de secretos está activo en el repositorio (el de GitHub u otra herramienta, como gitleaks). (GitHub, s. f.-b; Gitleaks, s. f.)

**2.2. Datos personales y rutas locales**

- [ ] **FUG-01.** **Crítico.** Ningún archivo, salida ni metadato publicado contiene datos personales (nombres, cédulas, teléfonos, direcciones, correos privados o coordenadas de viviendas) ni datos de comunidades sin autorización registrada; se exceptúan los datos de autoría que la persona autora decidió hacer públicos. (Requisitos de datos, PER; Carroll et al., 2020)
- [ ] **FUG-02.** El código, las salidas guardadas y los documentos no contienen rutas absolutas del equipo de quien escribe (nombre de usuario, carpetas personales, nombre de la máquina); las rutas son relativas al repositorio. (Guía para publicar, Sección 4; Requisito de esta guía)
- [ ] **FUG-03.** Los metadatos de las imágenes, los PDF y otros archivos publicados (GPS, autoría, equipo, ruta de origen) se revisaron y se eliminaron los que identifican a personas o lugares privados. (Requisito de esta guía)
- [ ] **FUG-04.** Los correos de autoría del historial de git son institucionales, la dirección *noreply* de GitHub o los que la persona autora decidió publicar. (GitHub, s. f.-d)
- [ ] **FUG-05.** `CITATION.cff`, `myst.yml` y el `README` publican solo los contactos que la persona autora autorizó (ORCID, correo institucional). (Requisito de esta guía)
- [ ] **FUG-06.** `.gitignore` excluye cachés, registros, archivos temporales, configuración local del editor y copias de datos crudos que no deben publicarse. (Requisito de esta guía)

**2.3. Ejecución de código no confiable**

- [ ] **EJC-01.** **Crítico.** El cuaderno y los scripts no descargan ni ejecutan código de fuentes no verificadas: no hay `curl | bash`, ni `eval` o `exec` sobre contenido descargado, ni instalaciones desde direcciones URL o repositorios sin versión fijada. (OWASP Foundation, 2025, A03 y A08)
- [ ] **EJC-02.** Las instalaciones dentro del cuaderno (`%pip`, `!pip`, `!conda`, `!apt`) usan versiones fijas y los mismos paquetes que `environment.yml`. (Requisito de esta guía)
- [ ] **EJC-03.** El cuaderno no carga con `pickle`, `allow_pickle=True`, `torch.load` sin restricción ni `yaml.load` inseguro archivos que él mismo no generó. (Python Software Foundation, s. f.; OWASP Foundation, 2025, A08)
- [ ] **EJC-04.** El repositorio no contiene ejecutables, bibliotecas compiladas ni archivos con macros (`.exe`, `.dll`, `.so`, `.dylib`, `.jar`, `.bat`, `.msi`, `.xlsm`, `.docm`), salvo los que se declaran y se explican. (Requisito de esta guía)
- [ ] **EJC-05.** Los scripts de arranque (`postBuild` y `start` de Binder, `.devcontainer`, ganchos de git, `Makefile`) están revisados, se explican en el `README` y no descargan ni ejecutan nada fuera de los paquetes fijados. (OWASP Foundation, 2025, A03)
- [ ] **EJC-06.** Las descargas de datos externos usan HTTPS, citan la fuente y registran una suma de verificación o una versión, que el cuaderno o un script comprueba. (OWASP Foundation, 2025, A08)
- [ ] **EJC-07.** Los datos se distribuyen en formatos que no ejecutan código al abrirse (CSV, GeoJSON, GeoTIFF, NetCDF, Parquet). (Requisito de esta guía)
- [ ] **EJC-08.** Quien evalúa o verifica un cuaderno ajeno lo ejecuta en un entorno aislado y desechable (contenedor, máquina virtual, Binder o Codespace), sin credenciales ni acceso a carpetas personales, y antes lee `environment.yml`, los scripts de arranque y las celdas que ejecutan comandos (aplica solo a quien verifica). (Requisito de esta guía)

**2.4. Dependencias**

- [ ] **DEP-01.** Las dependencias están fijadas con versión exacta en `environment.yml` o `requirements.txt`. (OWASP Foundation, 2025, A03; Guía para publicar, Sección 2)
- [ ] **DEP-02.** Todas las dependencias provienen de índices oficiales (PyPI o conda-forge) y se verificó que el nombre corresponde al paquete previsto; ninguna fue sugerida por una IA sin comprobar que existe. (OWASP Foundation, 2025, A03; Requisitos de uso de IA, U16)
- [ ] **DEP-03.** Un auditor de vulnerabilidades (por ejemplo, `pip-audit`) se ejecutó sobre el entorno y las vulnerabilidades conocidas se corrigieron o se justifican por escrito. (Python Packaging Authority, s. f.; OWASP Foundation, 2025, A03)
- [ ] **DEP-04.** *(Recomendado)* Las alertas automáticas de dependencias (Dependabot o equivalente) están activas. (Requisitos de tableros, SEG-05)

**2.5. Automatización: Actions, Binder y Colab**

- [ ] **FLU-01.** Los flujos de GitHub Actions fijan los permisos de `GITHUB_TOKEN` en solo lectura por defecto y elevan, trabajo por trabajo, solo los que necesitan. (GitHub, s. f.-c)
- [ ] **FLU-02.** Las acciones de terceros están fijadas a un hash de commit completo, no a una etiqueta, que puede moverse o borrarse; las acciones oficiales de GitHub (`actions/*`) pueden fijarse por versión. (GitHub, s. f.-c; Requisito de esta guía)
- [ ] **FLU-03.** Los flujos no usan `pull_request_target` ni `workflow_run` con acceso a secretos para ejecutar código de ramas de terceros. (GitHub, s. f.-c)
- [ ] **FLU-04.** Los flujos no insertan entradas no confiables (títulos de issues, nombres de ramas, mensajes de commit) directamente en los pasos `run:`; las pasan por variables de entorno intermedias. (GitHub, s. f.-c)
- [ ] **FLU-05.** Los secretos de Actions se usan solo en los pasos que los necesitan y no se imprimen en los registros. (GitHub, s. f.-c)
- [ ] **FLU-06.** *(Recomendado)* La rama principal está protegida y los cambios se fusionan por *pull request* con revisión. (Requisito de esta guía)

**2.6. Releases y respuesta a incidentes**

- [ ] **REL-01.** **Crítico.** Antes de cada *release*, un escaneo de secretos del árbol y de todo el historial y una revisión de datos personales y de rutas locales dan resultado limpio, y el resultado se archiva en el repositorio. (Zenodo, s. f.; Requisito de esta guía)
- [ ] **REL-02.** El contenido del archivo que se deposita en Zenodo se listó y se revisó: no incluye `.env`, cachés, claves, datos restringidos ni carpetas ajenas al cuaderno. (Requisito de esta guía)
- [ ] **REL-03.** El repositorio tiene un `SECURITY.md` con las versiones compatibles y la forma de reportar una vulnerabilidad o una filtración. (GitHub, s. f.-a)
- [ ] **REL-04.** Existe un procedimiento escrito ante una filtración: revocar o rotar la credencial, retirar el contenido del repositorio, pedir a Zenodo la retirada del registro cuando proceda y avisar a las personas afectadas. (GitHub, s. f.-b; Zenodo, s. f.)
- [ ] **REL-05.** *(Recomendado)* Los incidentes de seguridad y su resolución se registran en el `CHANGELOG.md` o en un archivo aparte. (Requisito de esta guía)

## 4. Prompt para validar los requisitos de seguridad

Este prompt convierte la lista de verificación en una auditoría repetible. Revisa el repositorio de un cuaderno (archivos, historial, salidas guardadas, dependencias y flujos de automatización), ejecuta las herramientas gratuitas que estén instaladas y genera un **reporte de cumplimiento** en Markdown y JSON. Funciona con cualquier asistente de IA que pueda leer archivos y ejecutar comandos.

**Procedimiento de uso**

1. Copie el prompt completo y reemplace los valores entre `<>` de la sección ENTRADAS.
2. Ejecútelo desde un entorno con acceso a los archivos del repositorio. Para escanear con `gitleaks` y `pip-audit`, use el modo `con_herramientas`.
3. Revise el reporte con una persona. Un asistente de IA puede equivocarse al leer un archivo o interpretar un criterio. El resultado es un apoyo a la revisión y no una certificación, y todo lo marcado «Requiere revisión humana» lo decide una persona.
4. Guarde el reporte **fuera del repositorio** o sin valores de secretos, y repita la auditoría antes de cada *release*.

:::{warning} Lo que este prompt no puede hacer
No puede probar que un repositorio está libre de código malicioso ni de secretos: detecta patrones conocidos, y un secreto con un formato inusual o un código ofuscado pueden pasar inadvertidos. Tampoco puede verificar la configuración de la cuenta de GitHub (protección de ramas, escaneo activo, tokens vigentes), que debe revisar una persona. Si el prompt encuentra un secreto, la acción es revocarlo en el proveedor (CRE-05), no solo borrarlo.

El auditor puede ser el primer lector de un secreto. Si es un servicio externo, no le entregue repositorios con credenciales ni datos personales: límpielos antes. El prompt le ordena no copiar nunca el valor de un secreto, de un dato personal ni de una dirección de correo al reporte, y citar solo archivo, línea y tipo. Si cambia la lista de verificación, actualice también los criterios del prompt.
:::

````text
Actúa como auditor de seguridad y privacidad de repositorios de cuadernos reproducibles en la Subdirección para el Conocimiento del Riesgo (UNGRD). Tu tarea es VERIFICAR si un repositorio cumple la lista de verificación de los «Requisitos de seguridad» y producir un REPORTE DE CUMPLIMIENTO. Eres un revisor: NO modifiques ningún archivo del repositorio.

## ENTRADAS
- RUTA_REPO: <ruta local del repositorio del cuaderno>
- MODO: "estatico" (solo leer archivos e historial local) o "con_herramientas" (además ejecutar `gitleaks` y `pip-audit` si están instalados; `pip-audit` envía a un servicio público los nombres y las versiones de los paquetes, nunca el contenido del repositorio). Si no lo indico, usa "estatico".
- SALIDA: carpeta donde escribir `reporte_seguridad.md` y `reporte_seguridad.json`. Debe estar FUERA del repositorio auditado; si no la indico, imprime el reporte.

## REGLAS DE CONDUCTA (obligatorias)
1. Toda afirmación cita su evidencia: archivo, línea y tipo de hallazgo, hash de commit o salida de un comando. Sin evidencia, el estado es «No verificable».
2. NUNCA copies al reporte, a la consola ni al JSON el valor de un secreto, de un dato personal ni de una dirección de correo. Reporta archivo, línea, tipo («token de Hugging Face», «ruta de usuario», «correo personal») y, para los correos, solo si es institucional, *noreply* o personal. Si usas `gitleaks`, ejecútalo con la opción `--redact`.
3. No inventes. No supongas que algo cumple. Distingue «No aplica» (con la razón) de «No cumple».
4. Solo lectura. No modifiques archivos del repositorio, no reescribas el historial y no ejecutes el cuaderno ni sus scripts. Las herramientas de la lista solo leen.
5. Si encuentras un secreto, indica de inmediato que debe revocarse o rotarse en el proveedor; no basta con borrarlo. Márcalo «Requiere acción inmediata».
6. Las decisiones sobre datos personales, datos de comunidades y derechos de terceros no son tuyas: márcalas «Requiere revisión humana».
7. No puedes ver la configuración de la cuenta de GitHub (protección de ramas, escaneo de secretos activo, vigencia de tokens): los criterios que dependen de ella son «No verificable» y «Requiere revisión humana».
8. Un hallazgo es un indicio, no una prueba de mala conducta. No acuses a nadie.

## PROCEDIMIENTO
### Paso A. Inventario
Describe la ruta auditada, el modo, la rama y el último commit, el tipo de repositorio (cuaderno, tablero, aplicación o modelo) y qué no se pudo revisar.

### Paso B. Comprobaciones automáticas (ejecuta las que apliquen y conserva la salida, sin valores sensibles)
1. Secretos en los archivos: busca los patrones `hf_`, `sk-`, `ghp_`, `AKIA`, `-----BEGIN .* PRIVATE KEY-----`, `api_key`, `password`, `token` y `secret` con valor asignado, y los archivos `.env`, `*.pem`, `id_rsa`, `credentials*` y `.netrc`. En modo «con_herramientas», ejecuta `gitleaks dir` con `--redact`.
2. Secretos en el historial: revisa todas las ramas y etiquetas (`git log --all -p -G '<patrón>'`) y los archivos borrados (`git log --all --diff-filter=D --name-only`). En modo «con_herramientas», ejecuta `gitleaks git` con `--redact`.
3. Salidas guardadas: en cada `.ipynb`, revisa `outputs` y `metadata` (omite las imágenes en base64) en busca de secretos, de `os.environ`, de encabezados de autorización y de trazas de error con rutas.
4. Rutas locales: busca `/Users/<nombre>`, `/home/<nombre>`, `C:\Users\<nombre>` y nombres de máquina en el código, las salidas, los documentos y los PDF (`strings`). Reporta archivo y línea, no la ruta completa.
5. Datos personales: busca correos, teléfonos y números de documento en texto y en salidas; lista los correos de autoría del historial (`git log --format='%ae %ce'`) y clasifícalos como institucional, *noreply* o personal sin transcribirlos; revisa `CITATION.cff`, `myst.yml` y `README.md`.
6. Metadatos de archivos: si hay `exiftool`, lista los campos de GPS, autoría y equipo de las imágenes y los PDF publicados.
7. Ejecución de código: busca `curl`, `wget`, `| bash`, `| sh`, `eval(`, `exec(`, `os.system(`, `subprocess` con `shell=True`, `%pip`, `!pip`, `!conda`, `!apt`, `pickle.load`, `allow_pickle=True`, `torch.load` y `yaml.load(` en `.py`, `.ipynb`, `.sh`, `postBuild`, `start` y `Makefile`.
8. Archivos peligrosos: en `git ls-files`, marca ejecutables, bibliotecas y archivos con macros (`.exe`, `.dll`, `.so`, `.dylib`, `.jar`, `.bat`, `.msi`, `.xlsm`, `.docm`, `.pyc`) y revisa los scripts de arranque (`binder/postBuild`, `binder/start`, `.devcontainer/`, `.githooks/`).
9. Descargas: en los scripts, comprueba que cada descarga use HTTPS, cite la fuente y registre una suma de verificación o una versión, y que algo la compruebe.
10. Dependencias: comprueba que `environment.yml` o `requirements.txt` tengan versiones exactas y que los nombres sean los de paquetes conocidos. En modo «con_herramientas», ejecuta `pip-audit -r` sobre el archivo de requisitos.
11. Flujos de automatización: en `.github/workflows/*.yml`, revisa `permissions`, que las acciones de terceros usen un hash de 40 caracteres, la presencia de `pull_request_target` o `workflow_run`, expresiones `${{ github.event.* }}` dentro de `run:` y el uso de `secrets.`.
12. Publicación: comprueba que existan `SECURITY.md`, `.gitignore` (con `.env`, cachés y `data/raw` si aplica), `.env.example` y una constancia del escaneo previo al último *release*.

### Paso C. Evaluación de criterios
Evalúa los 36 criterios. Para cada uno asigna exactamente un estado: Cumple, Parcial, No cumple, No aplica o No verificable. Los marcados (CRÍTICO) son compuertas bloqueantes y los marcados (RECOMENDADO) no condicionan la aceptación.

### Credenciales y secretos
CRE-01 (CRÍTICO). Ningún secreto (clave de API, token, contraseña, clave privada o cadena de conexión) está en los archivos del repositorio. (OWASP Foundation, 2025, A02; Requisito de esta guía)
CRE-02 (CRÍTICO). Ningún secreto está en el historial de git, incluidas todas las ramas, las etiquetas y los archivos que se borraron después. (GitHub, s. f.-b; Requisito de esta guía)
CRE-03. Ningún secreto aparece en las salidas guardadas del cuaderno, en sus metadatos ni en los registros (encabezados HTTP, variables de entorno, trazas de error). (Requisito de esta guía)
CRE-04. Las credenciales se leen de variables de entorno o de un gestor de secretos; el repositorio incluye un `.env.example` sin valores reales y `.gitignore` excluye `.env` (aplica solo si el cuaderno usa credenciales). (OWASP Foundation, 2025, A02; Requisitos de aplicaciones, REP-04)
CRE-05. Si un secreto se expuso alguna vez, se revocó o se rotó en el proveedor y el incidente se documentó; borrar el archivo o reescribir el historial no basta. (GitHub, s. f.-b)
CRE-06. Los tokens y las claves tienen los permisos mínimos que la tarea necesita (aplica solo si el cuaderno usa credenciales). (GitHub, s. f.-c)
CRE-07 (RECOMENDADO). Un escaneo automático de secretos está activo en el repositorio (el de GitHub u otra herramienta, como gitleaks). (GitHub, s. f.-b; Gitleaks, s. f.)

### Datos personales y rutas locales
FUG-01 (CRÍTICO). Ningún archivo, salida ni metadato publicado contiene datos personales (nombres, cédulas, teléfonos, direcciones, correos privados o coordenadas de viviendas) ni datos de comunidades sin autorización registrada; se exceptúan los datos de autoría que la persona autora decidió hacer públicos. (Requisitos de datos, PER; Carroll et al., 2020)
FUG-02. El código, las salidas guardadas y los documentos no contienen rutas absolutas del equipo de quien escribe (nombre de usuario, carpetas personales, nombre de la máquina); las rutas son relativas al repositorio. (Guía para publicar, Sección 4; Requisito de esta guía)
FUG-03. Los metadatos de las imágenes, los PDF y otros archivos publicados (GPS, autoría, equipo, ruta de origen) se revisaron y se eliminaron los que identifican a personas o lugares privados. (Requisito de esta guía)
FUG-04. Los correos de autoría del historial de git son institucionales, la dirección *noreply* de GitHub o los que la persona autora decidió publicar. (GitHub, s. f.-d)
FUG-05. `CITATION.cff`, `myst.yml` y el `README` publican solo los contactos que la persona autora autorizó (ORCID, correo institucional). (Requisito de esta guía)
FUG-06. `.gitignore` excluye cachés, registros, archivos temporales, configuración local del editor y copias de datos crudos que no deben publicarse. (Requisito de esta guía)

### Ejecución de código no confiable
EJC-01 (CRÍTICO). El cuaderno y los scripts no descargan ni ejecutan código de fuentes no verificadas: no hay `curl | bash`, ni `eval` o `exec` sobre contenido descargado, ni instalaciones desde direcciones URL o repositorios sin versión fijada. (OWASP Foundation, 2025, A03 y A08)
EJC-02. Las instalaciones dentro del cuaderno (`%pip`, `!pip`, `!conda`, `!apt`) usan versiones fijas y los mismos paquetes que `environment.yml`. (Requisito de esta guía)
EJC-03. El cuaderno no carga con `pickle`, `allow_pickle=True`, `torch.load` sin restricción ni `yaml.load` inseguro archivos que él mismo no generó. (Python Software Foundation, s. f.; OWASP Foundation, 2025, A08)
EJC-04. El repositorio no contiene ejecutables, bibliotecas compiladas ni archivos con macros (`.exe`, `.dll`, `.so`, `.dylib`, `.jar`, `.bat`, `.msi`, `.xlsm`, `.docm`), salvo los que se declaran y se explican. (Requisito de esta guía)
EJC-05. Los scripts de arranque (`postBuild` y `start` de Binder, `.devcontainer`, ganchos de git, `Makefile`) están revisados, se explican en el `README` y no descargan ni ejecutan nada fuera de los paquetes fijados. (OWASP Foundation, 2025, A03)
EJC-06. Las descargas de datos externos usan HTTPS, citan la fuente y registran una suma de verificación o una versión, que el cuaderno o un script comprueba. (OWASP Foundation, 2025, A08)
EJC-07. Los datos se distribuyen en formatos que no ejecutan código al abrirse (CSV, GeoJSON, GeoTIFF, NetCDF, Parquet). (Requisito de esta guía)
EJC-08. Quien evalúa o verifica un cuaderno ajeno lo ejecuta en un entorno aislado y desechable (contenedor, máquina virtual, Binder o Codespace), sin credenciales ni acceso a carpetas personales, y antes lee `environment.yml`, los scripts de arranque y las celdas que ejecutan comandos (aplica solo a quien verifica). (Requisito de esta guía)

### Dependencias
DEP-01. Las dependencias están fijadas con versión exacta en `environment.yml` o `requirements.txt`. (OWASP Foundation, 2025, A03; Guía para publicar, Sección 2)
DEP-02. Todas las dependencias provienen de índices oficiales (PyPI o conda-forge) y se verificó que el nombre corresponde al paquete previsto; ninguna fue sugerida por una IA sin comprobar que existe. (OWASP Foundation, 2025, A03; Requisitos de uso de IA, U16)
DEP-03. Un auditor de vulnerabilidades (por ejemplo, `pip-audit`) se ejecutó sobre el entorno y las vulnerabilidades conocidas se corrigieron o se justifican por escrito. (Python Packaging Authority, s. f.; OWASP Foundation, 2025, A03)
DEP-04 (RECOMENDADO). Las alertas automáticas de dependencias (Dependabot o equivalente) están activas. (Requisitos de tableros, SEG-05)

### Automatización: Actions, Binder y Colab
FLU-01. Los flujos de GitHub Actions fijan los permisos de `GITHUB_TOKEN` en solo lectura por defecto y elevan, trabajo por trabajo, solo los que necesitan. (GitHub, s. f.-c)
FLU-02. Las acciones de terceros están fijadas a un hash de commit completo, no a una etiqueta, que puede moverse o borrarse; las acciones oficiales de GitHub (`actions/*`) pueden fijarse por versión. (GitHub, s. f.-c; Requisito de esta guía)
FLU-03. Los flujos no usan `pull_request_target` ni `workflow_run` con acceso a secretos para ejecutar código de ramas de terceros. (GitHub, s. f.-c)
FLU-04. Los flujos no insertan entradas no confiables (títulos de issues, nombres de ramas, mensajes de commit) directamente en los pasos `run:`; las pasan por variables de entorno intermedias. (GitHub, s. f.-c)
FLU-05. Los secretos de Actions se usan solo en los pasos que los necesitan y no se imprimen en los registros. (GitHub, s. f.-c)
FLU-06 (RECOMENDADO). La rama principal está protegida y los cambios se fusionan por *pull request* con revisión. (Requisito de esta guía)

### Releases y respuesta a incidentes
REL-01 (CRÍTICO). Antes de cada *release*, un escaneo de secretos del árbol y de todo el historial y una revisión de datos personales y de rutas locales dan resultado limpio, y el resultado se archiva en el repositorio. (Zenodo, s. f.; Requisito de esta guía)
REL-02. El contenido del archivo que se deposita en Zenodo se listó y se revisó: no incluye `.env`, cachés, claves, datos restringidos ni carpetas ajenas al cuaderno. (Requisito de esta guía)
REL-03. El repositorio tiene un `SECURITY.md` con las versiones compatibles y la forma de reportar una vulnerabilidad o una filtración. (GitHub, s. f.-a)
REL-04. Existe un procedimiento escrito ante una filtración: revocar o rotar la credencial, retirar el contenido del repositorio, pedir a Zenodo la retirada del registro cuando proceda y avisar a las personas afectadas. (GitHub, s. f.-b; Zenodo, s. f.)
REL-05 (RECOMENDADO). Los incidentes de seguridad y su resolución se registran en el `CHANGELOG.md` o en un archivo aparte. (Requisito de esta guía)

### Paso D. Puntuación
- Cumple = 1, Parcial = 0,5, No cumple = 0. «No aplica» y «No verificable» no entran en el denominador, pero repórtalos con su conteo.
- Puntaje por grupo y total = suma de puntos de los criterios obligatorios y críticos ÷ criterios evaluables × 100, con un decimal. Los recomendados se reportan aparte.
- Nivel: 90 o más, «Alto»; de 75 a 89,9, «Aceptable»; de 50 a 74,9, «Mejorable»; menos de 50, «Insuficiente».
- Compuertas: si algún criterio CRÍTICO está en «No cumple», el resultado global es «NO APTO». Si alguno está en «No verificable», es «PENDIENTE DE VERIFICACIÓN». Si el puntaje es menor de 90, el resultado es «NO APTO» aunque no falle ningún crítico.
- EJC-08 aplica solo a quien verifica un cuaderno ajeno: en una auditoría del propio repositorio es «No aplica».

### Paso E. Redacta el reporte con esta estructura exacta
1. **Resumen ejecutivo**: resultado global, puntaje y nivel, criterios críticos fallidos, hallazgos que requieren acción inmediata y las tres prioridades más urgentes, en menos de 150 palabras.
2. **Alcance y método**: ruta auditada, modo, fecha y qué no se pudo revisar.
3. **Resultados por criterio**: tabla con ID, criterio, estado, evidencia (sin valores sensibles), acción recomendada y prioridad (Alta, Media o Baja).
4. **Puntaje por grupo**.
5. **Hallazgos con acción inmediata**: secretos, datos personales publicados y rutas locales, con archivo, línea y tipo, y el paso a seguir (revocar, rotar, retirar).
6. **Hallazgos que requieren revisión humana**, cada uno marcado como tal.
7. **Plan de mejora** ordenado por prioridad, con esfuerzo estimado (S, M o L).
8. **Limitaciones de esta auditoría**.

### Paso F. Versión legible por máquina
Escribe `reporte_seguridad.json` con esta forma, sin valores sensibles:
{"repositorio": "...", "fecha": "AAAA-MM-DD", "modo": "...", "resultado_global": "...", "puntaje_total": 0.0, "nivel": "...", "criterios": [{"id": "XXX-00", "estado": "...", "evidencia": "...", "accion": "...", "prioridad": "..."}], "acciones_inmediatas": [{"archivo": "...", "linea": 0, "tipo": "..."}], "revision_humana": ["..."], "no_verificables": ["XXX-00"]}

Termina con un resumen de cinco líneas y la ruta de los archivos generados.
````

**Compuertas críticas.** El prompt trata como bloqueantes los 5 criterios críticos y exige además un puntaje de 90 o más en los obligatorios. Estas reglas son criterios propios de la SCR.

## Referencias

Carroll, S. R., Garba, I., Figueroa-Rodríguez, O. L., Holbrook, J., Lovett, R., Materechera, S., Parsons, M., Raseroka, K., Rodriguez-Lonebear, D., Rowe, R., Sara, R., Walker, J. D., Anderson, J., y Hudson, M. (2020). The CARE Principles for Indigenous Data Governance. *Data Science Journal, 19*, Artículo 43. https://doi.org/10.5334/dsj-2020-043

GitHub. (s. f.-a). *Adding a security policy to your repository* [Documentación de GitHub]. Recuperado el 19 de noviembre de 2026, de https://docs.github.com/en/code-security/getting-started/adding-a-security-policy-to-your-repository

GitHub. (s. f.-b). *Secret scanning* [Documentación de GitHub]. Recuperado el 19 de noviembre de 2026, de https://docs.github.com/en/code-security/secret-scanning/introduction/about-secret-scanning

GitHub. (s. f.-c). *Secure use reference* [Documentación de GitHub Actions]. Recuperado el 19 de noviembre de 2026, de https://docs.github.com/en/actions/security-for-github-actions/security-guides/security-hardening-for-github-actions

GitHub. (s. f.-d). *Setting your commit email address* [Documentación de GitHub]. Recuperado el 19 de noviembre de 2026, de https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/setting-your-commit-email-address

Gitleaks. (s. f.). *Gitleaks* [Software]. GitHub. Recuperado el 19 de noviembre de 2026, de https://github.com/gitleaks/gitleaks

OWASP Foundation. (2025). *OWASP Top 10:2025*. Recuperado el 19 de noviembre de 2026, de https://top10.owasp.org/2025/

Python Packaging Authority. (s. f.). *pip-audit* [Software]. GitHub. Recuperado el 19 de noviembre de 2026, de https://github.com/pypa/pip-audit

Python Software Foundation. (s. f.). *pickle: Python object serialization* [Documentación de Python 3.15]. Recuperado el 19 de noviembre de 2026, de https://docs.python.org/3/library/pickle.html

Zenodo. (s. f.). *Manage records* [Documentación de Zenodo]. Recuperado el 19 de noviembre de 2026, de https://help.zenodo.org/docs/deposit/manage-records
