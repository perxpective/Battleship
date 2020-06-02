# Battleship
Play battleship and guess the location of the CPU's battleship in 10 tries.

## Setting up
First, I import the `random` module so that I can assign random coordinates of the opponent's hidden battleship. I also delcare the board as a null list.

```python
from random import randint

board = []
```
Using a `for` loop, I print 6 rows and 6 columns to form a list, which is a battleship board for the game.

```python
for x in range(6):
    board.append(["O"] * 6)
```

I declare a function `print_board(board)` so that I can compile the board into a 6x6 grid of '0's. After which, I can print the game title and the board itself.

```python
def random_row(board):
    return randint(0, len(board) - 1)
def random_col(board):
    return randint(0, len(board[0]) - 1)

ship_row = random_row(board)
ship_col = random_col(board)
```

## Assigning Position of the Battleship
In the next few lines of code below, I can use the `randint` function to randomly assign the row and column coordinates of the hidden enemy battleship.

```python
def random_row(board):
    return randint(0, len(board) - 1)
def random_col(board):
    return randint(0, len(board[0]) - 1)

ship_row = random_row(board)
ship_col = random_col(board)
```

## Playing the Game
The player only has 10 turns to guess the coordinates of the enemy battleship. This is done using a `for` loop with a user prompt to guess the row and column respectively, iterated 10 times.

```python
for turn in range(9):
    print ("Turn"), turn
    guess_row = int(input("Guess Row:"))
    guess_col = int(
        input("Guess Col:"))
```

Now, all is left is the `if` statements, which determine the outcome of the game; whether it is game over, the inputs are in range within the board and if the player guesses the coordinates of the battleship correctly.

```python
if guess_row == ship_row and guess_col == ship_col:
        print("Congratulations! You sunk my battleship!")
        break
    else:
        if (guess_row < 0 or guess_row > 5) or (guess_col < 0 or guess_col > 5):
            print("Oops, that's not even in the ocean.")
        elif(board[guess_row][guess_col] == "X"):
            print("You guessed that one already.")
        else:
            print("You missed my battleship!")
            board[guess_row][guess_col] = "X"
    if turn == 8:
        print("Game Over")
    turn =+ 1
    print_board(board)
```
## Dry Run
Missing the Battleship
```
Let's play Battleship!
O O O O O O
O O O O O O
O O O O O O
O O O O O O
O O O O O O
O O O O O O
Turn
Guess Row:2
Guess Col:3
You missed my battleship!
O O O O O O
O O O O O O
O O O X O O
O O O O O O
O O O O O O
O O O O O O
```

## Out of Range
```
O O X O O O
O O O O O O
O O O X O O
O O O O O O
O O O O O O
O O O O X O
Turn
Guess Row:7
Guess Col:8
Oops, that's not even in the ocean.
```

## Game Over :((
```
You missed my battleship!
Game Over
X O O O O O
O O O O O O
O X O O X X
O O O O X O
O O O X O O
O O O X O X
```







