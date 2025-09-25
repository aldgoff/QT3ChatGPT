**Specs for the user interface to a web based game of Quantum Tic-Tac-Toe (QT3)**

---

# Visual Elements

## List
- Quantum board (3x3 grid of squares, separated by doubled lines, two vertical, two horizontal)
- List of quantum moves (with a **vertical scroll bar**)
- Classical ensemble (3 x 9 grid for small classical tic-tac-toe boards)
- List of classical moves (2 cols, 1 header row (X, O), 5 move rows)
- Guidance text box (whose move, type of move, illegal move warnings, etc.)
- Typical play buttons (**New**, **Repeat**, **Undo**, **Redo**, **Load**)
- Game _state string_ text box (human readable typographic string recording state of the game)
- **Load** button (to the right of the _state string_)

## Placement
Quantum board on the left, guidance text box above it.
List of quantum moves to the right with a vertical scroll bar on right.
Play buttons to the right of the list of quantum moves (vertical stack).
Game state text box below the quantum board.
Below it the classical ensemble (3x9, rows/cols).
This is an array of light gray squares into which a classical board and moves may be placed.
To its right the listing of classical moves, dimmed and empty unless a classical game is selected.
As play progresses, the number of classical games in the classical ensemble changes.
Fill in left to right and top to bottom.
Any light gray square with a classical game in it (board & pieces) is an active 'radio button.'
Clicking on any classical game populates the classical listing for that game.
The selected classical game (if any) is highlighted.
The classical listing is empty if no classical game is selected.
There is no easy algorithm for tracking a selected classical game upon a quantum move.
For now, any change in the quantum state unselects a classical game (radio buttons all off).

## Layout
Use white space strategically, clean, clear, professional.
Visual elements should line up, use the appropriate justification alignment.
The quantum board should have a light gray background to set it off.

## Guidance Text Box
Displays hints and error messages.

Something like this:
- X's move, place a pair of spooky-marks (place first mark)
- X's move, place a pair of spooky-marks (place second mark)
- O's move, collapse the cyclic entanglement (select a spooky-mark)
- Illegal: spooky-mark not on the cycle.
- Illegal: cannot play in a square with a classical mark.
- Illegal: game string not well formed, does not represent a viable game of quantum tic-tac-toe.
- Reviewing: state at move n.

## Game State String
The game state string is shown in an editable text box.
This is a human readable typographic string that encodes the state of the game.
As a text box it is editable, but is intended to be used via copy & paste.
As play proceeds it is filled in.
At any point a Player can copy it and save it or send it to someone else.
Pasting a valid state string and hitting the load button restores the game to that state.
The string is a linear history of the moves, both placement and collapse.

Something like "1:X(1-2),2:0(2-3),3:X(6-7),4:O(3-1),4c:X(O4(3)),5:X(5-9)".
In this example, X had a collapse move as part of O's move #4.
He selected O's spooky-mark O4 to become classical in square 3.
When the game ends, append the score "::X(1.5)-O(0)".

The game state string makes it easy to share interesting games, positions, or puzzles.

# Game Play

## Flow Control

### Buttons (with keyboard shortcuts)
- New Game (resets game state and corresponding visual elements)
- Repeat (allows review of current game from the beginning)
- Undo
- Redo
- Load (restore the game to the state indicated by the _state_string_.

### Scrolling
Only the listing of quantum moves can be scrolled.
Provide a vertical scroll bar to the right of the listing.
It allows convenient review of the game.
A scroll may uncover a _placement move_ or a _collapse move_.
The quantum board and the classical ensemble should change appropriately.
When not at the current move, dim the latter moves.
Allow the game to be redirected from anywhere in the list.
If this happens, the dimmed moves are removed from the listing.

## Moves
After every move, the state of the game must be updated.
Update the quantum board, quantum listing, and game _state string_ on each spooky-mark.
For a placement move, the classical ensemble cannot be updated until the 2nd spooky-mark is placed.

### Placement Moves
Clicking on a square on the quantum board indicates a move.
If the square has a classical mark, make a 'bleep' sound indicating an illegal move.
Also issue a warning in the _guidance box_ about the illegal move.
If the click is on an empty square or on a spooky-mark from previous moves, place the mark.
If the click is on a mark from the current move, undo it.

### Collapse Moves
Clicking on a spooky-mark which is on the cycle of a cyclic entanglement causes collapse.
The selected spooky-mark becomes the classical mark in that square.
This forces all the other spooky-marks in the cyclic entanglement to take on classical values.
Every cyclic entanglement has only two possible collapses, but multiple ways to chose which one.
Selecting any spooky-mark on the cycle converts that mark to a classical value, collapsing the entire cycle.
However, canonicaly, the collapse is applied to the last move in the cycle.
This is the way the collapse move is recorded in the list of quantum moves, and in the _state string_.
A collapse move will reduce the number of classical games in the clasical ensemble, possibly to just one.

# Quantum Board

## Playing Field
3x3 grid with doubled lines demarking the squares.
Squares number 1 - 9, row/col, in lower right hand coner.
Clean font, smaller than the spooky-marks but still readable.

## Spooky-Marks
Placement moves consist of indicating two squares.
Indication is with a captial X or a capital O subscripted with the number of the move.
Player X gets the odd number moves, Player O gets the even number moves.
A square may contain multiple spooky-marks, so use a medium font size.
An unentangled pair of spooky-marks shall be in gray.

## Entanglements
Two pairs of spooky-marks which share a square are entangled (semi-entanglement).
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
Spooky-marks on the cycle shall be displayed in purple.
Spooky marks off the cycle (stems) shall be displayed in red.
The spooky-marks on the cycle should be animated.
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
Each column has two subcolumns, move number on the left, square ID's on the right (1-9).
So under the X header, you have rows something like 1 sq-sq, 3 sq-sq, 5 blank, 7 blank, etc.
So under the O header, you have rows something like 2 sq-sq, 4 sq-sq, 6 blank, 8 blank.
A header row, 5 move rows (1/2, 3/4, 5/6, 7/8, 9/blank), last square should be grayed out.
Placement moves look like 2-3, 7-9, etc.
Collapse move bolds one of these, the one which becomes classical.

# Classical Ensemble

## Grid
A game of QT3 implies upto 27 simultaneous classical games.
It is actually these games which are in superposition.
The set of classical games is called the _classical ensemble_.
It consists of 0 to 27 games of classical tic-tac-toe.
Setup a 3x9 grid of light gray squares to hold a classical board and associated classical moves.
Call this the _ensemble_grid_.
Most of the time most of the light gray squares in the _ensemble_grid_ will be empty.
Fill in left to right, top to bottom order as needed.
When classical games are pruned, reduce the set of classical games.
This probably means you have to recompute the classical games after every quantum move.
Which is too bad, showing doubling, and pruning by contradiction or collapse, has pedagogical value.

## Radio Buttons
Treat each clasical game in the _ensemble_grid_ as a radio button.
Only one classical game can be selected at a time.
Selecting an already selected game deselects it.
The listing of classical moves is populated only if a classical game is selected.
The selection is cleared upon any change in the quantum state.
Either a quantum move (placement, collapse), or another state change action, (undo/redo, new, repeat).
Even scrolling the list of quantum moves will clear the _ensemble_grid_ selection.
