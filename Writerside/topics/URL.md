# URL
## Definición:
La URL (Uniform Resource Locator) en una API es la dirección que permite acceder a recursos específicos en el servidor. 
En una API RESTful, cada recurso, como usuarios, productos o pedidos, se representa mediante una URL estructurada de forma
lógica y predecible, lo que facilita su acceso y uso.

## Estructura Básica:
Una URL de API suele tener esta estructura general:
```
https://api.ejemplo.com/{version}/{recurso}/{id_recurso}/{sub-recurso}
```
1.	Protocolo (https://): Especifica el protocolo de comunicación, generalmente HTTP o HTTPS en APIs modernas.
2. Dominio (api.ejemplo.com): El dominio o host donde reside la API.
3.	Versión de la API (v1): Se incluye una versión para garantizar la compatibilidad de cambios en la API sin interrumpir a los usuarios que usan versiones anteriores (por ejemplo, v1, v2).
4.	Recurso (/usuarios): Representa la entidad o colección de datos a la que se accede (p.ej., /users, /products).
5.	Identificador del recurso (/{id}): El ID de un recurso específico dentro de una colección, como /users/123.
6.	Sub-recurso (/{sub-recurso}): Se usa para especificar relaciones o detalles adicionales del recurso, como /users/123/orders.

### Ejemplos Urls:

| URL Endpoint                                | Descripción                                                     |
|---------------------------------------------|-----------------------------------------------------------------|
| https://api.ejemplo.com/v1/users            | Obtener la lista de usuarios.                                   |
| https://api.ejemplo.com/v1/users/123        | Obtener, actualizar o eliminar un usuario específico (ID: 123). |
| https://api.ejemplo.com/v1/users/123/orders | Obtener pedidos de un usuario específico.                       |
| https://api.ejemplo.com/v1/orders/456       | Acceder a un pedido específico (ID: 456).                       |

## Endpoint y Sus Reglas:
Un endpoint es una URL específica dentro de una API que permite acceder a un recurso o servicio particular en el servidor.
En el contexto de una API RESTful, un endpoint define la ubicación exacta donde una solicitud de cliente puede interactuar
con datos (por ejemplo, obtener, crear, actualizar o eliminar información).

### Ejemplos Endpoints:
- GET /books – Obtener una lista de todos los libros.
- POST /books – Crear un nuevo libro en la biblioteca.
- GET /books/{id} – Obtener información de un libro específico por su ID.
- PUT /books/{id} – Actualizar la información de un libro específico.
- DELETE /books/{id} – Eliminar un libro específico de la biblioteca.

### Reglas de Naming para Endpoints de una API RESTful:
1.	Nombres de Recursos en Plural:
- Los nombres de los recursos deben estar en plural para representar la colección de recursos. Ejemplo: /products, /users.
- Los sub-recursos también se nombran en plural, si representan una colección (por ejemplo, /users/123/orders).
2.	Uso de Verbos en Métodos, no en URLs:
- Los verbos no deben aparecer en las URLs; los métodos HTTP (GET, POST, PUT, DELETE, etc.) ya indican la acción a realizar.
- Correcto: GET /products para obtener productos.
- Incorrecto: /getProducts o /createUser.
3.	Jerarquía de Recursos y Sub-recursos:
- Si un recurso tiene una relación con otro, se puede expresar mediante sub-recursos.
- Ejemplo: Para pedidos de un usuario específico, usar /users/123/orders en lugar de /orders?user=123.
4.	Uso de IDs Únicos para Recursos Específicos:
- Para acceder a un recurso específico, se utiliza su identificador único en la URL.
- Ejemplo: /users/123 para acceder al usuario con ID 123.
5.	Convención de Nombres en Minúsculas y con Guiones:
- Utiliza nombres en minúsculas y separa palabras con guiones medios (-) en lugar de guiones bajos (_).
- Correcto: /product-categories
- Incorrecto: /product_categories
6.	Filtrado y Parámetros en la Query String:
- Para opciones de filtrado o búsqueda, utiliza parámetros en la query string (?).
- Ejemplo: /products?category=electronics para obtener productos en la categoría de electrónica.
7.	Versionado de la API en la URL:
- Usa un prefijo de versión (/v1, /v2) en la URL, especialmente útil cuando la API evoluciona con cambios no compatibles hacia atrás.
- Ejemplo: /v1/users vs. /v2/users para versiones diferentes de la API.

### Ejemplo Práctico de Endpoints Correctamente Nombrados:

| Método | URL Endpoint                  | Descripción                                    |
|--------|-------------------------------|------------------------------------------------|
| GET    | /v1/users                     | Obtener la lista de todos los usuarios         |
| POST   | /v1/users                     | Crear un nuevo usuario                         |
| GET    | /v1/users/{user_id}           | Obtener detalles de un usuario específico      |
| PUT    | /v1/users/{user_id}           | Actualizar completamente un usuario específico |
| DELETE | /v1/users/{user_id}           | Eliminar un usuario específico                 |
| GET    | /v1/users/{user_id}/orders    | Obtener los pedidos de un usuario específico   |
| PATCH  | /v1/orders/{order_id}/status  | Actualizar el estado de un pedido específico   |
