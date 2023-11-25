# KeyScribe

## Design Prototype

### Project Description
KeyScribe is a tool for those who are interested in learning piano and would benefit from remote and real-time lessons. Its ability to connect wirelessly to another KeyScribe (keyboard/piano) enables interaction between a teacher and student where the keys being pressed would be transmitted to the other board. Additionally, its sheet music reading and writing functionalities serve as a bridge between the auditory and visual aspects of learning to improve a user’s understanding of music and allow them to compose their own pieces.

### Design Prototype Completed Work
| Task                  | Description                                                                                                                      |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| Front-end records data in MIDI format | When a button is pressed on the web it sends its corresponding MIDI data. |
| Database setup  | The database has all the tables set up with the necessary relations. |
| Back-end handles verification | A verification route for authentication of the keyboards connected to the server is set up. |
| Raspberry Pi sends timing data | Through interrupt handling, the boards can sync the LED ON and OFF state with the buttons' states and store the time the button was pressed to send it to the server |

### Project Architecture Description
#### External Interfaces
- Keyboard prototype:
  * Push button and LED synchronization: the Raspberry Pi will send information on when a button is pressed and released to the server. The server will forward this information to the other Raspberry Pi which will handle the received information. When a message is received, it checks the information about the state of the button (pressed or released) and calls the function to turn on or off the LED accordingly. Switch debouncing was added to the push button circuit and it performs well.
  * Keyboard verification: We are using JSON Web Tokens (JWT) to authenticate the Raspberry Pi boards over WebSockets. The board first sends a request to the HTTP server to connect to the WebSocket server. After the authentication is approved it will generate a token which will be passed in with each request and verified before the information gets passed to the other boards.
- Webpage:
  * After the login page, the user gets directed to the keyboard page. There we have added a better version of the breadboard than the pre-alpha one. We also added a “Start Recording” and a “Stop Recording” button on either side of the online keyboard and a timer on the bottom. 
  * We added a feature that when you click record and then stop recording, an output midi file is generated. However, currently, it is just hardcoded MIDI data. Will work on that in the future.
 
#### Internal System/ Data processing
The server is responsible for handling the requests from the webpage and the Raspberry Pi. The webpage sends HTTP requests to the server, for example, when a piano key button on the web is pressed, a POST request is sent to the server and the server will handle it. The handler for this particular case will extract the necessary information from the request (which key was pressed or released, mouse down or mouse up states) and will forward that information to the Raspberry Pi which will be ready to receive the information sent via WebSocket. When the Raspberry Pi receives the information, it will check if the key was pressed or released. If the key was pressed, it will light up the LED. If the key was released, it will turn off the LED. On the other hand, the Raspberry Pi will also be ready to send messages via WebSocket to the server whenever a push button is pressed. After it receives the message that comes through the server from the other Raspberry Pi, it will handle it accordingly. Currently, the Raspberry Pis store the information about the duration of each key pressed and send this to the server through a JSON formatted message. The server currently only prints a message to let us know which push button was pressed and for how long. In the future, we want that information to be stored in the server and to be able to use that information to generate MIDI files.

### Known Bugs
- SSL encryption of the WebSocket communication between the Raspberry Pi and the server is not working. Currently, it is operating over an insecure channel.
- The MIDI data is being received but not stored in the database.
- The user needs to request the assigning of a keyboard. Currently, this is fixed in the database. It is something we need to resolve before the next milestone.


## Pre-Alpha Design

### Pre-Alpha Completed Work
#### [Pre-Alpha Video](https://youtu.be/eNwDsNahN8E)
| Task                  | Description                                                                                                                      |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| Breadboard setup      | Built the prototype for the keyboard/piano LED and push button circuits.                                                         |
| Raspberry Pi setup    | Set the Raspberry Pi as the client sending and receiving data to/from the server.                                                |
| Backend server setup  | Had the server handle the HTTP requests coming from the webpage and the WebSocket data from the Raspberry Pi.                    |
| Frontend setup        | Set up the login page for users being students or teachers. Set up a simple HTML webpage to interact with the keyboard prototype.|

### Project Architecture Description
#### External Interfaces
- Keyboard prototype:
  The keyboard prototype is built on a breadboard with two separate circuits.
  * Push buttons circuit:
    When the user presses a push button, it will send a message to the server for the server to handle it. Currently, we have the server display which push buttons were pressed. Eventually, we will pass in that data to the other Raspberry Pi/keyboard and have the LEDs on the other breadboard light up. 
  * LEDs circuit:
    When a button on the webpage is pressed, the corresponding LED will light up. The Raspberry Pi will accept a message and handle that so that the appropriate LED is lit up on the keyboard.
- Webpage:
  * The login page is implemented. We have the users logging in with teacher or student options. We also have a piano keyboard route implemented, that displays 4 white keys and 3 black keys. The white keys correspond to the LEDs on the breadboard. The white keys are buttons that when a user presses them, will send a message to the server. Currently, simple HTML webpage is implemented but will be transferred to the React framework.
  
#### Internal System/ Data processing
The server is responsible for handling the requests from the webpage and the Raspberry Pi. The webpage sends HTTP requests to the server, for example, when a piano key button on the web is pressed, a POST request is sent to the server and the server will handle it. The handler for this particular case will extract the necessary information from the request (which key was pressed) and will forward that information to the Raspberry Pi which will be ready to receive the information sent via WebSocket. When the Raspberry Pi receives the information, it will set the corresponding GPIO pin to high and the LED will turn on. On the other hand, the Raspberry Pi will also be ready to send messages via WebSocket to the server whenever a push button is pressed. After it receives the message from the Raspberry Pi, it will handle it accordingly. Currently, the server prints a message to let us know which push button is pressed. In the future, we want that information to be sent to the other Raspberry Pi and the LED on the keyboard prototype connected to that Raspberry Pi to light up.

### Known Bugs
- SSL encryption of the websocket communication between the Raspberry Pi and the server is not working. Currently, it is operating over an insecure channel.
- Button presses on the keyboard may result in multiple messages sent to the server. This will be resolved in the future by debouncing the switches.
- Connecting multiple clients/Raspberry Pi-s overwhelms the server causing it to not respond at some times.
- The server sends the same data to all its connected clients. Needs to send it only to the desired ones.
