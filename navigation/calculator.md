---
layout: page
title: Calculator
search_exclude: true
permalink: /my_calculator/
---

<head>
  <style>
    .calculator {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 10px;
      max-width: 400px;
      margin: 0 auto;
      padding: 20px;
      border: 1px solid #ccc;
      border-radius: 10px;
      background-color: #f9f9f9;
    }
    .two-spaces {
      grid-column: span 2;
    }
    .three-spaces {
      grid-column: span 3;
      background-color: #ff4d4d;
    }
    .four-spaces {
      grid-column: span 4;
      background-color: #ff4d4d;
    }
    .display {
      grid-column: 1 / -1;
      background-color: rgba(0, 0, 0, .75);
      display: flex;
      align-items: flex-end;
      justify-content: space-around;
      flex-direction: column;
      padding: 10px;
      word-wrap: break-word;
      word-break: break-all;
    }
    input {
      width: 100%;
      border: none;
      font-size: 1.5rem;
      background-color: transparent;
      color: white;
    }
    .operator {
      background-color: #33cc33;
      color: white;
    }
    .blue-button {
      background-color: #3399ff;
      color: white;
    }
    button {
      padding: 20px;
      font-size: 1.5rem;
      border: none;
      border-radius: 5px;
      background-color: #e0e0eb;
      cursor: pointer;
    }
    button:hover {
      background-color: #d4d4d4;
    }
  </style>
</head>

<body>
  <div class="calculator">
    <div class="display">
      <input type="text" id="result" value="0" disabled>
    </div>
    <button class ="three-spaces" onclick="deleteLastCharacter()">C</button>
    <button class="operator" onclick="appendSymbol('/')">÷</button>
    <button onclick="appendSymbol('1')">1</button>
    <button onclick="appendSymbol('2')">2</button>
    <button onclick="appendSymbol('3')">3</button>
    <button class="operator" onclick="appendSymbol('*')">*</button>
    <button onclick="appendSymbol('4')">4</button>
    <button onclick="appendSymbol('5')">5</button>
    <button onclick="appendSymbol('6')">6</button>
    <button class="operator" onclick="appendSymbol('+')">+</button>
    <button onclick="appendSymbol('7')">7</button>
    <button onclick="appendSymbol('8')">8</button>
    <button onclick="appendSymbol('9')">9</button>
    <button class="operator" onclick="appendSymbol('-')">-</button>
    <button onclick="appendSymbol('.')">.</button>
    <button onclick="appendSymbol('0')">0</button>
    <button id="equals" class="two-spaces" onclick="calculate()">=</button>
    <button class="blue-button" onclick="appendSymbol('^')">^</button>
    <button class="blue-button" onclick="appendPi()">π</button>
    <button class="blue-button" onclick="calculateSquareRoot()">√</button>
    <button class="blue-button" onclick="startPiGame()">Pi Game</button>
    <button id="clear" class="four-spaces" onclick="clearDisplay()">AC</button>
  </div>

  <script>
    let currentInput = '';
    const piDigits = "3.14159265358979323846264338327950288419716939937510582097494459230781640628620899862803482534211706798214808651328230664709384460955058223172 53594081284811174502841027019385211055596446229489549303819644288109756659334461284756482337867831652712019091456485669234603486104543266482133936072602491412737245870066 0631558817488152092096282925409171536436789259036001133053054882046652138414695194151160943305727036575959195309218611738193261179 310511854807446237996274956735188575272489122793818301194912";
    let currentPiIndex = 2; // Start after "3."

    function appendSymbol(symbol) {
      currentInput += symbol;
      updateDisplay(currentInput);
    }

    function calculate() {
      try {
        const result = eval(currentInput.replace('^', '**'));
        updateDisplay(result);
        currentInput = result.toString();
      } catch (error) {
        updateDisplay('Error');
        currentInput = '';
      }
    }

    function clearDisplay() {
      currentInput = '';
      updateDisplay('0');
    }

    function updateDisplay(content) {
      document.getElementById('result').value = content;
    }

    function appendPi() {
      currentInput += Math.PI;
      updateDisplay(currentInput);
    }

    function calculateSquareRoot() {
      try {
        const result = Math.sqrt(eval(currentInput));
        updateDisplay(result);
        currentInput = result.toString();
      } catch (error) {
        updateDisplay('Error');
        currentInput = '';
      }
    }

    function startPiGame() {
      currentPiIndex = 2;
      updateDisplay(piDigits.substring(0, currentPiIndex));
      setTimeout(promptNextPiDigit, 1000);
    }

    function promptNextPiDigit() {
      let display = document.getElementById('result');
      let userInput = prompt("Enter the next digit of Pi:");
      if (userInput === piDigits[currentPiIndex]) {
        currentPiIndex++;
        if (currentPiIndex === piDigits.length) {
          updateDisplay('Great Job, you know ' + piDigits.length + ' digits of Pi!');
        } else {
          updateDisplay(piDigits.substring(0, currentPiIndex));
          setTimeout(promptNextPiDigit, 1000);
        }
      } else {
        updateDisplay('Game Over, Try Again!');
      }
    }

    function deleteLastCharacter() {
      currentInput = currentInput.slice(0, -1);
      updateDisplay(currentInput || '0');
    }
  </script>
</body>