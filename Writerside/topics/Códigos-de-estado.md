# Códigos de estado
## Definición:
Los códigos de estado HTTP son respuestas estándar emitidas por un servidor para indicar el resultado de una solicitud 
del cliente. Son fundamentales para la comunicación en la web, ya que permiten al cliente (por ejemplo, el navegador o 
una aplicación) entender si la solicitud se procesó correctamente o si hubo algún problema.

## ¿Porque usarlos?
Hay cuatro principales motivos:
- Indican el resultado de cada solicitud, permitiendo al cliente saber si fue exitosa, si requiere autenticación, si debe
- realizar otra acción o si debe corregir algún error en la solicitud. 
- Facilitan el manejo de errores y excepciones en el lado del cliente y del servidor, ya que ambos pueden interpretar y responder adecuadamente según el código de estado recibido.
- Mejoran la experiencia del usuario, especialmente los códigos como 404 o 503, que permiten mostrar mensajes claros o páginas de error informativas.

## Estructura de los códigos de estado:
Cada código de estado tiene tres dígitos  y está clasificado en posibles cinco categorias según su rango:

| Rango | Descripción                                                                                              |
|-------|----------------------------------------------------------------------------------------------------------|
| 1xx   | **Informativo:** Indican que la solicitud fue recibida y el proceso está en curso.                       |
| 2xx   | **Éxito:** Indican que la solicitud se completó con éxito.                                               |
| 3xx   | **Redirección:** Indican que es necesario tomar medidas adicionales para completar la solicitud.         |
| 4xx   | **Error del cliente:** Indican que hubo un problema en la solicitud hecha por el cliente.                |
| 5xx   | **Error del servidor:** Indican que el servidor no pudo procesar la solicitud debido a un error interno. |

## Código de estado comunes por categoría:
### 1xx
- **100 Continue:** El servidor ha recibido los encabezados de la solicitud y el cliente puede continuar enviando el cuerpo de la solicitud.
- **101 Switching Protocols:** El servidor acepta cambiar a otro protocolo, generalmente usado para cambiar de HTTP a WebSockets.

### 2xx
- **200 OK:** La solicitud se completó con éxito y se devolvió el recurso solicitado.
- **201  Created:** La solicitud fue exitosa y se creó un nuevo recurso.
- **202 Accepted:** La solicitud fue aceptada para procesamiento, pero aún no completada.
- **204 No Content:** La solicitud se completó con éxito, pero no se devuelve contenido en la respuesta.

### 3xx
- **301 Moved Permanently:** El recurso solicitado ha sido movido de forma permanente a una nueva URL.
- **302 Found:** El recurso solicitado ha sido movido temporalmente a una URL diferente.
- **304 Not Modified:** El recurso no ha cambiado desde la última solicitud, y el cliente puede usar la versión en caché.
- **307 Temporary Redirect:** Similar al 302, pero mantiene el método de solicitud original (como POST o GET) durante la redirección.

### 4xx
- **400 Bad Request:** La solicitud no es válida, a menudo debido a errores de sintaxis o parámetros incorrectos.
- **401 Unauthorized:** La solicitud requiere autenticación. Usualmente se presenta cuando el usuario no ha iniciado sesión.
- **403 Forbidden:** El servidor entendió la solicitud, pero rechaza cumplirla. Esto ocurre cuando el cliente no tiene los permisos necesarios.
- **404 Not Found:** El recurso solicitado no fue encontrado en el servidor.
- **405 Method Not Allowed:** El método HTTP utilizado no es permitido para el recurso.
- **429 Too Many Requests:** El cliente ha enviado demasiadas solicitudes en un tiempo determinado, a menudo como medida de control de uso (rate-limiting).

### 5xx
- **500 Internal Server Error:** Ocurrió un error inesperado en el servidor al intentar procesar la solicitud.
- **501 Not Implemented:** El servidor no soporta la funcionalidad requerida para cumplir con la solicitud.
- **502 Bad Gateway:** El servidor, actuando como un gateway o proxy, recibió una respuesta inválida del servidor upstream.
- **503 Service Unavailable:** El servidor no puede procesar la solicitud temporalmente, usualmente debido a mantenimiento o sobrecarga.
- **504 Gateway Timeout:** El servidor, actuando como gateway o proxy, no recibió una respuesta a tiempo del servidor upstream.