# 🚦 Sentencias Condicionales en Python

Las **sentencias condicionales** (o declaraciones condicionales) le permiten a tu programa tomar decisiones. Funcionan evaluando si una condición específica es verdadera (`True`) o falsa (`False`) y, basándose en ese resultado, ejecutan un bloque de código u otro.

[Image of Python if else flowchart diagram]

En Python, el control de flujo condicional se maneja principalmente con tres palabras clave: `if`, `elif` y `else`.

## 📌 1. La declaración `if` (Si...)
Es la forma más básica de una condicional. Le dice a Python: *"Si esta condición es verdadera, ejecuta el siguiente bloque de código. Si es falsa, sáltatelo"*.

**Nota importante sobre la sintaxis:** Python utiliza la **indentación** (espacios en blanco al principio de la línea) para definir qué código pertenece a la condición. No olvides poner los dos puntos (`:`) al final de la condición.

```python
temperatura = 30

# Si la temperatura es mayor a 25, se ejecuta el print
if temperatura > 25:
    print("Hace calor, no olvides hidratarte. 💧")
    
# El código sin indentación se ejecuta siempre, sin importar la condición
print("Fin de la revisión del clima.")
```

## 🔀 2. La declaración else (Si no...)
Se utiliza en combinación con un if. Sirve para atrapar cualquier caso en el que la condición del if original haya sido falsa.

```python
calificacion = 65

if calificacion >= 70:
    print("¡Felicidades, aprobaste el examen! 🎉")
else:
    print("No alcanzaste el mínimo aprobatorio. ¡Sigue intentando! 📚")
```

## 🚥 3. La declaración elif (O si no, si...)
Abreviatura de "else if". Te permite evaluar múltiples condiciones distintas, una tras otra, hasta encontrar una que sea verdadera. Puedes usar tantos elif como necesites.

```python
edad = 20

if edad < 13:
    print("Eres un niño.")
elif edad < 18:
    print("Eres un adolescente.")
elif edad < 65:
    print("Eres un adulto.")
else:
    print("Eres un adulto mayor.")
```

En este ejemplo, Python evalúa las condiciones en orden. Como 20 no es menor que 13, ni menor que 18, pero sí es menor que 65, imprimirá "Eres un adulto" y se saltará el resto.

## 🧩 4. Combinar condiciones con Operadores Lógicos
Puedes evaluar más de una cosa al mismo tiempo utilizando los operadores and (y), or (o), y not (no).

and: Devuelve True si ambas condiciones son verdaderas.

or: Devuelve True si al menos una condición es verdadera.

not: Invierte el resultado (de True a False y viceversa).

```python
tiene_identificacion = True
es_mayor_de_edad = False

# Uso de AND
if tiene_identificacion and es_mayor_de_edad:
    print("Puedes ingresar al club.")
else:
    print("Acceso denegado. Faltan requisitos.")
    
# Uso de OR
dia = "Sábado"
if dia == "Sábado" or dia == "Domingo":
    print("¡Es fin de semana! 🏖️")
```

## 5. Condicionales Anidados
Puedes poner una declaración if dentro de otra declaración if. Esto se conoce como anidamiento y es útil para verificar condiciones secundarias una vez que una condición primaria se ha cumplido.

```python
clima_bueno = True
tengo_dinero = True

if clima_bueno:
    print("Vamos a salir.")
    # Este if solo se evalúa si clima_bueno es True
    if tengo_dinero:
        print("¡Vamos a un restaurante!")
    else:
        print("Iremos a caminar al parque (es gratis).")
else:
    print("Nos quedamos en casa a ver películas.")
```