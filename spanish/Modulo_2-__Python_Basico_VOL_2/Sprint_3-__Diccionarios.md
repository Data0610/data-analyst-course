# 📖 Diccionarios en Python

Cuando trabajamos con datos estructurados, los **diccionarios** son una de las herramientas más poderosas y eficientes que ofrece Python. A continuación, exploraremos qué son, cómo se comparan con las listas y cómo manipularlos.

## 🧠 ¿Qué son los diccionarios?
Un diccionario en Python es una estructura de datos que almacena la información en pares de **clave-valor** (*key-value*). 
Imagina un diccionario del mundo real: buscas una palabra (la *clave*) para encontrar su definición (el *valor*). En Python, las claves deben ser únicas y los valores pueden ser cualquier tipo de dato (números, strings, listas, e incluso otros diccionarios).

Se definen utilizando llaves `{}` y separando la clave del valor con dos puntos `:`.

```python
# Ejemplo de un diccionario que representa a un usuario
usuario = {
    "nombre": "Carlos",
    "edad": 28,
    "profesion": "Analista de Datos",
    "activo": True
}
```

## ⚖️ Diccionarios vs. Listas
Aunque ambos sirven para almacenar colecciones de datos, tienen propósitos distintos:CaracterísticaListas []Diccionarios {}OrganizaciónColección ordenada de elementos.Colección de pares clave-valor.AccesoSe accede mediante índices numéricos (0, 1, 2...).Se accede mediante claves descriptivas (nombres).Uso idealGuardar secuencias de datos similares (ej. una lista de temperaturas).Representar entidades u objetos con atributos (ej. los datos de un cliente).

```python
# En una lista, debes recordar qué significa cada posición:
lista_usuario = ["Carlos", 28, "Analista"]
print(lista_usuario[1]) # Tienes que saber que el índice 1 es la edad

# En un diccionario, el acceso es explícito y claro:
print(usuario["edad"]) # Es evidente qué dato estás obteniendo
```

## 🔍 Recuperar valores de diccionarios
Existen dos formas principales de extraer información de un diccionario:

Usando corchetes []: Es directo, pero si la clave no existe, tu programa lanzará un error (KeyError) y se detendrá.

Usando el método .get(): Es la forma más segura. Si la clave no existe, devuelve None (o un valor por defecto que tú elijas) en lugar de romper el programa.

```python
equipo = {
    "nombre": "Cachorros",
    "ciudad": "Chicago",
    "campeonatos": 3
}

# 1. Usando corchetes
print(equipo["ciudad"]) # Muestra: Chicago

# 2. Usando .get()
print(equipo.get("campeonatos")) # Muestra: 3

# Si buscamos algo que no existe con .get()
print(equipo.get("estadio", "Estadio no registrado")) # Muestra: Estadio no registrado
```

## ➕➖ Agregar y eliminar elementos
Los diccionarios son mutables, por lo que puedes modificarlos en cualquier momento después de haberlos creado.

### Agregar o modificar
Para agregar un nuevo par clave-valor, simplemente asignas un valor a una nueva clave. Si la clave ya existe, su valor se actualizará (se sobrescribirá).

```python
perfil = {"usuario": "Ana", "puntos": 150}

# Agregar un nuevo elemento
perfil["nivel"] = "Avanzado"

# Actualizar (modificar) un elemento existente
perfil["puntos"] = 200

print(perfil) 
# Muestra: {'usuario': 'Ana', 'puntos': 200, 'nivel': 'Avanzado'}
```

### Eliminar
Puedes borrar elementos usando la palabra clave del o el método .pop() (que además te devuelve el valor eliminado).

```python
inventario = {"manzanas": 10, "naranjas": 5, "peras": 8}

# Eliminar con 'del'
del inventario["naranjas"]

# Eliminar con '.pop()' y guardar el valor
cantidad_peras = inventario.pop("peras")

print(inventario)      # Muestra: {'manzanas': 10}
print(cantidad_peras)  # Muestra: 8
```

## 🛠️ Trabajar con los resultados (Métodos de iteración)
Cuando necesitas procesar todos los datos de un diccionario, puedes utilizar bucles for junto con tres métodos muy útiles:

.keys(): Devuelve solo las claves.

.values(): Devuelve solo los valores.

.items(): Devuelve ambos (claves y valores) al mismo tiempo.

```python
calificaciones = {
    "Matemáticas": 9.5,
    "Historia": 8.0,
    "Ciencias": 9.0
}

# 1. Iterar sobre las claves (es el comportamiento por defecto)
print("Materias:")
for materia in calificaciones.keys():
    print(f"- {materia}")

# 2. Iterar sobre los valores (ej. para calcular un promedio)
total = sum(calificaciones.values())
promedio = total / len(calificaciones)
print(f"\nPromedio general: {promedio}")

# 3. Iterar sobre claves y valores a la vez (.items())
print("\nBoleta de calificaciones:")
for materia, nota in calificaciones.items():
    print(f"{materia}: {nota}")
```