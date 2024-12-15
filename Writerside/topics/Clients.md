# Clients
Además de conocer como montar un servidor/servicio API, es importante conocer también como se consumen, para ello vamos
a proceder a usar lo que denominamores clientes, puesto que estos son los que consumen nuestros servicios API.

## Tipos de clientes:
Existen diferentes tipos de clientes rest, para nosotros al menos vamos a usar dos:
- Clientes de lenguaje:
  - Son aquellos basados en lenguajes (Python, Go, Rust, etc..) que nos perminte de manera programatica, consumir servicios de API.
- Clientes de software
  - Son programas de software que facilitan y agilizan el consumo de api mediante interfaces sencillas de uso, y control avanzado de errores, estos software prestan:
      - **Postman** [https://www.postman.com](https://www.postman.com)
      - **Insomnia** [https://insomnia.rest](https://insomnia.rest)
      - **Thunder Client : VS Code** [https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client](https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client)
      - **RESTer** :
          - Firefox -> [https://addons.mozilla.org/en-US/firefox/addon/rester/](https://addons.mozilla.org/en-US/firefox/addon/rester/)
          - Chrome -> [https://chromewebstore.google.com/detail/rester/eejfoncpjfgmeleakejdcanedmefagga?hl=es&pli=1](https://chromewebstore.google.com/detail/rester/eejfoncpjfgmeleakejdcanedmefagga?hl=es&pli=1)
      - **Hoppscotch** : Cliente web https://hoppscotch.io
      - **HTTPie** : Cualquier OS, consola, web, app  [https://httpie.io](https://httpie.io)
      - **Curl** : Console
        curl -X GET "https://api.example.com/resource"
      - **Paw**: Solo macOS [https://paw.cloud](https://paw.cloud)
  
## Uso CURL:
El uso de curl es muy práctico, ya que ofrece una interfaz sencilla desde el propio terminal para interactuar con APIs 
REST. Es ideal para realizar pruebas rápidas sin necesidad de instalar software adicional o escribir código. Permite realizar solicitudes HTTP como GET, POST, PUT, DELETE, entre otras.

### Práctica con curl: Pokémon API
Vamos a utilizar la Pokémon API [https://pokeapi.co](https://pokeapi.co), que es gratuita y no requiere autenticación, para realizar solicitudes y obtener información de Pokémon.
1. **Consulta básica: Obtener un Pokémon por su nombre**
Usaremos una solicitud GET para obtener información sobre Pikachu:
```shell
curl -X GET "https://pokeapi.co/api/v2/pokemon/pikachu"
```
2. **Mostrar datos en un formato legible**:
```shell
curl -X GET "https://pokeapi.co/api/v2/pokemon/pikachu" | jq
```
3. **Obtener una lista de Pokémon:**
```shell
curl -X GET "https://pokeapi.co/api/v2/pokemon?limit=10"
```
4. **Simular un error: Solicitar un recurso inexistente:**
```shell
curl -X GET "https://pokeapi.co/api/v2/pokemon/nonexistent"
```

## Uso Python:
El uso de Python como cliente para consumir APIs REST es muy común, ya que es fácil de implementar y ofrece bibliotecas como requests para simplificar las solicitudes HTTP.
### Práctica con Python: Pokémon API
A continuación, un ejemplo sencillo de cómo consumir la misma API usando Python:
1. **Instalar la biblioteca requests (si no la tienes)**:
```shell
pip install requests
```
2. **Código para obtener información de Pikachu:**
```python
import requests

# URL de la API
url = "https://pokeapi.co/api/v2/pokemon/pikachu"

# Realizar la solicitud GET
response = requests.get(url)

if response.status_code == 200:
    data = response.json()
    print(f"Nombre: {data['name']}")
    print(f"Altura: {data['height']}")
    print(f"Peso: {data['weight']}")
    print("Habilidades:")
    for ability in data['abilities']:
        print(f"  - {ability['ability']['name']}")
else:
    print(f"Error: {response.status_code}")
```
**Salida esperada:**
```generic
Nombre: pikachu
Altura: 4
Peso: 60
Habilidades:
  - static
  - lightning-rod
```
3. **Listar Pokémons:**
```python
import requests

url = "https://pokeapi.co/api/v2/pokemon?limit=10"
response = requests.get(url)

if response.status_code == 200:
    data = response.json()
    for pokemon in data['results']:
        print(f"Nombre: {pokemon['name']} - URL: {pokemon['url']}")
else:
    print(f"Error: {response.status_code}")
```
**Salida esperada:**
```generic
Nombre: bulbasaur - URL: https://pokeapi.co/api/v2/pokemon/1/
Nombre: ivysaur - URL: https://pokeapi.co/api/v2/pokemon/2/
Nombre: venusaur - URL: https://pokeapi.co/api/v2/pokemon/3/
Nombre: charmander - URL: https://pokeapi.co/api/v2/pokemon/4/
Nombre: charmeleon - URL: https://pokeapi.co/api/v2/pokemon/5/
Nombre: charizard - URL: https://pokeapi.co/api/v2/pokemon/6/
Nombre: squirtle - URL: https://pokeapi.co/api/v2/pokemon/7/
Nombre: wartortle - URL: https://pokeapi.co/api/v2/pokemon/8/
Nombre: blastoise - URL: https://pokeapi.co/api/v2/pokemon/9/
Nombre: caterpie - URL: https://pokeapi.co/api/v2/pokemon/10/
```
4. **Manejar errores:**
```python
import requests 

url = "https://pokeapi.co/api/v2/pokemon/nonexistent"
response = requests.get(url)

if response.status_code == 404:
    print("El Pokémon solicitado no existe.")
else:
    print(f"Error: {response.status_code}")
```

## Comparativa entre Curl y Python
- curl es ideal para pruebas rápidas desde terminal sin ninguna dependencia de software, puesto se encuentra en la gran mayoria de terminales preinstalled.
- Python permite automatizar y manejar datos de manera más avanzada (programática) integrando la lógica en aplicaciones.

## Practica extendida:
Para ampliar tus conocimientos, dejo una practica extendida, que recomiendo hacer y que será afianzara los conocimientos aprendidos hasta el momento:
### Ejercicios con curl:
1- Obtener detalles de un Pokémon específico:
: - Usa curl para consultar los detalles del Pokémon Charmander en la API de Pokémon.
: - Formatea la salida utilizando jq para que sea legible (si tienen jq instalado).
: *Tip: Endpoint: https://pokeapi.co/api/v2/pokemon/charmander*

2- Listar Pokémon con un límite específico:
: - Realiza una solicitud para listar los primeros 20 Pokémon disponibles en la API.
: - Muestra únicamente el nombre de cada Pokémon utilizando herramientas como grep o jq.

3- Filtrar habilidades:
: - Consulta el Pokémon Bulbasaur y extrae únicamente los nombres de sus habilidades (abilities) en formato limpio, sin el resto de los datos.
: *Tip: La información sobre habilidades está en el campo abilities.*

4- Manejo de errores:
: - Simula una solicitud a un Pokémon que no existe (por ejemplo, nonexistent) y explica el resultado.
: - Devuelve únicamente el código de error usando el flag `-w "%{http_code}"`.

5- Envío de encabezados personalizados:
: - Haz una solicitud con un encabezado personalizado que envíe el nombre del alumno, simulando un uso más avanzado de curl.
: *Tip: Usa el flag -H para añadir encabezados.*

6- Descarga de sprites:
: - Consulta el sprite (imagen) del Pokémon Pikachu y descárgalo utilizando curl.
: *Tip: Los sprites están en sprites.front_default.*

### Ejercicios con Python:
1- Obtener detalles de un Pokémon específico:
: - Escribe un script que solicite al usuario el nombre de un Pokémon y devuelva su nombre, altura, peso y habilidades.
: * Tip: Maneja posibles errores como un nombre incorrecto o la ausencia de conexión a internet.*

2- Listar Pokémon con un límite específico:
: - Escribe un script que permita listar los nombres y URLs de los primeros N Pokémon.
: - N debe ser ingresado por el usuario.

3- Crear un diccionario con estadísticas:
: - Consulta los detalles de un Pokémon e imprime un diccionario con las estadísticas base (stats) en el formato:
:  ```
{
    "hp": 35,
    "attack": 55,
    "defense": 40,
    ...
}

4- Mostrar información de varios Pokémon:
: - Solicita al usuario una lista de nombres de Pokémon separados por comas (por ejemplo, “pikachu, charmander, bulbasaur”).
: - Devuelve los datos principales (nombre, altura, peso) de cada uno en un formato legible.

5- Buscar movimientos por tipo
: - Escribe un script que permita buscar los movimientos (moves) de un Pokémon específico.
: - Imprime una lista con los nombres de todos sus movimientos.

6- Descargar sprites automáticamente:
: - Escribe un script que permita descargar el sprite (imagen) de varios Pokémon y guardarlos en una carpeta local.
: - Los nombres de los Pokémon deben ser ingresados por el usuario.

7- Manejo avanzado de errores:
: - Crea un script que maneje los siguientes errores al consumir la API:
: Nombre de Pokémon incorrecto (error 404).
: Sin conexión a internet.
: Respuesta vacía o inesperada.

8- Extraer información avanzada:
: - Escribe un script que permita consultar el Pokémon con un ID específico, por ejemplo, el Pokémon con ID 25.
: - Extrae información como el tipo (types) y las habilidades (abilities) en una estructura como esta:
: ``` 
{
"name": "pikachu",
"types": ["electric"],
"abilities": ["static", "lightning-rod"]
}

9- Explorar la paginación de la API:
: - Usa Python para recorrer múltiples páginas de la API y listar los nombres de los primeros 100 Pokémon.
: *Tip: La API soporta parámetros de offset y limit para paginación.*

10- Generar un archivo JSON
: - Escribe un script que guarde los datos de los primeros 10 Pokémon (nombre, habilidades y tipos) en un archivo JSON llamado pokemon_data.json.
: - Usa la biblioteca json de Python para formatear los datos.

### Desafíos Avanzados:
#### Integración Python + curl:
1- Comparar resultados entre curl y Python:
: -	Realiza la misma solicitud con curl y Python (por ejemplo, listar los primeros 10 Pokémon).
: - Compara los resultados obtenidos para verificar consistencia.

2- Automatizar solicitudes con scripts:
: - Escribe un script en Python que genere comandos curl automáticamente para consultar los datos de varios Pokémon y los ejecute.