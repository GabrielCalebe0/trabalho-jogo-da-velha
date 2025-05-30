# trabalho-jogo-da-velha

"""
Tic Tac Toe Player
"""

import math
import copy
new_board = copy.deepcopy(board)

X = "X"
O = "O"
EMPTY = None


def initial_state():
    """
    Returns starting state of the board.
    """
    return [[EMPTY, EMPTY, EMPTY],
            [EMPTY, EMPTY, EMPTY],
            [EMPTY, EMPTY, EMPTY]]


def player(board):
    """
    Returns player who has the next turn on a board.
    """
    #Achata tudo em uma única lista
    flat_board = sum(board, [])
    #Conta a quantidade de X e O para decidir o próximo jogador
    x_count = flat_board.count("X")
    o_count = flat_board.count("O")
    return "X" if x_count <= o_count else "O"


def actions(board):
    """
    Returns set of all possible actions (i, j) available on the board.
    """
    acoes = set()
    for i in range(3):
        for y in range(3):
            if board[i][y] == EMPTY:
                acoes.add((i, y))

    return acoes


def result(board, action):
    """
    Returns the board that results from making move (i, j) on the board.
    """
    i,y = acao
    if board[i][y] is not EMPTY:
        raise Exception("Erro, campo já ocupado")
    new_board = copy.deepcopy(board)
    current_player = player(board)
    new_board[i][y] = current_player
    return new_board


def winner(board):
    """
    Returns the winner of the game, if there is one.
    """
    raise NotImplementedError


def terminal(board):
    """
    Returns True if game is over, False otherwise.
    """
    raise NotImplementedError


def utility(board):
    """
    Returns 1 if X has won the game, -1 if O has won, 0 otherwise.
    """
    raise NotImplementedError


def minimax(board):
    """
    Returns the optimal action for the current player on the board.
    """
    raise NotImplementedError
