# Clasificación de textos científicos en Esperanto

Práctica de Minería de Textos — CUNEF Universidad.

**Integrantes:** Gonzalo Casado Cabezas, Hugo Cortazar Alejo y Nicolás Mangas Álvarez.

Clasificamos párrafos de Wikipedia en Esperanto en tres categorías: biología (`biologio`), química (`kemio`) y física (`fiziko`). El notebook contiene la construcción del corpus, el NLP basado en reglas, la comparación de regresión logística y Naive Bayes mediante validación cruzada por artículos y la clasificación de páginas web.

## Archivos del repositorio

- `esperanto_scienco_dataset.csv`: corpus de partida, ampliado, antes de la última limpieza.
- `esperanto_scienco_fuentes.csv`: procedencia del corpus de partida, fila a fila.
- `esperanto_scienco_dataset_final.csv`: corpus limpio empleado en la evaluación y el entrenamiento.
- `esperanto_scienco_fuentes_final.csv`: procedencia del corpus definitivo, fila a fila.
- `MTPracticaFinal.ipynb`: código reproducible de las tres fases.

Los CSV de texto se guardan en UTF-8, con separador `;` y cabecera `text;class`. Los archivos de procedencia incluyen la huella SHA-256 del texto, el identificador de la página, su título y el identificador de la revisión original de Wikipedia.

## Ejecución

Abrir el notebook en Google Colab con CPU y ejecutar todas las celdas desde una sesión nueva. La variable `REPO` identifica el repositorio público y `REF` su rama. Con `REGENERAR_DATASET = False` se cargan los CSV publicados del corpus ampliado; con `True` se consulta la API para generar el corpus completo. El notebook informa del origen efectivo del corpus. Si faltan artículos previstos, no exporta los CSV para publicar.

El corpus ampliado evaluado en Colab contiene 2.114 párrafos finales de 62 artículos: 707 de biología (20 artículos), 781 de química (20) y 626 de física (22). Su huella es `4bbfeeff8265d51d4e7ecf68d1a0954b0608715f719c24bfc8a675a970c4f358`. La última limpieza elimina referencias y otros fragmentos de secciones auxiliares. Los cuatro CSV se exportan cuando todos los artículos previstos están disponibles. La revisión manual conserva los votos de la muestra histórica del corpus original de 1.203 párrafos, que no representa los artículos nuevos, y recupera sus textos por la huella de cada párrafo; las métricas se calculan nuevamente en cada ejecución.

## Fuentes, atribución y licencia de los textos

Los párrafos proceden de [Wikipedia en Esperanto](https://eo.wikipedia.org/), obra de sus respectivos colaboradores. La atribución de cada texto se puede consultar mediante `article_revision` en el fichero de procedencia: `https://eo.wikipedia.org/w/index.php?oldid=ID_DE_REVISION` (el enlace lleva a la revisión y al historial del artículo, donde figuran sus autores).

Distribuimos los textos reutilizados y adaptados bajo [Creative Commons Atribución-CompartirIgual 4.0 Internacional (CC BY-SA 4.0)](https://creativecommons.org/licenses/by-sa/4.0/), respetando las atribuciones adicionales que correspondan a cada fuente. Las modificaciones consisten en extraer párrafos, eliminar marcas y referencias residuales, normalizar espacios y separadores, excluir duplicados y asignar etiquetas temáticas. Esta licencia se refiere a los textos de Wikipedia; no implica automáticamente una licencia sobre el código del proyecto.

## Uso de herramientas de IA

Durante el desarrollo y la revisión del proyecto utilizamos herramientas de IA como apoyo para revisar código, preparar pruebas, desarrollar el clasificador y traducir y consultar textos de la muestra. Las valoraciones registradas corresponden a los integrantes del equipo. El uso de estas herramientas está sujeto al apartado 5.1 de la guía de la práctica; debemos poder justificar las decisiones y el funcionamiento del código.
