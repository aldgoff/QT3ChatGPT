**Specs for the user interface to a web based game of Quantum Tic-Tac-Toe (QT3)**

---

# Visual Elements

## List
- Quantum board
- List of quantum moves (with scroll arrows)
- Classical ensemble (3 x 9 grid for small tic-tac-toe boards)
- List of classical moves
- Guidance text box (whose move, type of move, illegal move warnings, etc.)
- Buttons
- Game state text box (human readable typographic string recording state of the game)

## Placement
Quantum board on the left, guidance text box above it.
List of quantum moves to the right with scroll arrows.
Play buttons to the right of the list of quantum moves (vertical stack).
Game state text box below the quantum board.
Below it the classical ensemble (3x9, rows/cols).
This is an array of light gray squares into which a classical board and moves may be placed.
To its right the listing of classical moves, dimmed and empty unless a classical game is selected.

# Game Play

## Flow Control

### Buttons
- New Game (resets game state and corresponding visual elements)
- Repeat (allows review of current game from the beginning)
- Undo (with keyboard shortcut)
- Redo (with keyboard shortcut)

### Scrolling
Only the listing of classical moves can be scrolled.
Provide up and down arrows to the right of the listing.
They allow convenient review of the game.
A scroll may uncover a _placement move_ or a _collapse move_.
The quantum board and the classical ensemble should change appropriately.
When not at the current move, dim the latter moves.
Allow the game to be redirected from anywhere in the list.
If this happens, the dimmed moves are removed from the listing.

## Moves

After every move, the state of the game must be updated.
Update the quantum board, quantum listing, game state text box on each spooky mark.
For a placement move, the classical ensemble cannot be updated until the 2nd spooky-mark is placed.

### Placement Moves
Clicking on a square on the Quantum Board indicates a move.
If the square has a classical mark, make a 'bleep' sound indicating an illegal move.
If the click is on an empty square or on a spooky mark from previous moves, place the mark.
If the click is on a mark from the current move, undo it.

### Collapse Moves
Clicking on a spooky mark which is on the cycle of a cyclic entanglement causes collapses.
The selected spooky-mark becomes the classical mark in that square.
This forces all the other spooky-marks in the cyclic entanglement to take on classical values.
Every cyclic entanglement has only two possible collapse, but multiple ways to chose which one.

# Quantum Board

## Playing Field
3x3 grid with doubled lines demarking the squares.
Squares number 1 - 9, row/col, in lower right hand coner.
Clean font, smaller than the spooky marks but still readable.

## Spooky Marks
Placement moves consist of indicating two squares.
Indication is with a captial X or a capital O subscripted with the number of the move.
Player X gets the odd number moves, Player O gets the even number moves.
A square may contain multiple spooky marks, so use a medium font size.
An unentangled pair of spooky marks shall be in gray.

## Entanglements
Two pairs of spooky marks which share a square are entangled (semi-entanglement).
Entanglements shall be colored coded in reverse rainbow order.
Dark blue, dark green, dark yellow - almost orange.
The first entanglement will be in blue, the second in green, etc.
A placement move which simply extends an entanglement takes on the same color.
A placement move which connects two entanglements takes on the lower color.
A move which connects a blue entanglement with a green entaglement becomes blue throughout.
If there were three entanglements, do not change the color of the 'orphaned' entanglement.

## Cyclic Entanglements
When a cyclic entanglement occurs, a new move is required, a collapse move.
The Player which did not create the cyclic entanglement gets to choose its collapse.
A cyclic entanglement occurs when there is a closed path around the entangled spooky-marks.
A cyclic entanglement is a kind of self-reference, every move in it depends on itself.
Spooky marks on the cycle shall be displayed in purple.
Spooky makrs off the cycle (stems) shall be displayed in red.
The spooky marks on the cycle should be animated.
Best form would be to cycle around momentarily highlighting each square on the cycle in yellow.
Should spend about half a second on each square.

## Classical Marks
Once a cyclic entanglement occurs, a collapse move is required.
Once the collapse is chosen, all the spooky marks become classical marks.
These marks are also X's and O's, but not subscripted.
Use a large font size that almost fills the square, but doesn't obscure the square number.
Classical marks should be in black.

## List of Quantum Moves
A two column list (X, O) which displays the quantum moves.
A header row, 5 move rows, last square should be grayed out.
Placement moves look like 2-3.
Collapse move bolds one of these, the one which becomes classical.

# Classical Ensemble

## Grid
A game of QT3 can result in upto 27 simultaneous classical games.
The set is called the classical ensemble.
