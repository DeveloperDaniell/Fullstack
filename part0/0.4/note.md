```mermaid
sequenceDiagram
    participant browser as Browser
    participant server as Server
    
    Note over browser: The user writes a note in the text field and presses "Save"
    
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note {noteContent}
    activate server
    Note over server: Server saves the note in the database
    server-->>browser: { success: true, id: noteId, content: noteContent, date: noteDate }
    deactivate server
    
    Note over browser: The browser updates the list of notes using JavaScript
    Note over browser: The new note is added to the display without reloading the page
    
    Note over browser: Optionally, the browser can make a GET request
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    Note over server: Server sends back the updated list of notes
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ..., { "content": noteContent, "date": noteDate }]
    deactivate server
    Note over browser: The browser updates the list of notes based on the response
