# Ejercicio - API Tasks
Ejercicio diseñado para poner en practica todo lo aprendido sobre APIs y Flask.
## Enunciado:
Imagina que estás desarrollando una API para gestionar tareas llamada TasksManager. Esta API permitirá a los usuarios realizar operaciones básicas sobre sus tareas, como listar, añadir, eliminar y completar tareas. El objetivo de este ejercicio es diseñar y construir una API funcional utilizando Flask, donde todas las respuestas se presenten en formato JSON, y los diferentes métodos HTTP y códigos de estado sean utilizados correctamente.

La API debe cubrir los siguientes escenarios básicos:
1.	Listar todas las tareas existentes.
2.	Añadir una nueva tarea.
3.	Borrar una tarea específica.
4.	Marcar una tarea como completada.

Además, para un desafío adicional, puedes incluir las siguientes funcionalidades extra:
1.	Editar una tarea específica, permitiendo tanto cambios parciales como totales.
2.	Borrar todas las tareas que ya estén completadas.
3.	Cambiar el estado de una tarea de “completada” a “incompleta”.

## Objetivo:

1.	Diseñar y construir una API funcional utilizando Flask que implemente todos los métodos necesarios para gestionar tareas.
2.  Asegurar que la API utilice correctamente los códigos de estado HTTP para comunicar el resultado de cada operación.
3.	Implementar validaciones para manejar errores como solicitudes mal formadas o tareas inexistentes.
4.	Presentar las operaciones disponibles en formato JSON, tanto en las respuestas como en los datos de entrada.

## Escenarios a Cubrir:

1.	Obtener todas las tareas: Los usuarios deben poder ver la lista completa de tareas, ya sea que estén pendientes o completadas.
2.  Crear una nueva tarea: Los usuarios pueden añadir una tarea con detalles como título, descripción y estado inicial (por defecto, “pendiente”).
3.	Eliminar una tarea específica: Los usuarios pueden borrar una tarea concreta si ya no es necesaria.
4.	Completar una tarea: Los usuarios pueden marcar tareas como “completadas”.
5.	Escenarios adicionales (opcional):
- Editar una tarea: Los usuarios pueden actualizar parcialmente o completamente una tarea específica.
- Eliminar todas las tareas completadas.
- Cambiar el estado de una tarea completada a “incompleta”.

## Tabla Guía:
A continuación, presenta los endpoints necesarios, los métodos HTTP correspondientes y los códigos de estado esperados:

| Endpoint               | Método HTTP | Descripción                                      | Código(s) de Estado Esperados          |
|------------------------|-------------|--------------------------------------------------|----------------------------------------|
| /tasks                | GET         | Listar todas las tareas                          | 200 OK, 404 Not Found                  |
| /tasks                | POST        | Añadir una nueva tarea                           | 201 Created, 400 Bad Request           |
| /tasks/{id}           | DELETE      | Eliminar una tarea específica                    | 204 No Content, 404 Not Found          |
| /tasks/{id}/complete  | POST        | Marcar una tarea como completada                 | 200 OK, 404 Not Found                  |
| /tasks/{id}           | PUT         | Editar completamente una tarea específica        | 200 OK, 400 Bad Request, 404 Not Found |
| /tasks/{id}           | PATCH       | Editar parcialmente una tarea específica         | 200 OK, 400 Bad Request, 404 Not Found |
| /tasks/completed      | DELETE      | Eliminar todas las tareas completadas            | 204 No Content                         |
| /tasks/{id}/incomplete| POST        | Cambiar una tarea de "completada" a "incompleta" | 200 OK, 404 Not Found                  |


## Criterios de Evaluación:
1. Diseño y estructura de los endpoints (40%):
- Los endpoints están claramente definidos y alineados con los principios REST.
- Los métodos HTTP seleccionados son apropiados para cada operación.
2. Uso de códigos de estado HTTP (30%):
- Los códigos de estado reflejan correctamente el resultado de cada operación.
- Se consideran posibles errores y escenarios excepcionales.
3. Implementación y manejo de errores (20%):
- La API devuelve mensajes de error claros en formato JSON.
- Las solicitudes mal formadas o los intentos de acceder a recursos inexistentes son correctamente manejados.
4. Características adicionales (10%):
- Se incluyen funcionalidades extra como editar tareas o eliminar tareas completadas.
- El diseño permite la extensibilidad futura para más funcionalidades.
