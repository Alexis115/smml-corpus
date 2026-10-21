# SMML-Corpus
### Corpus de Oferta Académica de Universidades del Ecuador

## Descripción

Este repositorio se centra en almacenar y mantener un corpus consolidado de información sobre la oferta académica de las diferentes universidades del Ecuador, generado mediante la metodología de Scrapping Mediado por Modelos de Lenguaje (SMML).

El corpus junta información estructurada sobre la oferta de carreras universitarias, obtenida a partir de las fuentes web institucionales de cada universidades/facultad y procesada mediante modelos de lenguaje para identificar, extraer y organizar datos académicos relevantes.

El objetivo del repositorio es proporcionar una fuente centralizada, versionada y actualizable de información, que facilite su utilización en procesos posteriores de preprocesamiento, análisis e investigación académica.

## Estructura del repositorio
```SMML-Corpus/
├── data/
│   └── corpus_smml.xlsx
├── docs/
│   └── diccionario_datos.md
├── README.md
├── CHANGELOG.md
```

El archivo data/corpus_smml.xlsx contiene información académica consolidada de diferentes universidades del Ecuador.

## Los principales campos de extracción son:


| Campo | Descripción | 
| :--- | :--- |
|id|Identificador unico.|
|pais|Ubicación geografica.|
|provincia|Ubicación geografica.|
|ciudad|Ubicación geografica.|
|universidad|Nombre completo.|
|siglas|Siglas oficiales.|
|nombre|Nombre de la carrera.|
|epn_homologa|Carrera equivalente en la EPN.|
|url|URL de la pagina oficial.|
|metodo_recoleccion|html (automatico) o manual.|
|fecha_recoleccion|Fecha ISO de recoleccion.|
|descripcion|Información descriptiva de la carrera.|
|perfil_ingreso|Conocimientos, habilidades o características esperadas del aspirante.|
|perfil_egreso|Competencias y capacidades del graduado.|
|perfil_profesional|Ámbitos y actividades de desempeño profesional.|



Los textos extraídos se conservan de forma literal, sin modificaciones ni resúmenes. Cuando la información no se encuentra disponible, se utiliza el valor No registra.

## Actualización del corpus

El corpus se mantiene como un único archivo Excel consolidado, actualizado progresivamente conforme se incorporan nuevas universidades y carreras.

Para publicar una nueva versión:
1. Actualizar el archivo Excel consolidado.
2. Mantener el nombre corpus_smml.xlsx y su estructura de columnas.
3. Reemplazar el archivo existente en data/.

Registrar la actualización mediante un commit y añadir una descripcion u razon de la actualizacion.

El historial de Git permite identificar las versiones publicadas y recuperar versiones anteriores cuando sea necesario.

## Uso del corpus

El archivo está destinado a actividades de investigación académica en conjunto con la oferta laboral presente en el país.

Ruta principal del corpus:

```data/corpus_smml.xlsx```

Esta ubicación se mantendrá constante para facilitar su integración con otros poryectos.

Consideraciones metodológicas

- Los datos por el momento proceden de las paginas web de universidades ecuatorianas.
- La extracción se realiza mediante la metodología SMML.
- Se procura conservar íntegramente el contenido textual extraido.
- La homologación de carreras considera su correspondencia académica con el catálogo de referencia de la EPN mediante homologación directa o afinidad academica.
- La disponibilidad y calidad de los campos dependen de la información publicada por cada universidad.
- Las actualizaciones del corpus pueden incorporar nuevos registros o correcciones de información previamente extraida.


