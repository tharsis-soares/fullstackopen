```mermaid
  sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server
    
    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server:  INPUT text field
    browser->>server: Click Save button  
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    browser->>server: headers { "Content-Type": "application/json" }
    browser->>server: body { "key": "value" }
    activate server
    server-->>browser: 200 OK
    server-->>browser: body { "response": "success" }
    deactivate server
    
    
    Note right of browser: The browser executes the callback function that record a new note
``` 