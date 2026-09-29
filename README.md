# tic-toc-toe
a simple tic toc toe game
# TIC-TAC-TOE GAME

board = [" " for _ in range(9)]

def print_board():
    print()
    print(board[0] + " | " + board[1] + " | " + board[2])
    print("--+---+--")
    print(board[3] + " | " + board[4] + " | " + board[5])
    print("--+---+--")
    print(board[6] + " | " + board[7] + " | " + board[8])
    print()

def check_winner(player):
    winning_positions = [
        (0, 1, 2),
        (3, 4, 5),
        (6, 7, 8),
        (0, 3, 6),
        (1, 4, 7),
        (2, 5, 8),
        (0, 4, 8),
        (2, 4, 6)
    ]

    for a, b, c in winning_positions:
        if board[a] == board[b] == board[c] == player:
            return True

    return False

def check_draw():
    return " " not in board

# Main game
current_player = "X"

print("===== TIC-TAC-TOE =====")
print("Choose a position from 1 to 9:")
print()
print("1 | 2 | 3")
print("--+---+--")
print("4 | 5 | 6")
print("--+---+--")
print("7 | 8 | 9")

while True:
    print_board()

    try:
        position = int(input(f"Player {current_player}, enter position (1-9): "))

        if position < 1 or position > 9:
            print("Please enter a number between 1 and 9.")
            continue

        position -= 1

        if board[position] != " ":
            print("That position is already occupied!")
            continue

        board[position] = current_player

        if check_winner(current_player):
            print_board()
            print(f"🎉 Player {current_player} wins!")
            break

        if check_draw():
            print_board()
            print("It's a draw!")
            break

        # Change player
        if current_player == "X":
            current_player = "O"
        else:
            current_player = "X"

    except ValueError:
        print("Please enter a valid number.")