# fcai.test
for m.elramaly
# Faculty of computers and artificial intelligence - Cairo University
# Number Scrabble Game
# By: Youssef Abd Elhakem ID:20210473
# Under supervisor of Dr\ mohammad El-Ramly
list1 = [1, 2, 3, 4, 5, 6, 7, 8, 9]
list2 = ["_","_","_","_","_","_","_","_","_"]
l1 = []
l2 = []
player1 = False
player2 = False

def Display_list(list, player1_name, player2_name, l1, l2):
    print(f"{player1_name}, you have {l1}")
    print(list)
    print(f"{player2_name}, you have {l2}\n \n ")


def player_input(player_name, list, l):
    player_numbers = []
    while True:
        while True:
            try:
                turn = int(input(f"{player_name}, Enter number between 1 and 9 :\n "))
                break
            except ValueError:
                print("Invalid input")
        if 1 <= turn <= 9:
            if turn in list:
                list[turn - 1] = "_"
                player_numbers.append(turn)
                l += player_numbers
                break
            else:
                print("This number is not in the list")

        else:
            print("Wrong input")
    return l


def check_sum(l, player_win):
    if len(l) >= 3:
        for a in l[0:]:
            for b in l[1:]:
                for c in l[2:]:
                    if a != b and b != c and a != c:
                        if a + b + c == 15:
                            player_win = True

    return player_win


def check_end(list, list2, player1, player2):
    if not player1 and not player2:
        if list == list2:
            print("# Draw #")
            quit()


print("How to play:")
print("is played with the list of numbers between 1 and 9")
print(" Each player takes turns picking a number from the list")
print("Once a number has been picked, it cannot be picked again")
print("If a player has picked three numbers that add up to 15, that player wins the game.However")
print(", if all the numbers are used and no player gets exactly 15, the game is a draw")
player1_name = input("Player 1 Enter your name : \n")
player2_name = input("Player 2 Enter your name : \n")
while True:
    Display_list(list1, player1_name, player2_name, l1, l2)
    while not player1 and not player2:
        player_input(player1_name, list1, l1)
        Display_list(list1, player1_name, player2_name, l1, l2)
        player1 = check_sum(l1, player1)

        if player1:
            print(f" # {player1_name} is the winner #\n")
            break

        check_end(list1, list2, player1, player2)
        player_input(player2_name, list1, l2)
        Display_list(list1, player1_name, player2_name, l1, l2)
        player2 = check_sum(l2, player2)
        if player2:
            print(f" # {player2_name} is the winner #\n")
            break
        check_end(list1, list2, player1, player2)
    while True:
        while True:
            try:
                x = int(input("To play again enter 1, to exit enter 0\n"))
                break
            except ValueError:
                print("Invalid input\n")
        if x == 1:
            player1 = False
            player2 = False
            list1 = [1, 2, 3, 4, 5, 6, 7, 8, 9]
            l1 = []
            l2 = []
            break
        elif x == 0:
            quit()
        else:
            print("Wrong input\n")





