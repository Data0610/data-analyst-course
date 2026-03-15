# 🚀 Análisis Eficiente de Datos con Pandas

Pandas no solo sirve para limpiar datos, sino que destaca por su tremenda eficiencia al momento de ingerir y explorar grandes volúmenes de información. A continuación, veremos las funcionalidades clave para cargar y conocer tus datasets a fondo.

## 📄 Leer archivos CSV con formatos diferentes
El formato CSV (Valores Separados por Comas) es el estándar de oro para compartir datos. Sin embargo, en la práctica, los archivos CSV vienen con separadores distintos, codificaciones diferentes o estructuras irregulares. La función `pd.read_csv()` está diseñada para manejar todos estos escenarios.

```python
import pandas as pd

# 1. Leer un CSV estándar (separado por comas)
df_estandar = pd.read_csv("datos.csv")

# 2. Leer un CSV separado por punto y coma (muy común en Excel en español)
df_punto_coma = pd.read_csv("datos_europeos.csv", sep=";")

# 3. Leer un CSV especificando la codificación (útil para evitar errores con tildes y ñ)
df_utf8 = pd.read_csv("datos_espanol.csv", encoding="utf-8")

# 4. Leer un CSV ignorando filas basura al inicio y asignando que no tiene encabezado
df_sin_formato = pd.read_csv("datos_sucios.csv", skiprows=3, header=None)
```

## 📊 Leer datos en diferentes hojas de archivos Excel
Los archivos de Excel (.xlsx) suelen contener múltiples pestañas u hojas de cálculo. Pandas te permite acceder a cualquiera de ellas, o incluso a todas al mismo tiempo, utilizando la función pd.read_excel().

```python
# Leer la primera hoja por defecto
df_excel = pd.read_excel("reporte_financiero.xlsx")

# Leer una hoja específica por su nombre exacto
df_ventas = pd.read_excel("reporte_financiero.xlsx", sheet_name="Ventas_Q1")

# Leer una hoja específica por su posición (el índice 1 es la segunda hoja)
df_gastos = pd.read_excel("reporte_financiero.xlsx", sheet_name=1)

# Leer TODAS las hojas a la vez (Esto devuelve un diccionario de DataFrames)
todas_las_hojas = pd.read_excel("reporte_financiero.xlsx", sheet_name=None)
```

## 🔍 Visualizar la estructura general y propiedades
Una vez cargados los datos, necesitas inspeccionarlos. Pandas ofrece herramientas integradas para obtener una radiografía instantánea de tu DataFrame sin tener que imprimir miles de filas en la pantalla.

```python
# Mostrar las dimensiones del dataset (devuelve una tupla: filas, columnas)
print(df_ventas.shape)

# Ver los tipos de datos de cada columna (int64 para enteros, float64 para decimales, object para texto)
print(df_ventas.dtypes)

# Obtener un resumen técnico completo
# ¡Esta es la función más útil para un primer vistazo! Muestra columnas, valores no nulos y uso de memoria.
df_ventas.info()
```

## 📈 Obtener estadísticas resumidas básicas
Para las columnas que contienen números (características numéricas), es vital conocer su distribución matemática rápida. El método .describe() calcula instantáneamente las estadísticas descriptivas más importantes de tu dataset.

```python
# Generar estadísticas descriptivas de todas las columnas numéricas
resumen_estadistico = df_ventas.describe()
print(resumen_estadistico)

"""
El método .describe() te devolverá automáticamente lo siguiente para cada columna:
- count: Cantidad total de datos (excluyendo valores nulos/vacíos)
- mean: El promedio o media aritmética
- std: Desviación estándar (qué tan dispersos están los datos respecto al promedio)
- min / max: Los valores mínimo y máximo registrados
- 25%, 50%, 75%: Los cuartiles (Nota: el 50% es exactamente la mediana)
"""
```
