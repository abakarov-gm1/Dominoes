import random

stock_pieces = [[i, j] for i in range(7) for j in range(i, 7)]

computer_pieces = [stock_pieces[i] for i in random.sample(range(28), 7)]
for i in computer_pieces:
    stock_pieces.remove(i)

player_pieces = [stock_pieces[i] for i in random.sample(range(21), 7)]
for i in player_pieces:
    stock_pieces.remove(i)


def computer_():
    list_computer = []
    for i in computer_pieces:
        if i[0] == i[1]:
            list_computer.append(i)
    return list_computer


def player_():
    list_player = []
    for i in player_pieces:
        if i[0] == i[1]:
            list_player.append(i)
    return list_player


def result():
    global computer_pieces
    global player_pieces
    global stock_pieces
    max_computer = []
    max_player = []
    if computer_():
        if not computer_():
            pass
        else:
            max_computer = max(computer_())

    if player_():
        if not player_():
            pass
        else:
            max_player = max(player_())

    if computer_() == [] and player_() == []:
        stock_pieces = [[i, j] for i in range(7) for j in range(i, 7)]

        computer_pieces = [stock_pieces[i] for i in random.sample(range(28), 7)]
        for i in computer_pieces:
            stock_pieces.remove(i)

        player_pieces = [stock_pieces[i] for i in random.sample(range(21), 7)]
        for i in player_pieces:
            stock_pieces.remove(i)
        result()

    if max_computer > max_player:
        return max_computer
    if max_computer < max_player:
        return max_player


l = result()
znake = [l]


def status_computer():
    global comp_rand
    if l in player_pieces:
        player_pieces.remove(l)
    count_player = 1
    print('=' * 70)
    print(f'Stock pieces: {len(stock_pieces)}')
    print(f'Computer pieces: {len(computer_pieces)}')
    if len(znake) > 6:
        for i in znake[0:3]:
            print(i, end='')
        print('...', end='')
        for j in znake[-4::]:
            print(j, end='')
    else:
        print(*znake)
    print('')
    print('Your pieces:')
    for i in player_pieces:
        print(f'{count_player}:{i}')
        count_player += 1
    input("Status: Computer is about to make a move. Press Enter to continue...\n")

    if len(computer_pieces) != 0:
        flag_1 = True
        while flag_1:
            try:
                for comp_rand_t in [i for i in range(len(computer_pieces))]:
                    for i in computer_pieces[abs(comp_rand_t) - 1]:
                        if i == znake[0][0]:
                            comp_rand = -comp_rand_t
                            flag_1 = False
                            break
                        if i == znake[-1][-1]:
                            comp_rand = comp_rand_t
                            flag_1 = False
                            break
                if flag_1:
                    comp_rand = 0
                    flag_1 = False
            except IndexError:
                pass

        if comp_rand in [-i for i in range(1, len(computer_pieces) + 1)] \
                or comp_rand in [i for i in range(1, len(computer_pieces) + 1)]:
            flag_2 = True
            while flag_2:
                try:
                    right_comp = computer_pieces[abs(comp_rand) - 1][-1]
                    left_comp = computer_pieces[abs(comp_rand) - 1][0]

                    if int(comp_rand) != abs(int(comp_rand)):
                        if right_comp == znake[0][0]:
                            znake.insert(0, computer_pieces[abs(comp_rand) - 1])
                            computer_pieces.remove(computer_pieces[abs(comp_rand) - 1])
                            flag_2 = False
                        elif left_comp == znake[0][0]:
                            computer_pieces[abs(comp_rand) - 1][-1], computer_pieces[abs(comp_rand) - 1][0] = \
                                computer_pieces[abs(comp_rand) - 1][0], computer_pieces[abs(comp_rand) - 1][-1]
                            znake.insert(0, computer_pieces[abs(comp_rand) - 1])
                            computer_pieces.remove(computer_pieces[abs(comp_rand) - 1])
                            flag_2 = False
                    if abs(comp_rand) == int(comp_rand):
                        if left_comp == znake[-1][-1]:
                            znake.append(computer_pieces[comp_rand - 1])
                            computer_pieces.remove(computer_pieces[comp_rand - 1])
                            flag_2 = False

                        elif right_comp == znake[-1][-1]:
                            computer_pieces[comp_rand - 1][0], computer_pieces[comp_rand - 1][-1] = \
                                computer_pieces[comp_rand - 1][-1], computer_pieces[comp_rand - 1][0]
                            znake.append(computer_pieces[comp_rand - 1])
                            computer_pieces.remove(computer_pieces[comp_rand - 1])
                            flag_2 = False

                    elif comp_rand == 0:
                        flag_2 = False

                except IndexError:
                    pass

        elif comp_rand == 0:
            if stock_pieces != []:
                st = random.randint(0, len(stock_pieces) - 1)
                computer_pieces.append(stock_pieces[st])
                stock_pieces.remove(stock_pieces[st])

    if len(computer_pieces) == 0:
        return 'Status: The game is over. The computer won!'

    right = znake[0][0]
    left = znake[-1][-1]

    if right == left:
        count_right_left = 0
        for i in znake:
            for j in i:
                if right == j:
                    count_right_left += 1
        if count_right_left == 8:
            return "Status: The game is over. It's a draw!"


