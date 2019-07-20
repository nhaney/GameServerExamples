**Tic Tac Toe**
Client and server communicate via C sockets over TCP in real time.

Game specifications:
- Seperate executable for server and client
- Game is played entirely on server, client just displays game state.
- 2 people connect to game instance at a time. If someone else tries to connect, refuse.
- At the end of the game, both players have the option to play again or quit.
- If there are less than two people on the server, wait until two people connect to play game.
- Once two people connect, one is chosen at random to start.

Networking plan:
- Each space can either have an X, O, or be empty. This means there are 3 ** 9 = 19,683 possible game states. 
- We could easily use a string to represent this state, but is there a better way?
- We need at least 15 bits in order to represent all 19,683 states. How can we make this easy to do?
- We can keep the state in base 3, and turn that number into base 2 to represent the board state. We will then need to serialize and deserialize from from base 3 to two base 2 on either side. 