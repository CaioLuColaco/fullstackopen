Exercise 0.4:
```mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: The user fill the note's input and press the submit button

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server-->>browser: Status 302 - No Content
    deactivate server

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

    activate browser
    Note right of browser: The browser execute the javascript code to get the notes json from the server
    deactivate browser

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "Bora Vozão!", "date": "2001-11-20" }, ... ]
    deactivate server

    Note right of browser: The browser execute the callback's function to render the notes updated
```