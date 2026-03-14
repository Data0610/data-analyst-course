# 🐼 Análisis de Datos con Pandas

**Pandas** es una biblioteca de Python de código abierto construida sobre NumPy. Proporciona estructuras de datos rápidas, flexibles y expresivas (como el **DataFrame** y la **Series**) diseñadas para trabajar con datos estructurados (tabulares, multidimensionales, etc.) de manera intuitiva.

Antes de empezar, recuerda que siempre debes importar la biblioteca al inicio de tu script:

```python
import pandas as pd
```

## 🔬 Preprocesamiento y Análisis Inicial
Cuando cargas un conjunto de datos (dataset) por primera vez, necesitas entender su forma, tamaño y contenido básico antes de manipularlo. Pandas ofrece métodos rápidos para este "vistazo inicial".

```python
# Supongamos que ya cargamos un DataFrame llamado 'df'

# 1. Ver las primeras y últimas filas
print(df.head())    # Muestra las primeras 5 filas por defecto
print(df.tail(3))   # Muestra las últimas 3 filas
print(df.sample(5)) # Muestra 5 filas al azar

# 2. Conocer la estructura y los tipos de datos
print(df.shape)     # Devuelve una tupla (filas, columnas), ej. (1000, 15)
print(df.info())    # Resumen técnico: nombres de columnas, tipos de datos y valores no nulos

# 3. Estadísticas descriptivas rápidas
print(df.describe()) # Calcula media, desviación estándar, min, max y cuartiles para columnas numéricas
```

## 📖 Técnicas Avanzadas de Lectura y Procesamiento
A menudo, los datos crudos no vienen en un formato perfecto. La función pd.read_csv() (y sus equivalentes para Excel, SQL, JSON) tiene parámetros poderosos para procesar los datos mientras los lees, ahorrándote mucho trabajo posterior.

```python
# Lectura avanzada de un archivo CSV
df_ventas = pd.read_csv(
    "ventas_2023.csv",
    sep=";",                     # Si el archivo está separado por punto y coma en lugar de coma
    usecols=["Fecha", "Total"],  # Cargar solo columnas específicas para ahorrar memoria
    parse_dates=["Fecha"],       # Convertir la columna 'Fecha' a formato de tiempo (datetime) automáticamente
    index_col="Fecha"            # Usar la columna 'Fecha' como el índice del DataFrame
)

# Procesamiento avanzado: Aplicar funciones personalizadas a columnas
# El método .apply() ejecuta una función sobre cada elemento de una serie
df_ventas['Total_con_IVA'] = df_ventas['Total'].apply(lambda x: x * 1.16)
```

## 🧹 Gestión de Datos Ausentes y Duplicados
En el mundo real, los datos están sucios. Faltan valores (representados como NaN o nulos) y hay registros repetidos. Limpiar esto es el 80% del trabajo de un analista de datos.

### Datos Ausentes (NaN)

```python
# 1. Identificar valores nulos
print(df.isna().sum())  # Cuenta cuántos valores nulos hay por cada columna

# 2. Eliminar filas con valores nulos (Útil si son pocos)
df_limpio = df.dropna()                 # Elimina cualquier fila que tenga al menos un NaN
df_limpio = df.dropna(subset=["Total"]) # Elimina la fila solo si falta el dato en la columna "Total"

# 3. Rellenar valores nulos (Imputación)
# Rellenar con un valor fijo (ej. 0) o con la media/mediana de la columna
media_ventas = df['Total'].mean()
df['Total'] = df['Total'].fillna(media_ventas)
```

### Datos Duplicados
```python
# 1. Identificar si hay filas exactamente iguales
print(df.duplicated().sum()) # Cuenta el total de filas duplicadas

# 2. Eliminar duplicados (Mantiene la primera aparición por defecto)
df = df.drop_duplicates()
```

## 🎯 Filtración de Datos con Métodos Sofisticados
Filtrar en Pandas va mucho más allá de seleccionar una columna. Puedes usar indexación booleana y métodos integrados para consultas complejas.

```python
# 1. Filtrado por condiciones múltiples (Indexación Booleana)
# Usamos & (AND) y | (OR). ¡Los paréntesis en cada condición son obligatorios!
filtro = (df['Edad'] > 25) & (df['Departamento'] == 'Ventas')
empleados_jovenes_ventas = df[filtro]

# 2. El método .isin() (Útil para buscar múltiples valores específicos)
paises_objetivo = ["México", "Colombia", "España"]
df_paises = df[df['Pais'].isin(paises_objetivo)]

# 3. El método .query() (Sintaxis más limpia basada en strings)
# Permite escribir consultas parecidas a SQL, haciendo el código muy legible
df_filtrado = df.query("Edad > 25 and Departamento == 'Ventas'")

# 4. Filtrado estructural con .loc e .iloc
# .loc: Filtra por las ETIQUETAS (nombres) de filas y columnas
# .iloc: Filtra por los ÍNDICES NUMÉRICOS (posiciones enteras) de filas y columnas

# Obtener todas las filas de clientes VIP, pero solo mostrando las columnas Nombre y Correo
vip_datos = df.loc[df['Categoria'] == 'VIP', ['Nombre', 'Correo']]

# Obtener las primeras 10 filas y las primeras 3 columnas (usando posiciones)
primeros_registros = df.iloc[:10, :3]
```


