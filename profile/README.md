## KeyScribe
### Project Description
KeyScribe is a tool for those who are interested in learning piano and would benefit from remote and real-time lessons. Its ability to connect wirelessly to another KeyScribe (keyboard/piano) enables interaction between a teacher and student where the keys being pressed would be transmitted to the other board. Additionally, its sheet music reading and writing functionalities serve as a bridge between the auditory and visual aspects of learning to improve a user’s understanding of music and allow them to compose their pieces.

### Completed Work
#### [Pre-Alpha Video](https://youtube)
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
- Bug 1
- Bug 2 ...
