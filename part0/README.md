4. New note diagram:---

Mermaid Syntax__
sequenceDiagram
participant browser

browser->>server: POST https://studies.cs.helsniki.fi/exampleapp/new_note
activate server
Note right of server:Server processes the new note and saves it to the database system

server-->>browser:Redirect to https://studies.cs.helsinki.fi/exampleapp/notes
deactivate server


browser->>server:GET https://studies.cs.helsinki.fi/exampleapp/notes
activate server
server-->>browser:HTML document
deactivate server

browser->server:GET https://studies.cs.helsinki.fi/exampleapp/main.css
activate server
server-->>browser:the css file
deactivate server

browser->>server:GET https://studies.cs.helsinki.fi/exampleapp/main.js
activate server
server-->>browser:the JavaScript file
deactivate server

Note right:The browser executes the JavaScript file to fetch JSON data

browser->>server:GET https://studies.cs.helsinki.fi/exampleapp/data.json
activate server
server-->>browser:Updated JSON with new note
deactivate server

Note right of browser: The browser executes the callback function to render updated notes







5.Single-Page App Diagram


sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser executes JavaScript to initialize the app and fetch the notes data

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: JSON data with existing notes
    deactivate server

    Note right of browser: JavaScript renders the notes dynamically on the page without a full reload




6.New note in single page app diagram


sequenceDiagram
    participant browser
    participant server

    Note right of browser: User enters a note and clicks Save

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    Note right of server: Server processes and saves the new note to the database
    server-->>browser: Response
    deactivate server

    Note right of browser: JavaScript dynamically updates the list of notes using the new data
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: Updated JSON with the new note
    deactivate server

    Note right of browser: JavaScript updates the UI to show the new note




