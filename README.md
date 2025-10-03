## Documentación de limpieza del dataset EVA

Este documento describe los cambios realizados al dataset Evaluaciones Agropecuarias Municipales (EVA) con el fin de estandarizar y preparar la información para su análisis en Power BI.

-----------------------------------------------------------------------------------------------------------------------------------------
## Fuente de datos

El dataset fue extraído de la Plataforma Nacional de Datos Abiertos de Colombia.

-Evaluaciones_Agropecuarias_Municipales_EVA_20250923.csv -> Dataset Original.


------------------------------------------------------------------------------------------------------------------------------------------
## Cambios realizados

1.	Estandarización de nombres:
Se cambia el nombre de diferentes columnas puesto que no tenían un orden definido. Se implementa snake_case para evitar errores en análisis posteriores.

2.	Normalización de columnas numéricas:
Los datos en algunas columnas numéricas estaban almacenados como texto con separadores de miles representados por comas. Se eliminaron las comas y se asignó su respectivo tipo (entero o decimal) para facilitar el análisis de esta información.

3.	Normalización de texto:
En las columnas de texto, para prevenir inconsistencias, se aplica mayúsculas a todos los valores.

4.	Verificación de valores nulos:
Se verificaron las columnas del dataset y se identificaron valores nulos. Estos se conservaron, ya que corresponden a datos faltantes propios de la fuente y no alteran la estructura del dataset.

------------------------------------------------------------------------------------------------------------------------------------------
## Caso especial

Al importar el archivo csv en Power BI salió un mensaje similar a este: 

1 de las consultas cargadas contienen errores.Ver errores Evaluaciones_Agropecuarias_Municipales_EVA_20250923 
cargaron 15.774 filas. 43 errores.


Al revisar, en la columna produccion_t había valores donde la coma se utilizaba en algunos casos como separador decimal (ejemplo: 1,85) y en otros como separador de miles (ejemplo: 2,028, que corresponde a 2028). Dado que esta inconsistencia proviene del creador del dataset, se estandarizó el formato reemplazando las comas por puntos y se utilizó la configuración regional para asegurar que se leyera bien. Sin embargo, hay que aclarar que la normalización pudo modificar el valor real en algunos registros, debido a errores de digitación en el origen de los datos.

------------------------------------------------------------------------------------------------------------------------------------------
## Archivos Generados

- limpieza_eva.pbix -> Archivo de Power BI con las transformaciones aplicadas.
- README.md -> Este documento con la descripción y justificación del proceso de limpieza. 