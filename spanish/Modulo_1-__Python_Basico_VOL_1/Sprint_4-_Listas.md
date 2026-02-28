# 📋 Listas en Python

Una **lista** es una estructura de datos que te permite almacenar una colección ordenada de elementos en una sola variable. A diferencia de los strings, las listas son **mutables**, lo que significa que puedes modificarlas después de haberlas creado.

## ➕ Crear listas y agregarles datos
Para crear una lista, simplemente encierra los elementos entre corchetes `[]` y sepáralos con comas. Las listas pueden contener diferentes tipos de datos (números, strings, e incluso otras listas).

```python
# Crear una lista vacía
mi_lista = []

# Crear una lista con datos
frutas = ["manzana", "banana", "cereza"]
edades = [25, 30, 18, 42]
mezcla = ["texto", 45, True, 3.14]

# Agregar un elemento al final de la lista con .append()
frutas.append("naranja")
print(frutas)  # Muestra: ['manzana', 'banana', 'cereza', 'naranja']

# Insertar un elemento en una posición específica con .insert()
# (El primer número es el índice, el segundo es el valor)
frutas.insert(1, "kiwi")
print(frutas)  # Muestra: ['manzana', 'kiwi', 'banana', 'cereza', 'naranja']
```

## ✂️ Sorting, Slicing y modificaciones básicas
Slicing (Segmentación)
El slicing te permite extraer una porción o "sub-lista" utilizando la sintaxis [inicio:fin]. Recuerda que el índice de inicio se incluye, pero el índice de fin no se incluye.

```python
letras = ["A", "B", "C", "D", "E"]

# Extraer desde el índice 1 hasta el 3 (sin incluir el 4)
print(letras[1:4])  # Muestra: ['B', 'C', 'D']

# Extraer desde el principio hasta el índice 2
print(letras[:3])   # Muestra: ['A', 'B', 'C']

# Extraer desde el índice 2 hasta el final
print(letras[2:])   # Muestra: ['C', 'D', 'E']
```

## Sorting (Ordenación)
Puedes ordenar los elementos de una lista fácilmente. Si son números, se ordenarán de menor a mayor; si son strings, se ordenarán alfabéticamente.

```python
numeros = [4, 1, 8, 3]

# .sort() modifica la lista original permanentemente
numeros.sort()
print(numeros)  # Muestra: [1, 3, 4, 8]

# Para ordenar al revés (descendente)
numeros.sort(reverse=True)
print(numeros)  # Muestra: [8, 4, 3, 1]
```
## Otras modificaciones (Eliminar datos)

```python
colores = ["rojo", "azul", "verde", "azul"]

# .remove() elimina la primera aparición de un valor específico
colores.remove("azul")
print(colores)  # Muestra: ['rojo', 'verde', 'azul']

# .pop() elimina y devuelve el elemento en el índice especificado (o el último si no se especifica)
ultimo_color = colores.pop()
print(colores)       # Muestra: ['rojo', 'verde']
print(ultimo_color)  # Muestra: 'azul'
```

## Trabajar con listas anidadas
Una lista anidada es simplemente una lista dentro de otra lista. Esto es muy útil para representar matrices, tablas o cuadrículas de datos.

```python
# Crear una lista de listas (matriz de 3x3)
matriz = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

# Acceder a la primera lista interna
print(matriz[0])  # Muestra: [1, 2, 3]

# Acceder a un elemento específico (fila 1, columna 2)
# Primero seleccionamos la lista interna, luego el elemento dentro de ella
numero_seis = matriz[1][2]
print(numero_seis)  # Muestra: 6
```

## 🧹 Utilizar métodos de lista para preprocesar strings
Las listas y los strings trabajan muy bien juntos. Es común convertir un string en una lista para limpiarlo o procesarlo, y luego volver a unirlo.

Los métodos clave aquí son .split() (de string a lista) y .join() (de lista a string).


```python
# 1. Tenemos un string desordenado o proveniente de un archivo CSV
datos_crudos = "manzana, pera,   uva , naranja"

# 2. Separamos el string en una lista usando la coma como delimitador
lista_frutas = datos_crudos.split(",")
print(lista_frutas)  # Muestra: ['manzana', ' pera', '   uva ', ' naranja']

# 3. Limpiamos los espacios en blanco de cada elemento (simulación de preprocesamiento)
# (Aquí usamos una 'comprensión de lista', una técnica avanzada pero muy común)
lista_limpia = [fruta.strip() for fruta in lista_frutas]
print(lista_limpia)  # Muestra: ['manzana', 'pera', 'uva', 'naranja']

# 4. Volvemos a unir la lista en un solo string, separado por guiones
nuevo_string = " - ".join(lista_limpia)
print(nuevo_string)  # Muestra: manzana - pera - uva - naranja
```