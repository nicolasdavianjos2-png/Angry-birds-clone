<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Simple Calculator</title>
    <style>
        body {
            background: #f4f4f4;
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .calculator {
            background: #fff;
            padding: 20px 30px;
            border-radius: 10px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.2);
            width: 280px;
        }
        .display {
            width: 100%;
            height: 40px;
            margin-bottom: 15px;
            text-align: right;
            font-size: 1.5em;
            border: 1px solid #ddd;
            border-radius: 5px;
            padding: 0 10px;
            box-sizing: border-box;
        }
        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }
        button {
            padding: 15px 0;
            font-size: 1.2em;
            border: none;
            border-radius: 5px;
            background: #eee;
            cursor: pointer;
            transition: background 0.2s;
        }
        button:active {
            background: #ccc;
        }
        .operator {
            background: #f9c74f;
        }
        .equals {
            background: #90be6d;
            color: white;
            grid-column: span 2;
        }
        .clear {
            background: #f94144;
            color: white;
            grid-column: span 2;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <input type="text" class="display" id="display" disabled>
        <div class="buttons">
            <button onclick="appendValue('7')">7</button>
            <button onclick="appendValue('8')">8</button>
            <button onclick="appendValue('9')">9</button>
            <button class="operator" onclick="appendValue('/')">÷</button>

            <button onclick="appendValue('4')">4</button>
            <button onclick="appendValue('5')">5</button>
            <button onclick="appendValue('6')">6</button>
            <button class="operator" onclick="appendValue('*')">×</button>

            <button onclick="appendValue('1')">1</button>
            <button onclick="appendValue('2')">2</button>
            <button onclick="appendValue('3')">3</button>
            <button class="operator" onclick="appendValue('-')">−</button>

            <button onclick="appendValue('0')">0</button>
            <button onclick="appendValue('.')">.</button>
            <button class="operator" onclick="appendValue('+')">+</button>
            <button class="equals" onclick="calculate()">=</button>
            <button class="clear" onclick="clearDisplay()">C</button>
        </div>
    </div>
    <script>
        const display = document.getElementById('display');

        function appendValue(val) {
            display.value += val;
        }

        function clearDisplay() {
            display.value = '';
        }

        function calculate() {
            try {
                display.value = eval(display.value.replace(/÷/g,"/").replace(/×/g,"*").replace(/−/g,"-"));
            } catch(e) {
                display.value = 'Error';
            }
        }
    </script>
</body>
</html>
