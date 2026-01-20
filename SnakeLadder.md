import random as r

n_players = int(input("Enter the number of players: "))
d = {}

snake = {45:7, 51:10, 38:20, 76:54, 97:61, 91:73}
ladders = {5:58, 14:49, 42:60, 53:72, 64:83, 75:94}

# Player input
for p in range(n_players):
    name = input("Enter the name of the player: ")
    d[name] = 0

won = False

while not won:
    for player in d:
        print(player, end=" ")
        input("press Enter to roll the dice ")

        dice = r.randint(1, 6)
        print(f"Dice => {dice}")

        if d[player] + dice <= 100:
            d[player] += dice
        else:
            print("Exceeding 100, try again")

        if d[player] in snake:
            print("Oops!! you got bitten by snake")
            d[player] = snake[d[player]]

        elif d[player] in ladders:
            print("Congrats!! you got a ladder")
            d[player] = ladders[d[player]]

        print(player, "you are at", d[player])

        if d[player] == 100:
            print("🎉 Congrats, you won!", player)
            won = True
            break
