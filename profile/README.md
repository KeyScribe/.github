# KeyScribe

### Project Description
KeyScribe is a tool for those who are interested in learning piano and would benefit from remote and real-time lessons. Its ability to connect wirelessly to another KeyScribe (keyboard/piano) enables interaction between a teacher and student where the keys being pressed would be transmitted to the other board. Additionally, its sheet music reading and writing functionalities serve as a bridge between the auditory and visual aspects of learning to improve a user’s understanding of music and allow them to compose their own pieces.

## Features
The system consists of two main components: a web application and a hardware module that interfaces with digital pianos.
- Usability:
  * Login and user creation functionality.
  * Interface for connecting devices securely through the settings page for piano sessions.
  * Settings page for managing personal information, connecting/removing keyboards, and adding/removing friends.
- Navigation:
  * User page accessible with correct credentials.
  * Protection against incorrect login information for enhanced security.
  * Keyboards verified with JSON Web Tokens (JWTs) to prevent malicious intrusions.
- Perception:
  * LED strips on the keyboard light up according to pressed keys.
  * Connected keyboards can see what they are playing, enabling collaborative sessions.
- Responsiveness:
  * Predictable reaction to key presses.
  * Immediate signal transmission to the server.
  * LED lights stay lit until the key is released.
  * Support for simultaneous key presses without errors.
- Build Quality:
  * No crashes during regular use.
  * Consistent login behavior.
- Vertical Features:
  * External interface through firmware and GPIO pins.
  * Data handling via MIDI port, WebSocket communication, and LED strip circuits.
  * Implementation of a database for user login information for the webapp.


### Repository Link
#### [Github](https://github.com/KeyScribe)

### Final Demo Link
#### [Youtube] (https://youtu.be/fKgIYZKwktc?si=qjQoP15Gk4qKrKGz)

### Instructions
#### Raspberry Pi module
1. Clone the Repository
2. Navigate to keyscribe-python
3. Connect the LED strip and the MIDI port connection to the Raspberry Pi.
4. Run sockets_midi.py on your Raspberry Pi.
  
#### WebApp
1. Navigate to keyscribe-webapp
2. Navigate to frontend
3. Add the frontend .env file for environment variables (request from a team member)
4. Run 'npm install'
5. Run 'npm run build'
6. Navigate to backend
7. Add the backend .env file for environment variables (request from a team member)
8. Run 'npm run dev' to view live changes while developing
9. Run 'npm test' to run the test suite
