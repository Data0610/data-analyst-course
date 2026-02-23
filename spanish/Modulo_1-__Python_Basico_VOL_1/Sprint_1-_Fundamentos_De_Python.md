# 🐍 Fundamentos de Python

Una guía rápida de conceptos básicos de Python, ideal para principiantes y profesionales de datos.

## 📌 ¿Qué es Python?
**Python** es uno de los lenguajes de programación más populares del mundo, ampliamente utilizado y altamente valorado, especialmente por los profesionales de datos. Destaca por su legibilidad y versatilidad.

## 📝 Sintaxis
La **sintaxis** es el conjunto de reglas que definen cómo se escribe e interpreta el código en Python. Una sintaxis limpia y correcta es fundamental para que la computadora entienda qué acciones debe ejecutar.

## 🖨️ Comando `print`
La función `print()` se utiliza para mostrar mensajes o resultados en la pantalla. Es una de las herramientas más básicas y útiles para interactuar con tu código.

```python
# Ejemplo de uso:
print("¡Hola, GitHub!")
```

## 📦 Variables
Una variable es un contenedor diseñado para almacenar valores de datos. Se crea asignándole un nombre y un valor específico.

Operador de asignación
Para guardar un dato dentro de una variable, utilizamos el operador de asignación, que es el símbolo =.

```python
# Creando una variable y asignándole un valor
edad = 25
```

## Nombres de variable descriptivos
Es una buena práctica usar nombres de variable que describan claramente el valor que almacenan. Esto mejora significativamente la legibilidad y el mantenimiento del código.


```python
# ❌ Mal ejemplo (poco descriptivo)
x = "María"

# ✅ Buen ejemplo (descriptivo)
nombre_cliente = "María"
```


## Reasignación de variables
Las variables en Python son dinámicas, lo que significa que puedes reasignar o cambiar el valor almacenado en una variable en cualquier momento asignándole un nuevo valor.

```python
puntuacion = 10
print(puntuacion) # Muestra: 10

puntuacion = 15   # Reasignación
print(puntuacion) # Muestra: 15
```

## Sensibilidad a mayúsculas y minúsculas (Case Sensitive)
Python distingue entre mayúsculas y minúsculas. Esto significa que trata los nombres de variables que difieren en su capitalización como contenedores completamente distintos.

```python
Mi_Variable = 100
mi_variable = 50

# Son dos variables independientes
```

## Nombres de variable válidos
Para que Python acepte el nombre de una variable, debes seguir estas reglas estrictas:

Debe comenzar con una letra (a-z, A-Z) o un guion bajo (_).

No puede comenzar con un número.

Sólo puede contener letras, números y guiones bajos (A-z, 0-9, y _).

No se pueden usar palabras reservadas del sistema (como print, if, for).

```python
# ✅ Nombres Válidos:
mi_variable = 1
_variable_secreta = 2
usuario_1 = "Juan"

# ❌ Nombres Inválidos:
# 1_usuario = "Juan"  (Empieza con número)
# mi-variable = 1     (Contiene un guion medio)
```