```mermaid
sequenceDiagram
    participant browser as Browser
    participant server as Server
    
    Note over browser: User types a new note and presses "Save"
    
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa { content: "New note" }
    activate server
    Note over server: Server stores the new note
    server-->>browser: { success: true, id: newNoteId, content: "New note", date: "2024-03-27" }
    deactivate server
    
    Note over browser: Browser updates the notes display using JavaScript without reloading the page

