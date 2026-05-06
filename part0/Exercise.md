# Part 0

## Exercise 4

```mermaid
sequenceDiagram
participant browser
participant server

browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note <br/> request body:note=URL_ENCODED_USER_NOTE
activate server
server-->>browser: HTML REDIRECT /notes
deactivate server

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
activate server
server-->>browser: HTML-code
deactivate server

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
activate server
server-->>browser: the css file
deactivate server

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
activate server
server-->>browser: the JavaScript file
deactivate server

Note right of browser: The browser starts executing the JavaScript code that requests JSON data from the server

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
activate server
server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
deactivate server

Note right of browser: The browser executes the callback function that renders the notes
```

## Exercise 5

```mermaid
sequenceDiagram
participant browser
participant server

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
activate server
server-->>browser: HTML-code
deactivate server

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
activate server
server-->>browser: the css file
deactivate server

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
activate server
server-->>browser: the JavaScript file
deactivate server

Note right of browser: The browser starts executing the JavaScript code that requests JSON data from the server

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
activate server
server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
deactivate server

Note right of browser: The browser executes the callback function that renders the notes
```

## Exercise 6

```mermaid
sequenceDiagram
    participant browser
    participant server

    Note left of browser: user writes inside the text box and presses enter
    
    activate browser
    Note over browser: browser executes the form submit handler<br/>adds the text as a new note and timestamps
    browser->>browser: redrawNotes()
    Note left of browser: form-handler prepares a json payload

    browser->>server: "HTTP POST https://fullstack-exampleapp.herokuapp.com/new_note_spa\n**request** body:{\"content\":\"USER_NOTE\",\"date\":\"CURRENT_TIMESTAMP\"}"
    activate server
    Note right of server: payload is added<br/>to the notes array.
    server-->>browser: "HTTP 201 CREATED\n{\"message\":\"note created\"}"
    deactivate server

    Note left of browser: browser executes the event handler<br/>for the response
    deactivate browser
```
