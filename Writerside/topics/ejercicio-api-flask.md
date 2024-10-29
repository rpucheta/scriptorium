# Ejercicio - API Flask
Estos ejercicios están diseñados para proporcionar una base sólida en el desarrollo de APIs REST usando Flask, cubriendo desde la creación de rutas simples hasta la manipulación de datos con métodos GET y POST.
Ref: https://flask.palletsprojects.com/en/3.0.x/

## Ejercicio 1: “Hola Mundo” con Flask

### 1- Enunciado:
Desarrolla una API simple en Flask que devuelva el mensaje “Hola Mundo” al acceder a la raíz (/) de la aplicación.

### 1- Objetivo:
Familiarizarse con la estructura básica de una aplicación Flask y el uso del método route para definir una ruta raíz.

### 1- Criterios de Evaluación:
- La API responde con el texto “Hola Mundo” en la raíz.
- La aplicación corre sin errores y responde en http://localhost:5000.
- El uso de debug=True en app.run() para facilitar la depuración.

## Ejercicio 2: “Endpoint de Saludo Personalizado”

### 2- Enunciado:
Expande la API para aceptar un nombre en la URL y devolver un saludo personalizado en el formato "Hola, < nombre > !".

### 2- Objetivo:
Entender cómo Flask maneja las rutas con parámetros dinámicos en la URL.

### 2- Criterios de Evaluación:
- La API devuelve un saludo personalizado cuando se accede a la ruta /saludo/< nombre >.
- El nombre se integra correctamente en el mensaje de respuesta.
- La aplicación responde correctamente en http://localhost:5000/saludo/<tu_nombre>.

## Ejercicio 3: “Lista de Tareas Simple”

### 3- Enunciado:
Crea un endpoint que devuelva una lista de tareas en formato JSON cuando el usuario acceda a /tareas.

### 3- Objetivo:
Familiarizarse con el uso de datos JSON y el método jsonify en Flask para formatear la respuesta de la API.

### 3- Criterios de Evaluación:
- El endpoint /tareas devuelve la lista de tareas en formato JSON.
- La respuesta contiene una estructura JSON con una clave “tareas” y el contenido adecuado.
- La API responde en http://localhost:5000/tareas y muestra la lista completa de tareas predefinidas.

## Ejercicio 4: “Agregar Tarea”

### 4- Enunciado:
Implementa un endpoint POST que permita al usuario agregar una nueva tarea a la lista. La tarea debe incluir un ID único y un título.

### 4- Objetivo:
Aprender a manejar solicitudes POST en Flask y a modificar datos existentes en respuesta a la solicitud del usuario.

### 4- Criterios de Evaluación:
- El endpoint /tareas acepta solicitudes POST para agregar nuevas tareas.
- Las nuevas tareas contienen un id único y el titulo proporcionado en el cuerpo de la solicitud.
- La API devuelve la tarea recién creada con un código de estado 201, confirmando que fue añadida correctamente.
- La aplicación responde correctamente en http://localhost:5000/tareas al agregar una tarea nueva usando una herramienta como Postman o curl.

Estos ejercicios te guiarán paso a paso en la creación de una API básica en Flask, cubriendo las operaciones esenciales 
y sentando las bases para desarrollar aplicaciones más complejas.


## Respuestas {collapsible="true"}

Mínima Aplicación:
```python  
from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello_world():
    return "<p>Hello, World!</p>"
```

Ejercicio 1:

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hola Mundo'

if __name__ == '__main__':
    app.run(debug=True)

```

Ejercicio 2:
```python
from flask import Flask

app = Flask(__name__)

@app.route('/saludo/<nombre>')
def saludo_personalizado(nombre):
    return f'Hola, {nombre}!'

if __name__ == '__main__':
    app.run(debug=True)

```

Ejercicio 3:
```python
from flask import Flask, jsonify

app = Flask(__name__)

tareas = [
    {"id": 1, "titulo": "Comprar leche"},
    {"id": 2, "titulo": "Estudiar Flask"}
]

@app.route('/tareas', methods=['GET'])
def get_tareas():
    return jsonify({'tareas': tareas})

if __name__ == '__main__':
    app.run(debug=True)
```

Ejercicio 4:
```python
from flask import Flask, jsonify, request

app = Flask(__name__)

tareas = [
    {"id": 1, "titulo": "Comprar leche"},
    {"id": 2, "titulo": "Estudiar Flask"}
]

@app.route('/tareas', methods=['GET'])
def get_tareas():
    return jsonify({'tareas': tareas})

@app.route('/tareas', methods=['POST'])
def add_tarea():
    if not request.json or not 'titulo' in request.json:
        abort(400)
    tarea = {
        'id': tareas[-1]['id'] + 1,
        'titulo': request.json['titulo']
    }
    tareas.append(tarea)
    return jsonify({'tarea': tarea}), 201

if __name__ == '__main__':
    app.run(debug=True)
```
