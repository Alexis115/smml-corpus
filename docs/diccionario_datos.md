# Diccionario de datos — SMML-Corpus

## 1. Descripción

Este documento describe el esquema del archivo `data/corpus_smml.xlsx`, corpus consolidado de oferta académica de universidades ecuatorianas generado y ampliado mediante el proyecto de Scraping Mediado por Modelos de Lenguaje (SMML).

- **Formato:** Excel (`.xlsx`).
- **Hoja:** `data`.
- **Unidad de observación:** una carrera o programa académico registrado para una universidad y fuente de consulta.
- **Número de columnas:** 15.
- **Estructura:** una fila de encabezados y registros tabulares.
- **Ruta prevista en el repositorio:** `data/corpus_smml.xlsx`.

## 2. Campos

| Campo | Tipo lógico | Descripción | Criterios y observaciones |
|---|---|---|---|
| `id` | Entero | Identificador numérico del registro dentro del corpus. | Debe ser único y estable al actualizar registros; no confundir con un identificador oficial de carrera. |
| `pais` | Texto | País al que pertenece la institución de educación superior. | En el alcance actual se espera `Ecuador`. |
| `provincia` | Texto | Provincia donde se ubica la institución o sede asociada al registro. | Revisar la convención utilizada para universidades con varias sedes. |
| `ciudad` | Texto | Ciudad de ubicación de la institución o sede asociada al registro. | Mantener criterios de escritura consistentes. |
| `universidad` | Texto | Nombre de la institución de educación superior que oferta la carrera. | Usar la denominación institucional registrada en el corpus. |
| `siglas` | Texto | Sigla o abreviatura de la universidad. | Por ejemplo, `EPN`; no sustituye el nombre completo. |
| `nombre` | Texto | Denominación de la carrera o programa académico extraído. | Preservar el nombre registrado; distinguirlo de su homologación. |
| `epn_homologa` | Texto | Carrera de referencia de la Escuela Politécnica Nacional con la que se establece correspondencia académica. | Usar la denominación exacta del catálogo de referencia cuando exista; en registros de la propia EPN se observó `No aplica`. No interpretar como homologación oficial institucional. |
| `url` | Texto (URL) | Dirección web de la fuente institucional utilizada para obtener información de la carrera. | Conservar una URL trazable y verificar su validez cuando se actualice la fuente. |
| `metodo_recoleccion` | Texto categórico | Método o modalidad mediante el cual se recopiló el registro. | Se observó el valor `html`; el catálogo completo de métodos aún debe formalizarse. |
| `fecha_recoleccion` | Fecha o texto de ausencia | Fecha en que se obtuvo o registró la información. | En el archivo se observó `No registra`. Cuando haya fecha, conviene usar formato ISO `AAAA-MM-DD`; no asumir que todas las celdas son fechas nativas de Excel. |
| `descripcion` | Texto largo | Descripción general, presentación, propósito o información equivalente sobre la carrera. | Preservar íntegramente el texto fuente, sin resúmenes ni paráfrasis. |
| `perfil_ingreso` | Texto largo | Requisitos, conocimientos, habilidades y características esperadas del aspirante. | Aceptar secciones semánticamente equivalentes cuando correspondan al campo; conservar el texto literal. |
| `perfil_egreso` | Texto largo | Resultados de aprendizaje, capacidades o competencias esperadas de quien finaliza la carrera. | Preservar íntegramente el texto fuente. |
| `perfil_profesional` | Texto largo | Actividades, funciones, ámbitos ocupacionales o capacidades de ejercicio profesional del graduado. | Preservar íntegramente el texto fuente; admitir secciones equivalentes solo si corresponden semánticamente. |

## 3. Convenciones y calidad de datos

1. **Ausencia de información:** el proyecto utiliza la cadena literal `No registra` cuando no se dispone de un dato extraíble. Esta cadena no equivale a una celda vacía ni a un valor nulo en sistemas externos.
2. **No aplicabilidad:** `No aplica` representa un caso distinto de `No registra`; se ha observado en `epn_homologa` para carreras de la propia EPN. No generalizar a otros campos sin una regla explícita.
3. **Fidelidad textual:** los campos de contenido académico deben mantener el texto obtenido de la fuente, sin modificaciones, resúmenes ni generación de contenido ausente.
4. **Homologación:** la correspondencia con carreras EPN debe basarse en afinidad académica sustantiva y no únicamente en similitud nominal. Deben evitarse asociaciones forzadas.
5. **Trazabilidad:** `url`, `metodo_recoleccion` y `fecha_recoleccion` permiten documentar el origen y procedimiento de captura; una fecha ausente no debe inventarse.
6. **Actualizaciones:** mantener estables los nombres de las 15 columnas, la hoja `data` y la ruta del archivo para no romper procesos consumidores.
7. **Identificadores:** comprobar unicidad y continuidad de `id` antes de usarlo como clave en una base de datos externa.

## 4. Consideraciones para sistemas consumidores

- Leer expresamente la hoja `data` y los encabezados existentes.
- Tratar `No registra` y `No aplica` como valores categóricos especiales, sin convertirlos indiscriminadamente al mismo valor nulo.
- No suponer que `fecha_recoleccion` contiene siempre una fecha válida.
- No suponer que la homologación académica constituye un reconocimiento oficial de equivalencia curricular.
- No depender de un número fijo de filas: el corpus crece con las nuevas universidades y carreras.
- Registrar la versión del archivo o commit utilizado para facilitar la reproducibilidad de los análisis.

## 5. Aspectos pendientes de validación

- Catálogo completo de valores admitidos para `metodo_recoleccion`.
- Política definitiva de valores ausentes y no aplicables por campo.
- Regla de ubicación geográfica para instituciones con varias sedes.
- Validación de unicidad de `id`, duplicados académicos y filas efectivamente utilizables.
- Fecha y mecanismo de actualización del corpus.

---

**Estado del documento:** versión inicial basada en el esquema observado en `corpus_smml.xlsx`. Las recomendaciones de validación no implican que los datos existentes hayan sido modificados.
