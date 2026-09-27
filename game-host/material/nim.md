# Nim

Two players share some heaps of counters; the common start is three heaps of three,
four, and five. On a turn a player takes one or more counters from a single heap. The
player who takes the last counter wins. (In the variant called misere, the player who
takes the last counter loses; agree which before you start.)

## Rules a host keeps

- A turn takes at least one counter, from exactly one heap, never more than the heap
  holds.
- Show every heap's count after each move, for example `heaps: 3 4 5`.
- Say when the game ends and who won.

## Play well

Write each heap's size in binary and add the columns without carrying (exclusive or).
If the total is zero, the player to move is losing against best play; otherwise there
is a move that makes the total zero, and taking it wins.
