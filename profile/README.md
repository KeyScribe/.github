In addition to all source code and hardware designs, the project repository should include a README outlining
completed work, a description of the project’s architecture, and all known bugs. Failure to document bugs is
grounds for grade reduction.

Completed Work:

Project Architecture Description:

All Known Bugs:

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
When the user presses a push button, it will send a message to the server for the server to handle it. Currently, we have the server display which push buttons were pressed. Eventually we will pass in that data to the other Raspberry Pi/keyboard and have the LEDs on the other breadboard light up. 
  * LEDs circuit:
    When a button on the webpage is pressed, the corresponding LED will light up. The Raspberry Pi will accept a message and handle that so that the appropriate LED is lit up on the keyboard.
- Webpage:
  * The 
  
#### Internal System/ Data processing
### Known Bugs
