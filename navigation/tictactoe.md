---
layout: page
title: Tic Tac Toe
permalink: /tic-tac-toe/
---

<style>
    .tic-tac-toe {
        display: grid;
        grid-template-columns: repeat(3, 100px);
        grid-template-rows: repeat(3, 100px);
        gap: 5px;
        justify-content: center;
        margin-top: 20px;
    }
    .tic-tac-toe div {
        width: 100px;
        height: 100px;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 2rem;
        background-color: #f0f0f0;
        border: 1px solid #ccc;
        cursor: pointer;
    }
    .tic-tac-toe div:hover {
        background-color: #e0e0e0;
            }
</style>

<div class="tic-tac-toe" id="ticTacToeBoard">
    <div onclick="makeMove(this, 0)"></div>
    <div onclick="makeMove(this, 1)"></div>
    <div onclick="makeMove(this, 2)"></div>
    <div onclick="makeMove(this, 3)"></div>
    <div onclick="makeMove(this, 4)"></div>
    <div onclick="makeMove(this, 5)"></div>
    <div onclick="makeMove(this, 6)"></div>
    <div onclick="makeMove(this, 7)"></div>
    <div onclick="makeMove(this, 8)"></div>
</div>
<script>
    let board = ['', '', '', '', '', '', '', '', ''];
    let currentPlayer = 'X';
    const winningCombinations = [
        [0, 1, 2],
        [3, 4, 5],
        [6, 7, 8],
        [0, 3, 6],
        [1, 4, 7],
        [2, 5, 8],
        [0, 4, 8],
        [2, 4, 6]
    ];
    function makeMove(cell, index) {
        if (board[index] === '') {
            board[index] = currentPlayer;
            cell.innerText = currentPlayer;
            if (checkWin()) {
                setTimeout(() => alert(currentPlayer + ' wins!'), 100);
                resetBoard();
            } else if (board.every(cell => cell !== '')) {
                setTimeout(() => alert('Draw!'), 100);
                resetBoard();
            } else {
                currentPlayer = currentPlayer === 'X' ? 'O' : 'X';
            }
        }
    }
    function checkWin() {
        return winningCombinations.some(combination => {
            return combination.every(index => {
                return board[index] === currentPlayer;
                    });
        });
    }
    function resetBoard() {
        board = ['', '', '', '', '', '', '', '', ''];
        currentPlayer = 'X';
        document.querySelectorAll('.tic-tac-toe div').forEach(cell => {
            cell.innerText = '';
        });
    }
</script>