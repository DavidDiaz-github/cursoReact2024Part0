# cursoReact2024Part0

#0.4: Nuevo diagrama de nota

sequenceDiagram
    participant User as Usuario
    participant Browser as Navegador
    participant Server as Servidor

    User->>Browser: Escribe una nota y hace clic en "Save"
    
    Note right of Browser: El navegador enviará la entrada del usuario al servidor.

    Browser->>Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate Server
    Server-->>Browser: Respuesta 302 Found (Redirección)
    deactivate Server

    Note right of Browser: El navegador realiza una redirección para recargar la página principal de notas

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate Server
    Server-->>Browser: HTML document
    deactivate Server

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate Server
    Server-->>Browser: the CSS file
    deactivate Server

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate Server
    Server-->>Browser: the JavaScript file
    deactivate Server

    Note right of Browser: El navegador ejecuta el código JavaScript que obtiene las notas actualizadas

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate Server
    Server-->>Browser: [{ "content": "Nueva nota", "date": "2024-12-30" }, ... ]
    deactivate Server

    Note right of Browser: El navegador renderiza la lista 



#0.5: Diagrama de aplicación de una sola página

sequenceDiagram
    participant User as Usuario
    participant Browser as Navegador
    participant Server as Servidor

    User->>Browser: Ingresa a la URL https://studies.cs.helsinki.fi/exampleapp/spa
    
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate Server
    Server-->>Browser: HTML document
    deactivate Server

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate Server
    Server-->>Browser: the CSS file
    deactivate Server

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate Server
    Server-->>Browser: the JavaScript file
    deactivate Server

    Note right of Browser: El navegador ejecuta el código JavaScript que maneja la lógica de la SPA

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate Server
    Server-->>Browser: [{ "content": "Primera nota", "date": "2024-12-30" }, ... ]
    deactivate Server

    Note right of Browser: El navegador renderiza la interfaz de la SPA con las notas obtenidas


#0.6: Nueva nota en diagrama de aplicación de una sola pagina

sequenceDiagram
    participant User as Usuario
    participant Browser as Navegador
    participant Server as Servidor

    User->>Browser: Escribe una nota y hace clic en "Save"
    
    Note right of Browser: El navegador envía la nueva nota al servidor mediante una solicitud POST

    Browser->>Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate Server
    Server-->>Browser: Respuesta 201 Created
    deactivate Server

    Note right of Browser: El navegador actualiza la lista de notas localmente sin recargar la página

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate Server
    Server-->>Browser: [{ "content": "Nueva nota", "date": "2024-12-30" }, ... ]
    deactivate Server

    Note right of Browser: El navegador re-renderiza la lista de notas actualizada en la interfaz
