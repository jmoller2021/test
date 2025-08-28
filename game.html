<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>🌴 Florida Chess</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(to bottom, #c8f7f5, #fffde7);
      display: flex;
      flex-direction: column;
      align-items: center;
      margin: 10px;
      color: #004d40;
      user-select: none;
    }

    h1 {
      font-size: 2em;
      margin-bottom: 0.2em;
    }

    #status {
      margin-bottom: 10px;
      font-size: 1.1em;
      font-weight: bold;
    }

    #board {
      display: grid;
      grid-template-columns: repeat(8, 50px);
      grid-template-rows: repeat(8, 50px);
      border: 4px solid #00695c;
      border-radius: 12px;
      box-shadow: 0 0 10px #004d40;
    }

    .square {
      width: 50px;
      height: 50px;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 32px;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }

    .light {
      background-color: #a7d7c5; /* light Florida palm leaf green */
    }

    .dark {
      background-color: #4f8a74; /* dark Florida palm leaf green */
    }

    .highlight {
      background-color: #ffeb3b; /* highlight yellow */
    }

    .possible-move {
      background-color: #ffd54f; /* lighter yellow */
    }

    .selected {
      outline: 3px solid #ffa726; /* orange border */
    }

    #controls {
      margin-top: 15px;
    }

    button {
      background-color: #00897b;
      color: white;
      border: none;
      padding: 10px 18px;
      font-size: 1em;
      border-radius: 8px;
      cursor: pointer;
      margin: 5px;
      user-select: none;
    }

    button:hover, button:focus {
      background-color: #00695c;
      outline: none;
    }

    button:disabled {
      background-color: #b2dfdb;
      cursor: not-allowed;
    }

    @media (max-width: 480px) {
      #board {
        grid-template-columns: repeat(8, 40px);
        grid-template-rows: repeat(8, 40px);
      }
      .square {
        width: 40px;
        height: 40px;
        font-size: 26px;
      }
    }
  </style>