def status_player():
    try:
        if l in computer_pieces:
            computer_pieces.remove(l)
        count_computer = 1
        print('=' * 70)
        print(f'Stock pieces: {len(stock_pieces)}')
        print(f'Computer pieces: {len(computer_pieces)}')
        if len(znake) > 6:
            for i in znake[0:3]:
                print(i, end='')
            print('...', end='')
            for j in znake[-4::]:
                print(j, end='')
        else:
            print(*znake)
        print('')
        print('Your pieces:')
        for i in player_pieces:
            print(f'{count_computer}:{i}')
            count_computer += 1
        print("Status: It's your turn to make a move. Enter your command.")

        while True:
            status_2 = input()
            while True:
                try:
                    if int(status_2) in [i for i in range(len(player_pieces) + 1)]:
                        break
                    elif int(status_2) in [-i for i in range(len(player_pieces) + 1)]:
                        break
                    else:
                        print('Invalid input. Please try again.')
                        status_2 = input()
                except ValueError:
                    print('Invalid input. Please try again.')
                    status_2 = input()

            flag_1 = False
            for i in player_pieces[abs(int(status_2)) - 1]:
                if int(i) == znake[0][0] or int(i) == znake[-1][-1] or int(status_2) == 0:
                    flag_1 = True

            if flag_1:
                if len(player_pieces) != 0:
                    if int(status_2) in [-i for i in range(len(player_pieces) + 1) if i != 0] \
                            or int(status_2) in [i for i in range(len(player_pieces) + 1) if i != 0]:
                        while True:
                            try:
                                rig = player_pieces[abs(int(status_2)) - 1][1]
                                lef = player_pieces[abs(int(status_2)) - 1][0]

                                if int(status_2) != abs(int(status_2)):
                                    if rig == znake[0][0]:
                                        znake.insert(0, player_pieces[abs(int(status_2)) - 1])
                                        player_pieces.remove(player_pieces[abs(int(status_2)) - 1])
                                        break
                                    elif lef == znake[0][0]:
                                        player_pieces[abs(int(status_2)) - 1][1], player_pieces[abs(int(status_2)) - 1][
                                            0] = \
                                            player_pieces[abs(int(status_2)) - 1][0], \
                                            player_pieces[abs(int(status_2)) - 1][1]
                                        znake.insert(0, player_pieces[abs(int(status_2)) - 1])
                                        player_pieces.remove(player_pieces[abs(int(status_2)) - 1])
                                        break
                                if abs(int(status_2)) == int(status_2):
                                    if lef == znake[-1][-1]:
                                        znake.append(player_pieces[int(status_2) - 1])
                                        player_pieces.remove(player_pieces[int(status_2) - 1])
                                        break

                                    elif rig == znake[-1][-1]:
                                        player_pieces[int(status_2) - 1][1], player_pieces[int(status_2) - 1][0] = \
                                            player_pieces[int(status_2) - 1][0], player_pieces[int(status_2) - 1][1]
                                        znake.append(player_pieces[abs(int(status_2)) - 1])
                                        player_pieces.remove(player_pieces[abs(int(status_2)) - 1])
                                        break

                                if int(status_2) == 0:
                                    break

                                else:
                                    print('Illegal move. Please try again.')
                                    status_2 = input()

                            except IndexError:
                                status_2 = input()

                    elif int(status_2) == 0:
                        if len(stock_pieces) != 0:
                            st = random.randint(0, len(stock_pieces) - 1)
                            player_pieces.append(stock_pieces[st])
                            stock_pieces.remove(stock_pieces[st])

                elif len(player_pieces) == 0:
                    return 'Status: The game is over. You won!'

                right = znake[0][0]
                left = znake[-1][-1]
                if right == left:
                    count_right_left = 0
                    for i in znake:
                        for j in i:
                            if right == j:
                                count_right_left += 1
                    if count_right_left == 8:
                        return "Status: The game is over. It's a draw!"
                break
            else:
                print('Illegal move. Please try again.')
    except IndexError:
        return 'Status: The game is over. You won!'


if len(stock_pieces) != 0:
    if l in player_pieces:
        while True:
            a = status_computer()
            if a == 'Status: The game is over. The computer won!':
                print(a)
                break
            elif a == "Status: The game is over. It's a draw!":
                print(a)
                break
            b = status_player()
            if b == 'Status: The game is over. You won!':
                print(b)
                break
            elif b == "Status: The game is over. It's a draw!":
                print(b)
                break

    elif l in computer_pieces:
        while True:
            v = status_player()
            if v == 'Status: The game is over. You won!':
                print(v)
                break
            elif v == "Status: The game is over. It's a draw!":
                print(v)
                break
            c = status_computer()
            if c == 'Status: The game is over. The computer won!':
                print(c)
                break
            elif c == "Status: The game is over. It's a draw!":
                print(c)
                break
