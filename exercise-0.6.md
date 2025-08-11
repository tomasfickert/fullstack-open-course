sequenceDiagram
    participant Browser
    participant Server

    Browser->>Server: GET /notes/new
    activate Server
    Server-->>Browser: HTML document
    deactivate Server

    Browser->>Server: GET /main.css
    activate Server
    Server-->>Browser: CSS file
    deactivate Server

    Browser->>Server: GET /main.js
    activate Server
    Server-->>Browser: JavaScript file
    deactivate Server

    Note right of Browser: Browser executes JavaScript that<br/>handles form submission via AJAX

    Browser->>Server: POST /api/notes (AJAX)
    activate Server
    Server-->>Browser: JSON response { "id": 123, "title": "New Note", ... }
    deactivate Server

    Note right of Browser: JavaScript updates DOM to show<br/>the new note without page reload
    
