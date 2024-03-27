```mermaid
sequenceDiagram
    participant browser as Browser
    participant server as Server
    
    Note over browser: User navigates to https://studies.cs.helsinki.fi/exampleapp/spa
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: SPA HTML document
    deactivate server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.css
    activate server
    server-->>browser: CSS file
    deactivate server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: JavaScript file
    deactivate server
    
    Note right of browser: The browser executes the JavaScript code initializing the SPA
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "SPAs are efficient", "date": "2023-1-1" }, ...]
    deactivate server
    
    Note right of browser: The browser renders the notes using JavaScript without reloading the page