</head>
<body>

  <h1>🌴 Florida Chess 🌴</h1>
  <div id="status">White to move</div>
  <div id="board" role="grid" aria-label="Florida themed chessboard"></div>

  <div id="controls">
    <button id="resetBtn">Restart Game</button>
  </div>

  <script>
    // Board and game state
    const boardElem = document.getElementById('board');
    const statusElem = document.getElementById('status');
    const resetBtn = document.getElementById('resetBtn');

    // Unicode chess pieces (white and black)
    const piecesUnicode = {
      'r': '♜', 'n': '♞', 'b': '♝', 'q': '♛', 'k': '♚', 'p': '♟',
      'R': '♖', 'N': '♘', 'B': '♗', 'Q': '♕', 'K': '♔', 'P': '♙'
    };

    // Initial board setup: uppercase = White, lowercase = Black
    let board = [
      ['r','n','b','q','k','b','n','r'],
      ['p','p','p','p','p','p','p','p'],
      ['','','','','','','',''],
      ['','','','','','','',''],
      ['','','','','','','',''],
      ['','','','','','','',''],
      ['P','P','P','P','P','P','P','P'],
      ['R','N','B','Q','K','B','N','R']
    ];

    // Game variables
    let selectedSquare = null; // [row, col]
    let possibleMoves = [];
    let currentTurn = 'white'; // 'white' or 'black'
    let gameOver = false;

    // Utility functions
    function isUpperCase(char) {
      return char === char.toUpperCase() && char !== '';
    }

    function isLowerCase(char) {
      return char === char.toLowerCase() && char !== '';
    }

    function isWhitePiece(piece) {
      return piece && isUpperCase(piece);
    }

    function isBlackPiece(piece) {
      return piece && isLowerCase(piece);
    }

    function oppositeColor(color) {
      return color === 'white' ? 'black' : 'white';
    }

    // Convert board coords to algebraic notation (e.g. [0,0] = 'a8')
    function coordsToNotation(row, col) {
      const files = 'abcdefgh';
      return files[col] + (8 - row);
    }

    // Render the board UI
    function renderBoard() {
      boardElem.innerHTML = '';
      for(let row=0; row<8; row++) {
        for(let col=0; col<8; col++) {
          const square = document.createElement('div');
          square.classList.add('square');
          // Florida green themed checkerboard coloring
          if ((row + col) % 2 === 0) {
            square.classList.add('light');
          } else {
            square.classList.add('dark');
          }
          square.dataset.row = row;
          square.dataset.col = col;
          square.setAttribute('role', 'gridcell');
          square.setAttribute('aria-label', `Square ${coordsToNotation(row,col)}`);

          // Add piece if any
          const piece = board[row][col];
          if (piece) {
            square.textContent = piecesUnicode[piece];
            square.setAttribute('aria-live', 'polite');
            square.setAttribute('aria-atomic', 'true');
          }

          // Highlight selected or possible moves
          if (selectedSquare && selectedSquare[0] === row && selectedSquare[1] === col) {
            square.classList.add('selected');
          } else if (possibleMoves.some(m => m[0] === row && m[1] === col)) {
            square.classList.add('possible-move');
          }

          // Add click listener
          square.addEventListener('click', () => onSquareClick(row, col));
          boardElem.appendChild(square);
        }
      }
    }

    // Check if position is inside board limits
    function insideBoard(row, col) {
      return row >= 0 && row < 8 && col >= 0 && col < 8;
    }

    // Get piece color
    function getPieceColor(piece) {
      if (!piece) return null;
      return isWhitePiece(piece) ? 'white' : 'black';
    }

    // Movement logic for each piece type
    // Returns array of valid moves [row, col]
    function getMoves(row, col) {
      const piece = board[row][col];
      if (!piece) return [];
      const color = getPieceColor(piece);
      const moves = [];

      function addMove(r, c) {
        if (!insideBoard(r,c)) return false;
        const target = board[r][c];
        if (!target) {
          moves.push([r,c]);
          return true;
        } else {
          if (getPieceColor(target) !== color) {
            moves.push([r,c]);
          }
          return false;
        }
      }

      switch(piece.toLowerCase()) {
        case 'p': {
          // Pawns move direction
          const dir = (color === 'white') ? -1 : 1;
          // 1 step forward if empty
          if (insideBoard(row+dir,col) && !board[row+dir][col]) {
            moves.push([row+dir, col]);
            // 2 steps on first move
            const startRow = (color === 'white') ? 6 : 1;
            if (row === startRow && !board[row+dir*2][col]) {
              moves.push([row+dir*2, col]);
            }
          }
          // Captures
          for(let dc of [-1,1]) {
            const r = row+dir, c = col+dc;
            if (insideBoard(r,c)) {
              const target = board[r][c];
              if (target && getPieceColor(target) !== color) {
                moves.push([r,c]);
              }
            }
          }
          break;
        }
        case 'r': {
          // Rook moves: straight lines
          const directions = [[1,0],[-1,0],[0,1],[0,-1]];
          directions.forEach(([dr,dc]) => {
            let r = row+dr, c = col+dc;
            while (insideBoard(r,c)) {
              if (!board[r][c]) {
                moves.push([r,c]);
              } else {
                if (getPieceColor(board[r][c]) !== color) moves.push([r,c]);
                break;
              }
              r += dr;
              c += dc;
            }
          });
          break;
        }
        case 'n': {
          // Knight moves (L shape)
          const knightMoves = [[-2,-1],[-2,1],[-1,-2],[-1,2],[1,-2],[1,2],[2,-1],[2,1]];
          knightMoves.forEach(([dr,dc]) => {
            const r = row+dr, c = col+dc;
            if (insideBoard(r,c)) {
              if (!board[r][c] || getPieceColor(board[r][c]) !== color) {
                moves.push([r,c]);
              }
            }
          });
          break;
        }
        case 'b': {
          // Bishop moves: diagonals
          const directions = [[1,1],[1,-1],[-1,1],[-1,-1]];
          directions.forEach(([dr,dc]) => {
            let r = row+dr, c = col+dc;
            while (insideBoard(r,c)) {
              if (!board[r][c]) {
                moves.push([r,c]);
              } else {
                if (getPieceColor(board[r][c]) !==
