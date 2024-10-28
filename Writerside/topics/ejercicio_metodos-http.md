# Ejercicio - Métodos HTTP
## Enunciado:
Imagina que estás diseñando una API para una plataforma de tareas llamada TaskManager. La plataforma permite a los usuarios
gestionar sus tareas diarias, como añadir nuevas tareas, actualizar el estado de las existentes, eliminar tareas completadas
o listar las tareas pendientes. El objetivo de este ejercicio es que, sin escribir código, diseñes cómo funcionaría la 
API y cómo se comportarían los métodos HTTP en diferentes escenarios.

## Objetivo:
1.	Definir los endpoints y métodos HTTP necesarios para las operaciones de una API RESTful que permita a los usuarios gestionar sus tareas en la plataforma.
2.  Identificar el código de estado HTTP que debería devolver cada operación según el escenario y cómo interpretará el cliente el resultado de cada operación.
3.	Presentar la estructura de la API (endpoints, métodos, códigos de estado) en una tabla clara y bien organizada.

## Escenarios a Cubrir:
1.	Obtener la lista de todas las tareas: Los usuarios deben poder ver todas sus tareas pendientes o completadas en una lista.
2.	Crear una nueva tarea: Los usuarios deben poder agregar una nueva tarea especificando el título, la descripción y la fecha de vencimiento.
3.	Actualizar una tarea específica: Los usuarios pueden editar una tarea existente, cambiando el título, la descripción o el estado (por ejemplo, de “pendiente” a “completada”).
4.	Eliminar una tarea: Los usuarios pueden eliminar tareas específicas cuando ya no son necesarias o han sido completadas.
5.	Marcar una tarea como completada: Los usuarios pueden marcar tareas específicas como completadas sin eliminar la tarea.

## Puntos Adicionales:
1. Considera el comportamiento de la API cuando la tarea no existe o cuando los parámetros de la solicitud son incorrectos.
2. Define claramente el código de estado HTTP que la API devolvería en cada operación.
3. Reflexiona sobre qué tipo de validaciones serían necesarias y cómo impactarían en el código de estado devuelto.

## Tabla Guia:
Realiza una tabla similar a la siguiente:

| Endpoint     | Método HTTP | Descripción                                   | Código(s) de Estado Esperados |
|--------------|-------------|-----------------------------------------------|-------------------------------|
| /fruits      | GET         | Obtener la lista de todas las frutas          | 200 OK, 404 Not Found         |
| /fruits/{id} | DELETE      | Elimina una fruta especifica de la plataforma | 204 No Content, 404 Not Found |
| /fruits/{id} | GET         | Obtener una fruta de la lista                 | 200 OK, 404 Not Found         |

## Criterios de Evaluación:
1.	Complejidad y precisión de los endpoints (40%):
   - Cada endpoint está claramente definido y cubre una funcionalidad específica en la API de TaskManager.
   - La selección de los métodos HTTP es correcta y sigue los principios REST.
2.	Uso adecuado de códigos de estado HTTP (30%):
   - Los códigos de estado son los apropiados para cada operación y escenario descrito (p. ej., creación, eliminación, errores).
   - Se consideran posibles errores y situaciones límite (como solicitudes incorrectas o tareas inexistentes).
3.	Claridad y organización de la presentación (20%):
   - La tabla es clara, fácil de leer y está bien organizada, facilitando la comprensión de cada operación.
   - La descripción es precisa y explica adecuadamente el comportamiento de cada endpoint.
4.	Creatividad en el diseño y consideración de validaciones (10%):
   - Consideración de casos especiales o adicionales que puedan surgir en un entorno real.
   - Ejemplos de validaciones útiles y cómo los códigos de estado ayudan a la experiencia del cliente (por ejemplo, gestión de errores de solicitud).
