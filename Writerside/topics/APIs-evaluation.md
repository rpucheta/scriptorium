# Evaluación
Para evaluar este bloque vamos a hacer un ejercicio combinando los diferentes conceptos que hemos aprendido, pero para ir ya familiarizandonos con el tema IA que nos atañe, añadiremos un nuevo componente al paradigma.
En este caso vamos a añadir un modelo LLM de Meta para poder llamarlo desde nuestra API, así que antes de detallar todo lo necesario para esta prueba, vamos a empezar por el primer paso que es habilitar la forma de descargar y descargar dicho modelo.

## Paso 1 - Download LLM "meta-llama/Llama-3.2-1B-Instruct"
Este es el modelo de 1 Billón de parametros que vamos a utilizar en nuestra prueba, para ello, vamos a utilizar **[Huggingface](https://huggingface.co)** como proveedor de este modelo.
Aprendamos antes que es Huggingface, para el que no conozca HF es una plataforma y una biblioteca de herramientas de código abierto enfocada en la inteligencia artificial, particularmente en el procesamiento del lenguaje natural (NLP) y la implementación de modelos de aprendizaje profundo. Su misión es facilitar el acceso y la utilización de modelos avanzados de IA de una manera simple, eficiente y colaborativa.

### Alta en HF:
Es un proceso sencillo, de alta, con vuestro correo, no tiene mayor importancia, registraros y validar la cuenta para poder tener acceso a todos los modelos y datasets que este portal ofrece.

### Descarga el CLI para HF:
No es que sea estrictamente necesario pero va a agilizar todo aquello que vamos a realizar, y nos permitirá tener acceso a cualquier recurso por medio de sencillas lineas de comando en el cliente, para descargarlo e instalarlo:

Requisitos del sistema:
: - Asegúrate de tener Python 3.7 o superiror instalado
: - Tambien necesitas pip (el administrador de paquetes de python)

#### Instrucciones generales (todas las plataformas)
Instala con la siguiente instrucción desde tu terminal.
```generic
pip install -U "huggingface_hub[cli]"
```
Una vez se realice la instalación verifica que el CLI esta instalado correctamente:
```generic
huggingface-cli --version
```
Si ves la versión actual del CLI, la instalación fue exitosa.


#### Instrucciones especificas por sistema operativo
##### Windows
1. Abrir el terminal:
- Puedes usar PowerShell o el Símbolo del sistema (cmd).
- Si tienes Python instalado en Windows, asegúrate de que el comando python o pip esté en tu variable de entorno PATH.

2. Ejecutar la instalación:
```generic
pip install -U "huggingface_hub[cli]"
```

3. Comprueba que ha sido exitosa la instalación:
```generic
huggingface-cli --version
```

##### macOS
Se puede utilizar también python pero si quieres con brew:
```generic
brew install huggingface-cli
```

### Login en el CLI de Hugginface
Antes tendreis que acudir al portal web, para generaros de manera muy sencilla desde vuestro perfil un User access token os dejo el enlace:
[Huggingface Access Token](https://huggingface.co/security-checkup?next=%2Fsettings%2Ftokens)
Una vez obtenido guardarlo para futuro y vamos a proceder a hacer login:
```generic
huggingface-cli login
```
En este punto os pedira que introduzcais vuestro token, y con esto lo tendremos listo para trabajar.

### Descargar el modelo
Lo siguiente que vamos a entender es que no necesitamos descargar el modelo aunque podremos mediante línea de comandos, puesto que con las librerías que vamos a usar esto sera automático, no obstante si necesitamos aceptar los términos de meta para que nos deje descargarlos
cosa que tendreís que hacer cuanto antes, porque no es inmediato puede costar horas, para ello acudir a esta URL:

**[meta-llama/Llama-3.2-1B-Instruct](https://huggingface.co/meta-llama/Llama-3.2-1B-Instruct)**

Aquí veréis que tenéis que aceptar unos términos y esto lanzará una request a meta que os notificará por email cuando ya podéis acceder a los modelos.
Una vez que os notifique podeis probar a bajaros el modelo desde la linea de comandos (repito que no es necesario) mediante el siguiente command:
```generic
huggingface-cli download meta-llama/Llama-3.2-1B-Instruct --include "original/*" --local-dir Llama-3.2-1B-Instruct
```
Recomiendo hacer esto ya dentro de vuestro proyecto si queréis probar, puesto es bastante grande el modelo.

Por ahora esto es todo... WIP 

