# TicTacToe
This is a simple game of TicTacToe with some added features.
import pygame

pygame.init()

win = pygame.display.set_mode((550, 550))
pygame.display.set_caption('TicTacToe')

board = [[0, 0, 0], [0, 0, 0], [0, 0, 0]]

r1c1 = pygame.draw.rect(win, (255, 255, 255), (25, 25, 150, 150))
r1c2 = pygame.draw.rect(win, (255, 255, 255), (200, 25, 150, 150))
r1c3 = pygame.draw.rect(win, (255, 255, 255), (375, 25, 150, 150))
r2c1 = pygame.draw.rect(win, (255, 255, 255), (25, 200, 150, 150))
r2c2 = pygame.draw.rect(win, (255, 255, 255), (200, 200, 150, 150))
r2c3 = pygame.draw.rect(win, (255, 255, 255), (375, 200, 150, 150))
r3c1 = pygame.draw.rect(win, (255, 255, 255), (25, 375, 150, 150))
r3c2 = pygame.draw.rect(win, (255, 255, 255), (200, 375, 150, 150))
r3c3 = pygame.draw.rect(win, (255, 255, 255), (375, 375, 150, 150))

run = True
pr = True

draw_object = 'rect'
r1c1_open = True
r1c2_open = True
r1c3_open = True
r2c1_open = True
r2c2_open = True
r2c3_open = True
r3c1_open = True
r3c2_open = True
r3c3_open = True


def win_check(num):
    for row in board:
        for tile in row:
            if tile == num:
                continue
            else:
                break
        else:
            return True

    for column in range(3):
        for row in board:
            if row[column] == num:
                continue
            else:
                break
        else:
            return True

    for tile in range(3):
        if board[tile][tile] == num:
            continue
        else:
            break
    else:
        return True

    for tile in range(3):
        if board[tile][2 - tile] == num:
            continue
        else:
            break
    else:
        return True


run = True
won = False
while run:
    pygame.time.delay(100)
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            run = False

        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_SPACE:
                won = False
                r1c1_open = True
                r1c2_open = True
                r1c3_open = True
                r2c1_open = True
                r2c2_open = True
                r2c3_open = True
                r3c1_open = True
                r3c2_open = True
                r3c3_open = True

                r1c1 = pygame.draw.rect(win, (255,255,255), (25,25,150,150))
                r1c2 = pygame.draw.rect(win, (255,255,255), (200,25,150,150))
                r1c3 = pygame.draw.rect(win, (255,255,255), (375,25,150,150))
                r2c1 = pygame.draw.rect(win, (255,255,255), (25,200,150,150))
                r2c2 = pygame.draw.rect(win, (255,255,255), (200,200,150,150))
                r2c3 = pygame.draw.rect(win, (255,255,255), (375,200,150,150))
                r3c1 = pygame.draw.rect(win, (255,255,255), (25,375,150,150))
                r3c2 = pygame.draw.rect(win, (255,255,255), (200,375,150,150))
                r3c3 = pygame.draw.rect(win, (255,255,255), (375,375,150,150))

        if event.type == pygame.MOUSEBUTTONUP:
            pos = pygame.mouse.get_pos()

            if won != True:
                if r1c1.collidepoint(pos) and r1c1_open:
                    if draw_object == 'rect':
                        pygame.draw.rect(win, (255, 0, 255), (50, 50, 100, 100))
                        draw_object = 'circle'
                        board[0][0] = 1
                    else:
                        pygame.draw.circle(win, (0, 0, 255), (100, 100), 50)
                        draw_object = 'rect'
                        board[0][0] = 2
                    r1c1_open = False

                if r1c2.collidepoint(pos) and r1c2_open:
                    if draw_object == 'rect':
                        pygame.draw.rect(win, (255, 0, 255), (225, 50, 100, 100))
                        draw_object = 'circle'
                        board[0][1] = 1
                    else:
                        pygame.draw.circle(win, (0, 0, 255), (275, 100), 50)
                        draw_object = 'rect'
                        board[0][1] = 2
                    r1c2_open = False

                if r1c3.collidepoint(pos) and r1c3_open:
                    if draw_object == 'rect':
                        pygame.draw.rect(win, (255, 0, 255), (400, 50, 100, 100))
                        draw_object = 'circle'
                        board[0][2] = 1
                    else:
                        pygame.draw.circle(win, (0, 0, 255), (450, 100), 50)
                        draw_object = 'rect'
                        board[0][2] = 2
                    r1c3_open = False

                if r2c1.collidepoint(pos) and r2c1_open:
                    if draw_object == 'rect':
                        pygame.draw.rect(win, (255, 0, 255), (50, 225, 100, 100))
                        draw_object = 'circle'
                        board[1][0] = 1
                    else:
                        pygame.draw.circle(win, (0, 0, 255), (100, 275), 50)
                        draw_object = 'rect'
                        board[1][0] = 2
                    r2c1_open = False

                if r2c2.collidepoint(pos) and r2c2_open:
                    if draw_object == 'rect':
                        pygame.draw.rect(win, (255, 0, 255), (225, 225, 100, 100))
                        draw_object = 'circle'
                        board[1][1] = 1
                    else:
                        pygame.draw.circle(win, (0, 0, 255), (275, 275), 50)
                        draw_object = 'rect'
                        board[1][1] = 2
                    r2c2_open = False

                if r2c3.collidepoint(pos) and r2c3_open:
                    if draw_object == 'rect':
                        pygame.draw.rect(win, (255, 0, 255), (400, 225, 100, 100))
                        draw_object = 'circle'
                        board[1][2] = 1
                    else:
                        pygame.draw.circle(win, (0, 0, 255), (450, 275), 50)
                        draw_object = 'rect'
                        board[1][2] = 2
                    r2c3_open = False

                if r3c1.collidepoint(pos) and r3c1_open:
                    if draw_object == 'rect':
                        pygame.draw.rect(win, (255, 0, 255), (50, 400, 100, 100))
                        draw_object = 'circle'
                        board[2][0] = 1
                    else:
                        pygame.draw.circle(win, (0, 0, 255), (100, 450), 50)
                        draw_object = 'rect'
                        board[2][0] = 2
                    r3c1_open = False

                if r3c2.collidepoint(pos) and r3c2_open:
                    if draw_object == 'rect':
                        pygame.draw.rect(win, (255, 0, 255), (225, 400, 100, 100))
                        draw_object = 'circle'
                        board[2][1] = 1
                    else:
                        pygame.draw.circle(win, (0, 0, 255), (275, 450), 50)
                        draw_object = 'rect'
                        board[2][1] = 2
                    r3c2_open = False

                if r3c3.collidepoint(pos) and r3c3_open:
                    if draw_object == 'rect':
                        pygame.draw.rect(win, (255, 0, 255), (400, 400, 100, 100))
                        draw_object = 'circle'
                        board[2][2] = 1

                    else:
                        pygame.draw.circle(win, (0, 0, 255), (450, 450), 50)
                        draw_object = 'rect'
                        board[2][2] = 2
                    r3c3_open = False

    
    if win_check(1):
        won = True
        if pr == True:
            print ("Player 1 wins")
            print ("Press SPACEBAR to restart")
            pr = False
    
    if win_check(2):
        won = True
        if pr == True:
            print ("Player 2 wins")
            print ("Press SPACEBAR to restart")
            pr = False


    

    pygame.display.update()

pygame.quit()
