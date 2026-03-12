# 🛠️ Funciones y Alcance de Variables

A medida que tus programas crecen, escribir el mismo código una y otra vez se vuelve insostenible. Aquí es donde entran las **funciones**, que te permiten empaquetar bloques de código para reutilizarlos y optimizar tus procesos.

## 🏗️ Crear tus propias funciones
Una función es un bloque de código con un nombre que realiza una tarea específica. Para crear (o "definir") una función en Python, utilizamos la palabra clave `def`, seguida del nombre de la función, paréntesis `()` y dos puntos `:`.

[Image of Python function definition structure with parameters and return statement]

Puedes pasarle información a la función dentro de los paréntesis; a esto se le llama **parámetros** o **argumentos**.

```python
# Definir la función
def saludar_usuario(nombre):
    print(f"¡Hola, {nombre}! Bienvenido al sistema.")

# Llamar a la función (ejecutarla)
saludar_usuario("Ana")    # Muestra: ¡Hola, Ana! Bienvenido al sistema.
saludar_usuario("Carlos") # Muestra: ¡Hola, Carlos! Bienvenido al sistema.
```

## 📤 Utilizar la palabra clave return
Es muy importante entender la diferencia entre imprimir un valor (print) y devolver un valor (return).

print() simplemente muestra algo en la pantalla para que el humano lo lea.

return hace que la función devuelva un dato real al programa, de modo que puedas guardarlo en una variable o usarlo en otro cálculo. Cuando Python lee un return, la función termina inmediatamente.

```python
def calcular_area_rectangulo(base, altura):
    area = base * altura
    return area # Devuelve el valor calculado

# Guardamos el resultado de la función en una variable
resultado = calcular_area_rectangulo(5, 10)

# Ahora podemos usar ese resultado para otras cosas
costo_por_metro = 15
costo_total = resultado * costo_por_metro

print(f"El área es {resultado} y el costo total será ${costo_total}")
```

## 🌍 Variables Globales vs. Locales
En Python, el lugar donde creas una variable determina dónde puedes usarla. A esto se le llama alcance o scope.

- Variable Global: Se crea fuera de cualquier función. Puede ser leída y utilizada por cualquier parte de tu código, incluyendo dentro de las funciones.

- Variable Local: Se crea dentro de una función. Solo existe mientras esa función se está ejecutando. Una vez que la función termina, la variable local desaparece. El resto del programa no sabe que existe.

```python
# Variable GLOBAL (creada en el cuerpo principal del código)
impuesto_global = 0.16 

def calcular_precio_final(precio):
    # Variable LOCAL (creada dentro de la función)
    descuento_local = 20 
    
    # La función puede usar la variable local Y la global
    precio_con_descuento = precio - descuento_local
    precio_final = precio_con_descuento * (1 + impuesto_global)
    return precio_final

print(calcular_precio_final(100))

# ❌ ESTO DARÁ ERROR:
# print(descuento_local) 
# NameError: name 'descuento_local' is not defined (Porque solo existe dentro de la función)
```

## ⚡ Optimizar el código para grandes cantidades de datos
Cuando trabajas con análisis de datos (listas con miles o millones de registros), usar funciones es clave para la optimización y el rendimiento:

1- Evitas la repetición: En lugar de escribir la misma fórmula matemática en diferentes partes de tu código, llamas a una única función. Si hay un error en la fórmula, solo tienes que corregirlo en un lugar.

2- Procesamiento en lote (List Comprehensions): Puedes aplicar una función a todos los elementos de una lista grande de manera muy eficiente combinándola con técnicas avanzadas de Python.

```python
# Tenemos una lista inmensa de precios crudos
precios_crudos = [10.5, 20.0, 15.75, 40.2, 5.99] # Imagina que son miles

# Definimos una función de limpieza/transformación
def aplicar_inflacion(precio):
    nuevo_precio = precio * 1.05
    return round(nuevo_precio, 2)

# Optimizamos el procesamiento aplicando la función a toda la lista de forma compacta
precios_actualizados = [aplicar_inflacion(p) for p in precios_crudos]

print(precios_actualizados) 
# Muestra: [11.02, 21.0, 16.54, 42.21, 6.29]
```