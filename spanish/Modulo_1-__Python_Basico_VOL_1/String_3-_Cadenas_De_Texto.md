# 🧵 Cadenas de Texto (Strings) en Python

El manejo de texto es una de las tareas más comunes en programación. En Python, el texto se representa mediante un tipo de dato llamado **string** (cadena de caracteres).

## 🔤 Características básicas de los strings
* **Definición:** Un string es una secuencia de caracteres. Se crean envolviendo el texto entre comillas simples (`'Texto'`) o comillas dobles (`"Texto"`). Ambas funcionan exactamente igual.
* **Inmutabilidad:** Los strings en Python son **inmutables**. Esto significa que, una vez que creas un string, no puedes modificar sus caracteres internos de forma individual (aunque siempre puedes asignarle un texto completamente nuevo a la variable).

```python
saludo_1 = 'Hola Mundo'
saludo_2 = "Hola Mundo"
# Ambos son válidos y equivalentes
```

## 📏 Calcular la longitud de los strings
Para saber exactamente cuántos caracteres contiene un string (contando letras, espacios, números y símbolos), utilizamos la función incorporada len() (de length, longitud en inglés).

```python
mensaje = "Hola, GitHub"
longitud = len(mensaje)
print(longitud) # Muestra: 12 (El espacio y la coma también cuentan)
```

## 🏃‍♂️ Utilizar caracteres de escape
A veces necesitas incluir caracteres especiales dentro de un string, como comillas internas o saltos de línea. Para que Python no se confunda, usamos la barra invertida \ como carácter de escape.

- \' o \" : Permite insertar comillas dentro del texto.
- \n : Crea un salto de línea (Enter).
- \t : Crea una tabulación (sangría).

```python
# Usando comillas dentro de un string
cita = "Él dijo: \"Python es genial\""

# Usando salto de línea y tabulación
texto_formateado = "Lista de compras:\n\t- Manzanas\n\t- Pan"
print(texto_formateado)
```

## 📜 Crear strings multilínea
Si tienes un texto muy largo que abarca varios párrafos, usar \n puede ser tedioso. Python permite crear strings multilínea encerrando el texto entre tres comillas simples (''') o tres comillas dobles (""").

```python
poema = """Este es un texto
que ocupa varias líneas
sin necesidad de usar
caracteres de escape."""
print(poema)
```

## ✨ Formatear strings de manera efectiva
La forma más moderna, legible y eficiente de combinar variables con texto en Python son los f-strings (cadenas con formato). Solo tienes que poner una f antes de las comillas y colocar las variables entre llaves {}.

```python
nombre = "Ana"
edad = 28
# Usando f-strings
presentacion = f"Hola, me llamo {nombre} y tengo {edad} años."
print(presentacion) # Muestra: Hola, me llamo Ana y tengo 28 años.
```

## 🔍 Utilizar índices para acceder a elementos
Puedes acceder a cualquier carácter individual dentro de un string usando su índice (su posición numérica).

En Python, se empieza a contar desde el cero (0).

También puedes usar índices negativos para contar desde el final hacia atrás (donde -1 es el último carácter).
```python
palabra = "PYTHON"

# Índices positivos (de izquierda a derecha)
print(palabra[0])  # Muestra: 'P' (Primer carácter)
print(palabra[3])  # Muestra: 'H' (Cuarto carácter)

# Índices negativos (de derecha a izquierda)
print(palabra[-1]) # Muestra: 'N' (Último carácter)
print(palabra[-2]) # Muestra: 'O' (Penúltimo carácter)
```

## 🛠️ Procesar strings con métodos especializados
Los strings en Python vienen con "poderes" integrados llamados métodos, que te permiten transformarlos y analizarlos fácilmente. Aquí tienes algunos de los más comunes:

```python
texto = "  Python es INcreíble  "

# .lower() - Convierte todo a minúsculas
print(texto.lower())      # "  python es increíble  "

# .upper() - Convierte todo a mayúsculas
print(texto.upper())      # "  PYTHON ES INCREÍBLE  "

# .strip() - Elimina los espacios en blanco al principio y al final
texto_limpio = texto.strip()
print(texto_limpio)       # "Python es INcreíble"

# .replace() - Reemplaza una parte del texto por otra
print(texto_limpio.replace("INcreíble", "fácil")) # "Python es fácil"

# .split() - Divide el texto en una lista de palabras (por defecto separa por espacios)
palabras = texto_limpio.split()
print(palabras)           # ['Python', 'es', 'INcreíble']
```