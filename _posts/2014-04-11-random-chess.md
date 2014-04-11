---
layout: post
title:  "A random chess game or: chessboard.js and chess.js are friends"
date:   2014-04-10
---

Straight from the `chessboard.js` examples page, `chess.js` plays a random game against itself for your amusement. 

<div id="randomGameSample" style="width: 400px"></div>


<script src="js/chess.js"></script>
<script>
    var board,
    game = new Chess();

    var makeRandomMove = function() {
        var possibleMoves = game.moves();

         // exit if the game is over
        if (game.game_over() === true ||
            game.in_draw() === true ||
            possibleMoves.length === 0) return;

        var randomIndex = Math.floor(Math.random() * possibleMoves.length);
        game.move(possibleMoves[randomIndex]);
        board.position(game.fen());

        window.setTimeout(makeRandomMove, 500);
    };

    board = new ChessBoard('randomGameSample', 'start');

    window.setTimeout(makeRandomMove, 500);
</script>
