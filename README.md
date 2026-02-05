<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body style="background-color: black;">
  
 <div class="calc">

   <div id="display">0</div>

 <table   border="2" style="width: 350px; height: 350px;   margin: auto;
    margin-top: 50px; background-color: black;">

  <tr>
    <td   class="btn"id="td1">C</td>
    <td   class="btn"id="td1">()</td>
    <td   class="btn"id="td1">%</td>
    <td   class="btn"id="td1">/</td>
  </tr>

  <tr>
    <td  class="btn">7</td>
    <td  class="btn">8</td>
    <td  class="btn">9</td>
    <td  class="btn" id="td1">*</td>
  </tr>

  <tr>
    <td  class="btn">6</td>
    <td  class="btn">5</td>
    <td  class="btn">4</td>
    <td  class="btn" id="td1">-</td>
  </tr>

  <tr>
    <td  class="btn">3</td>
    <td  class="btn">2</td>
    <td  class="btn">1</td>
    <td  class="btn" id="td1">+</td>
 </tr>

 <tr>
  <td  class="btn">.</td>
  <td  class="btn">0</td>
  <td  class="btn">AC</td>
  <td  class="btn" id="td1">=</td>
 </tr>

  </table>
  <style>
    
    
     
        td {
    width: 60px;
    height: 60px;
    border-radius: 50%;
    text-align: center;
    vertical-align: middle;
    border: none; 
    background: #3a3a3a;
    color: white;
    font-size: 20px;
    font-weight: 600; 
    cursor: pointer;
    user-select: none;
      
      
    }
    #td1
    {

    background: #7dd3fc;
    font-size: 24px;
    font-weight: bold;
    width: 65px;
    height: 65px;
}




    

   
#display {
    width:350px;
    height: 100px;

    background: black;
    color: lime;

    font-size: 26px;
    font-weight: bold;

    text-align: right;
    line-height: 80px;

    padding: 0 10px;
    box-sizing: border-box;

    margin-bottom:10px;
    border-radius: 5px;
    
}

.calc {
    width: 300px;
    margin: auto;
}
 </style>

 <script>

let display = document.getElementById("display");

let buttons = document.querySelectorAll(".btn");

buttons.forEach(btn => {

    btn.addEventListener("click", function () {

        let value = this.innerText;

        // Clear
        if (value === "C" ||  value === "AC") {
            display.innerText = "0";
            return;
        }

        // Equal
        if (value === "=") {
            try {
                display.innerText = eval(display.innerText);
            } catch {
                display.innerText = "Error";
            }
            return;
        }

        // Normal Numbers & Operators
        if (display.innerText === "0") {
            display.innerText = value;
        } else {
            display.innerText += value;
        }

    });

});




// Keyboard Support
document.addEventListener("keydown", function (event) {

    let key = event.key;

    // Numbers
    if (key >= 0 && key <= 9) {
        pressKey(key);
    }

    // Operators
    if (key === "+" || key === "-" || key === "*" || key === "/") {
        pressKey(key);
    }

    // Enter = Equal
    if (key === "Enter") {
        pressKey("=");
    }

    // Backspace = Clear One
    if (key === "Backspace") {
        pressKey("C");
    }

    // Escape = All Clear
    if (key === "Escape") {
        pressKey("AC");
    }
});

// Same function for Mouse + Keyboard
function pressKey(value) {

    let display = document.getElementById("display");

    // Clear
    if (value === "C" || value === "AC") {
        display.innerText = "0";
        return;
    }

    // Equal
    if (value === "=") {
        try {
            display.innerText = eval(display.innerText);
        } catch {
            display.innerText = "Error";
        }
        return;
    }

    // Normal Input
    if (display.innerText === "0") {
        display.innerText = value;
    } else {
        display.innerText += value;
    }
}

buttons.forEach(btn => {
    btn.addEventListener("click", function () {
        pressKey(this.innerText);
    });
});
{
    transform: scale(0.92);
}



</script>

</body>
</html>
