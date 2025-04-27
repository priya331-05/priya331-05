Cross puzzle Game 
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Crossword Puzzle Game</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 20px;
      margin: 0;
      background-color: #f0f8ff;
    }
    .page {
      display: none;
    }
    .active {
      display: block;
    }
    table {
      border-collapse: collapse;
      margin: 20px 0;
    }
    td {
      width: 30px;
      height: 30px;
      border: 1px solid #333;
      text-align: center;
      vertical-align: middle;
    }
    input[type="text"] {
      width: 100%;
      height: 100%;
      text-transform: uppercase;
      border: none;
      text-align: center;
      background-color: #fff;
    }
    .black {
      background-color: black;
    }
    .clues {
      margin-top: 20px;
    }
    .correct {
      background-color: lightgreen;
    }
    .wrong {
      background-color: lightcoral;
    }
    .button {
      padding: 10px 20px;
      font-size: 18px;
      cursor: pointer;
      margin: 10px;
    }
    .winner {
      font-size: 50px;
      text-align: center;
      margin-top: 100px;
      color: green;
    }
  </style>
</head>
<body>

<!-- Page 1: Welcome Page -->
<div id="page1" class="page active">
  <h1>Welcome to the Game Center</h1>
  <button class="button" onclick="goToPage(2)">Play</button>
</div>

<!-- Page 2: Game Selection -->
<div id="page2" class="page">
  <h2>Select a Game</h2>
  <button class="button" onclick="goToPage(3)">Puzzle</button>
  <button class="button" disabled>Crossword</button>
  <button class="button" disabled>Word Game</button>
</div>

<!-- Page 3: Crossword Puzzle -->
<div id="page3" class="page">
  <h2>Simple Crossword Puzzle Game</h2>

  <table id="crossword">
    <tr>
      <td><input type="text" maxlength="1" data-answer="C"></td>
      <td><input type="text" maxlength="1" data-answer="A"></td>
      <td><input type="text" maxlength="1" data-answer="T"></td>
      <td class="black"></td>
      <td><input type="text" maxlength="1" data-answer="D"></td>
    </tr>
    <tr>
      <td class="black"></td>
      <td><input type="text" maxlength="1" data-answer="A"></td>
      <td class="black"></td>
      <td class="black"></td>
      <td><input type="text" maxlength="1" data-answer="O"></td>
    </tr>
    <tr>
      <td><input type="text" maxlength="1" data-answer="D"></td>
      <td><input type="text" maxlength="1" data-answer="O"></td>
      <td><input type="text" maxlength="1" data-answer="G"></td>
      <td class="black"></td>
      <td><input type="text" maxlength="1" data-answer="G"></td>
    </tr>
  </table>

  <button class="button" onclick="checkAnswers()">Submit Answers</button>

  <div class="clues">
    <h3>Clues:</h3>
    <p><strong>Across</strong></p>
    <ul>
      <li>1A: A small domestic animal that purrs</li>
      <li>3A: A loyal pet that barks</li>
    </ul>
    <p><strong>Down</strong></p>
    <ul>
      <li>1D: A word that goes with "and cat"</li>
      <li>5D: Opposite of up</li>
    </ul>
  </div>
</div>

<!-- Page 4: Winner Page -->
<div id="page4" class="page">
  <div class="winner">Congratulations! You Won!</div>
</div>

<script>
  function goToPage(pageNumber) {
    document.querySelectorAll('.page').forEach(page => {
      page.classList.remove('active');
    });
    document.getElementById('page' + pageNumber).classList.add('active');
  }

  function checkAnswers() {
    const cells = document.querySelectorAll('#crossword input');
    let allCorrect = true;
    cells.forEach(cell => {
      const correct = cell.dataset.answer;
      const entered = cell.value.toUpperCase();
      if (!correct) return;
      if (entered === correct) {
        cell.classList.remove('wrong');
        cell.classList.add('correct');
      } else {
        cell.classList.remove('correct');
        cell.classList.add('wrong');
        allCorrect = false;
      }
    });
    if (allCorrect) {
      goToPage(4); // Go to Winner page
    }
  }
</script>

</body>
</html>
