# Clients
Además de conocer como montar un servidor/servicio API, es importante conocer también como se consumen, para ello vamos
a proceder a usar lo que denominamores clientes, puesto que estos son los que consumen nuestros servicios API.

## Tipos de clientes:
Existen diferentes tipos de clientes rest, para nosotros al menos vamos a usar dos:
- Clientes de lenguaje:
  - Son aquellos basados en lenguajes (Python, Go, Rust, etc..) que nos perminte de manera programatica, consumir servicios de API.
- Clientes de software
  - Son programas de software que facilitan y agilizan el consumo de api mediante interfaces sencillas de uso, y control avanzado de errores, estos software prestan:
      - Postman [https://www.postman.com](https://www.postman.com)
      - Insomnia [https://insomnia.rest](https://insomnia.rest)
      - Thunder Client : VS Code [https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client](https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client)
      - RESTer :
          - Firefox -> [https://addons.mozilla.org/en-US/firefox/addon/rester/](https://addons.mozilla.org/en-US/firefox/addon/rester/)
          - Chrome -> [https://chromewebstore.google.com/detail/rester/eejfoncpjfgmeleakejdcanedmefagga?hl=es&pli=1](https://chromewebstore.google.com/detail/rester/eejfoncpjfgmeleakejdcanedmefagga?hl=es&pli=1)
      - Hoppscotch : Cliente web https://hoppscotch.io
      - HTTPie : Cualquier OS, consola, web, app  [https://httpie.io](https://httpie.io)
      - Curl : Console
        curl -X GET "https://api.example.com/resource"
      - Paw: Solo macOS [https://paw.cloud](https://paw.cloud)