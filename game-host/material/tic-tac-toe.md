# Tic-tac-toe

Two players, X and O, take turns marking one empty square of a three-by-three grid. X
moves first unless the players agree otherwise.

## Naming squares

Squares are named by row and column: rows top, middle, bottom; columns left, center,
right. "Center" alone means the middle square, and the four "corners" are top-left,
top-right, bottom-left, bottom-right. In a chat, show the board after every move as
three lines, with a dot for an empty square:

```
X . O
. X .
. . O
```

## Winning

The first player with three marks in a row, in any row, column, or diagonal, wins. If
all nine squares are filled and nobody has three in a row, the game is a draw.

## Rules a host keeps

- A move must name an empty square; a move onto a filled square is not allowed, and
  the player moves again.
- Players alternate; nobody moves twice in a row.
- After each move, the host says whether the game has been won, drawn, or goes on,
  and whose turn it is.

## Play well

Take the center when it is free. Take a corner rather than an edge. Block any line
where the other player has two marks and the third square is empty. With best play
from both sides the game is always a draw.
