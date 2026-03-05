# 🔄 Control de Flujo y Estructuras de Datos Avanzadas

Una vez que dominas las listas, el siguiente paso es manipularlas dinámicamente y estructurar la información de manera más inteligente.

## 🔁 Iterar sobre tablas y modificar valores
En Python (sin usar librerías externas), una "tabla" se representa comúnmente como una **lista de listas**, donde cada sub-lista es una fila. 

Para modificar datos, iteramos sobre cada fila utilizando un bucle `for`. Como las listas son mutables, los cambios que hagas dentro del bucle afectarán a la tabla original.

```python
# Tabla de ventas: [Producto, Precio, Cantidad]
ventas = [
    ["Camisa", 20.0, 50],
    ["Pantalón", 30.0, 30],
    ["Zapatos", 50.0, 10]
]

# Objetivo: Aplicar un impuesto del 10% a la columna de 'Precio' (índice 1)
print("--- Antes ---")
print(ventas)

for fila in ventas:
    precio_actual = fila[1]
    # Modificamos el valor directamente en la fila
    fila[1] = precio_actual * 1.10 

print("\n--- Después (Precios con impuesto) ---")
print(ventas) 
# Muestra los precios actualizados: 22.0, 33.0, 55.0
```

## 🔍 Filtros complejos con sentencias condicionales
A menudo necesitamos extraer información específica basada en múltiples criterios. Para ello, combinamos el bucle for con sentencias if y operadores lógicos (and, or, not).

```python
empleados = [
    # [Nombre, Departamento, Salario, Años_Antiguedad]
    ["Ana", "Ventas", 3000, 5],
    ["Luis", "IT", 4500, 2],
    ["Marta", "Ventas", 3200, 1],
    ["Carlos", "IT", 2900, 6]
]

candidatos_ascenso = []

# Regla de filtro: Departamento de IT 'O' (or) más de 4 años de antigüedad
# 'Y' (and) salario menor a 4000.
for emp in empleados:
    depto = emp[1]
    salario = emp[2]
    antiguedad = emp[3]
    
    if (depto == "IT" or antiguedad > 4) and salario < 4000:
        candidatos_ascenso.append(emp)

print("Candidatos para ascenso:", candidatos_ascenso)
# Resultado: Ana (Antigüedad) y Carlos (IT y salario bajo)
```

## 📖 Almacenar y organizar datos con Diccionarios
Mientras que las listas usan índices numéricos (0, 1, 2...), los diccionarios nos permiten organizar los datos usando claves (nombres descriptivos) y valores. Son ideales para representar objetos del mundo real o registros de bases de datos.

Sintaxis: Se usan llaves {} y la estructura clave: valor.

```python
# Un diccionario representando un solo producto
producto = {
    "nombre": "Laptop Gamer",
    "precio": 1500,
    "disponible": True,
    "colores": ["Negro", "Rojo"]  # Un valor puede ser una lista
}

# Acceder a datos por su clave (mucho más legible que usar índices)
print(producto["nombre"])  # Muestra: Laptop Gamer

# Modificar valores
producto["precio"] = 1400

# Agregar nueva información
producto["garantia"] = "2 años"

print(producto)
```


## ⚙️ Manejar grandes cantidades de datos con Funciones
Cuando trabajas con muchos datos, escribir el mismo código una y otra vez es ineficiente y propenso a errores. Las funciones te permiten encapsular lógica compleja en un bloque reutilizable.

Ventajas:

Reutilización: Escribes el código una vez, lo usas mil veces.

Organización: Divide problemas grandes en partes pequeñas.

Legibilidad: Tu código principal se vuelve más fácil de leer.

```python
# Definimos una función para procesar datos
def calcular_promedio(lista_de_numeros):
    if len(lista_de_numeros) == 0:
        return 0
    total = sum(lista_de_numeros)
    promedio = total / len(lista_de_numeros)
    return promedio

# Datos masivos (simulados)
datos_region_norte = [10, 20, 30, 40, 50]
datos_region_sur = [5, 15, 25, 35, 45, 55, 65]

# Usamos la función para procesar diferentes conjuntos de datos
promedio_norte = calcular_promedio(datos_region_norte)
promedio_sur = calcular_promedio(datos_region_sur)

print(f"Promedio Norte: {promedio_norte}")
print(f"Promedio Sur: {promedio_sur}")
```