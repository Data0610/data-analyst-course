# 🧮 Operadores Aritméticos en Python

En Python, realizar cálculos matemáticos es un proceso muy intuitivo. A continuación, exploraremos qué son los operadores aritméticos, su sintaxis y cómo utilizarlos en tus programas.

## ❓ Qué es un operador aritmético
Un **operador aritmético** es un símbolo matemático estándar que le indica a Python que debe realizar una operación matemática específica (como sumar, restar, multiplicar o dividir) entre dos valores o datos. 

## 📝 Sintaxis de los operadores en Python
Python define y utiliza los siguientes símbolos para las operaciones aritméticas:

* **Suma (`+`)**: Suma dos valores.
* **Resta (`-`)**: Resta el valor de la derecha al de la izquierda.
* **Multiplicación (`*`)**: Multiplica dos valores.
* **División (`/`)**: Divide el valor de la izquierda por el de la derecha. (El resultado siempre es un número decimal o *float*).
* **División entera (`//`)**: Realiza la división pero devuelve solo la parte entera, descartando los decimales.
* **Módulo (`%`)**: Devuelve el "resto" o residuo de una división.
* **Exponenciación (`**`)**: Eleva el primer valor a la potencia del segundo.

## 🚀 Ejecutar operaciones aritméticas básicas
Puedes usar Python directamente como una calculadora. En estos ejemplos, utilizamos la función `print()` para que el resultado de la operación se muestre en la pantalla.

```python
# Suma
print(5 + 3)      # Muestra: 8

# Resta
print(10 - 2)     # Muestra: 8

# Multiplicación
print(4 * 2)      # Muestra: 8

# División
print(16 / 2)     # Muestra: 8.0 

# División entera
print(17 // 2)    # Muestra: 8 (ya que 2 cabe 8 veces en 17)

# Módulo (Resto)
print(17 % 3)     # Muestra: 2 (ya que 17 = 3 * 5 + 2)

# Exponenciación
print(2 ** 3)     # Muestra: 8 (2 elevado al cubo)
```

## 📦 Ejecutar operaciones aritméticas con variables
En proyectos reales, lo más habitual es almacenar los números en variables y realizar las operaciones utilizando los nombres de esas variables, en lugar de escribir los números directamente.

```python
# 1. Asignamos valores numéricos a las variables
precio = 50
descuento = 10
cantidad = 3

# 2. Ejecutamos operaciones usando las variables
precio_final = precio - descuento
costo_total = precio_final * cantidad

# 3. Mostramos los resultados
print("El precio con descuento es:", precio_final)  # Muestra: 40
print("El costo total por 3 artículos es:", costo_total)  # Muestra: 120

# También puedes actualizar el valor de una variable usando su propio valor actual:
puntuacion = 100
puntuacion = puntuacion + 50  # Sumamos 50 a los 100 originales
print("Puntuación actualizada:", puntuacion)  # Muestra: 150
```