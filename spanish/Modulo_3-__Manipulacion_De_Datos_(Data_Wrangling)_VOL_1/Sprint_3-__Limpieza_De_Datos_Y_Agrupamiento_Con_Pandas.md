# 🧹 Limpieza de Datos y Agrupamiento con Pandas

Antes de poder extraer *insights* valiosos o entrenar modelos de Machine Learning, los datos deben estar limpios, organizados y estructurados. En esta sección, cubriremos las técnicas esenciales de preparación y transformación de datos usando Pandas.

## 🏷️ Renombrar columnas de forma eficiente
A menudo, los nombres de las columnas en los datasets crudos son largos, tienen espacios o caracteres extraños. Pandas ofrece formas muy eficientes de estandarizarlos.

```python
# 1. Renombrar columnas específicas usando un diccionario
df = df.rename(columns={
    "Nombre del Cliente": "cliente",
    "Ventas Totales ($)": "ventas"
})

# 2. Renombrar TODAS las columnas de forma masiva (muy eficiente)
# Ejemplo: Convertir todo a minúsculas y reemplazar espacios por guiones bajos
df.columns = df.columns.str.lower().str.replace(' ', '_')
```

## 🕳️ Manejar valores ausentes (NaN)
Los datos faltantes son el pan de cada día. Dependiendo del contexto, puedes optar por eliminarlos o "imputarlos" (rellenarlos con otros valores).

```python
# 1. Eliminar filas que contengan CUALQUIER valor nulo
df_limpio = df.dropna()

# 2. Rellenar con un valor constante (ej. 0 o "Desconocido")
df_relleno = df.fillna(0)

# 3. Estrategia estadística: Rellenar con la media o mediana de esa columna específica
media_edad = df['edad'].mean()
df['edad'] = df['edad'].fillna(media_edad)

# 4. Estrategia secuencial: Rellenar con el valor anterior (útil en series de tiempo)
df_tiempo = df.fillna(method='ffill') # Forward fill
```
## 👯 Identificar y eliminar entradas duplicadas
Los registros repetidos pueden sesgar tus análisis (por ejemplo, contando una venta dos veces).

```python
# Ver cuántos registros duplicados existen en total
print("Duplicados:", df.duplicated().sum())

# Eliminar filas que son copias exactas en todas sus columnas
df = df.drop_duplicates()

# Eliminar duplicados basados SOLO en una columna (ej. ID de transacción)
# keep='last' mantiene la última aparición; por defecto mantiene la primera
df = df.drop_duplicates(subset=['id_transaccion'], keep='last')
```

## 🧩 Comprender y aplicar técnicas de agrupamiento
El agrupamiento nos permite segmentar nuestros datos por categorías para calcular métricas (sumas, promedios, conteos) de cada segmento por separado.

### Las 3 etapas del agrupamiento (Split-Apply-Combine)
El proceso de agrupamiento en Pandas sigue la famosa lógica Split-Apply-Combine (Dividir-Aplicar-Combinar):

- Split (Dividir): El dataset original se divide en pequeños grupos basados en los valores de una o más llaves (ej. dividir los datos por "País").
- Apply (Aplicar): Se aplica una función a cada grupo de forma independiente (ej. calcular la suma de las "Ventas").
- Combine (Combinar): Los resultados de cada grupo se unen en una nueva estructura de datos (un nuevo DataFrame resumido).

### Realizar agrupamientos en Pandas (groupby)
```python 
# Agrupar por 'departamento' y calcular el salario promedio de cada uno
salario_por_depto = df.groupby('departamento')['salario'].mean()

# Agrupamiento múltiple: Agrupar por 'departamento' y 'puesto', contando cuántos empleados hay
conteo_empleados = df.groupby(['departamento', 'puesto'])['id_empleado'].count()

# Agrupamiento avanzado con múltiples métricas usando .agg()
resumen_ventas = df.groupby('region').agg({
    'ventas': 'sum',       # Suma total de ventas por región
    'descuento': 'mean',   # Promedio de descuento dado
    'cliente': 'nunique'   # Conteo de clientes ÚNICOS
})
print(resumen_ventas)
```

## 🕵️ Ordenar datos para identificar valores atípicos (Outliers)
Una forma rápida y sencilla de encontrar anomalías (outliers) en tus datos sin usar matemáticas complejas es simplemente ordenar tus valores y revisar los extremos.

```python
# Ordenar de mayor a menor (descendente) para ver los valores más altos
# Útil para encontrar, por ejemplo, compras absurdamente grandes
valores_altos = df.sort_values(by='monto_compra', ascending=False)
print("Top 5 valores más altos:\n", valores_altos.head())

# Ordenar de menor a mayor (ascendente) para ver los valores más bajos
# Útil para encontrar valores negativos erróneos o precios en 0
valores_bajos = df.sort_values(by='monto_compra', ascending=True)
print("\nTop 5 valores más bajos:\n", valores_bajos.head())
```