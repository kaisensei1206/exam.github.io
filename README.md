<!DOCTYPE html>
<html>
<head>
  <title>Lottery</title>
  <link rel="stylesheet" type="text/css" href="mystyle.css">

</head>
<body>
  <h1>Lottery</h1>
  <p>Enter 3 number(1-10)。</p>
  
  <input type="number" id="number1" min="1" max="10">
  <input type="number" id="number2" min="1" max="10">
  <input type="number" id="number3" min="1" max="10">
  
  <button onclick="startLottery()">開獎</button>
  
  <div id="result"></div>
  
  <button onclick="resetGame()">重新開始</button>
  
  <script>
    function startLottery() {
  // 取得user輸入的號碼
        var numbers = [];
        numbers.push(parseInt(document.getElementById('number1').value));
        numbers.push(parseInt(document.getElementById('number2').value));
        numbers.push(parseInt(document.getElementById('number3').value));

  // 檢查user輸入的數值是否有效
  if (isNaN(numbers[0]) || isNaN(numbers[1]) || isNaN(numbers[2]) ||
      numbers[0] < 1 || numbers[0] > 10 || numbers[1] < 1 || numbers[1] > 10 ||
      numbers[2] < 1 || numbers[2] > 10 || numbers[0] === numbers[1] ||
      numbers[0] === numbers[2] || numbers[1] ===numbers[2]) {
    alert('請輸入有效且不重複的數字1-10:)');
    resetGame();
    return;
  }

  // 得獎號碼
  var winNumber1 = Math.floor(Math.random() * 10) + 1;
  var winNumber2 = Math.floor(Math.random() * 10) + 1;
  var winNumber3 = Math.floor(Math.random() * 10) + 1;

  // 比對號碼
  var matchedNumbers = 0;
    if (numbers[0] === winNumber1 || numbers[0] === winNumber2 || numbers[0] === winNumber3) {
    matchedNumbers++;
    }
    if (numbers[1] === winNumber1 || numbers[1] === winNumber2 || numbers[1] === winNumber3) {
    matchedNumbers++;
    }
    if (numbers[2] === winNumber1 || numbers[2] === winNumber2 || numbers[2] === winNumber3) {
    matchedNumbers++;
    }

  // 顯示結果
  var resultDiv = document.getElementById('result');
      resultDiv.innerHTML = '';

      if (matchedNumbers === 3) {
        resultDiv.innerHTML = '恭喜中頭獎獲得1億元';
      } else if (matchedNumbers === 2) {
        resultDiv.innerHTML = '恭喜中貳獎獲得100萬元';
      } else if (matchedNumbers === 1) {
        resultDiv.innerHTML = '恭喜中參獎獲得1000元';
      } else {
        resultDiv.innerHTML = '沒有中獎。';
      }
    }
function resetGame() {
  // 清空輸入欄位
  document.getElementById('number1').value = '';
  document.getElementById('number2').value = '';
  document.getElementById('number3').value = '';
  document.getElementById('result').innerHTML = '';
}

</script>
    
</body>
</html>
