<!DOCTYPE html>
<html lang="ua">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HANGMAN</title>
  </head>
  <body>
    <canvas id="canvas" width="500" height="500"></canvas>
    <script>
      var canvas = document.getElementById("canvas");
      var ctx = canvas.getContext("2d");

      var words = ["лайк", "шлагбаум", "портфоліо", "фотографія", "попкорн", "відео", "рюкзак", "клавіатура"];

      var word = words[Math.floor(Math.random() * words.length)];

      var answerarray = [];
      for (i = 0; i < word.length; i++) {
        answerarray[i] = "_";
      };

      var ww = 0;
      var qqq = 0;
      var man = 0;
      var remainingletters = word.length;
      var remaining = 7;
      var length = word.length;

      var r = function (mans) {
      if (mans === 1) {
                ctx.lineWidth = 5;
                ctx.strokeRect(100, 10, 80, 80);
              } else if (mans === 2) {
                ctx.lineWidth = 5;
                ctx.beginPath();
                ctx.moveTo(140, 90);
                ctx.lineTo(140, 240);
                ctx.stroke();
              } else if (mans === 3) {
                ctx.lineWidth = 5;
                ctx.beginPath();
                ctx.moveTo(140, 240);
                ctx.lineTo(90, 330);
                ctx.stroke();
              } else if (mans === 4) {
                ctx.lineWidth = 5;
                ctx.beginPath();
                ctx.moveTo(140, 240);
                ctx.lineTo(190, 330);
                ctx.stroke();
              } else if (mans === 5) {
                ctx.lineWidth = 5;
                ctx.beginPath();
                ctx.moveTo(140, 140);
                ctx.lineTo(85, 120);
                ctx.stroke();
              } else if (mans === 6) {
                ctx.lineWidth = 5;
                ctx.beginPath();
                ctx.moveTo(140, 140);
                ctx.lineTo(195, 120);
                ctx.stroke();
              };
      };

      while (remainingletters > 0 && remaining > 0) {
        r(man);
        ww = 0;
        qqq = 0;
        alert(answerarray.join(" "));
        
        var guess = prompt("Введіть букву українською мовою або натисніть Cancel щоб припинити гру!");
        if (guess === null) {
          break;
        } else if (guess.length !== 1) {
          alert("Так так так, одну букву!");
        } else {
          for (j = 0; j < word.length; j++) {
            if (guess !== "й", "ц", "у", "к", "е", "н", "г", "ш", "щ", "з", "х", "ї", "ф", "і", "в", "а", "п", "р", "о", "л", "д", "ж", "є", "я", "ч", "с", "м", "и", "т", "ь", "б", "ю") {
              guess = guess.toLowerCase();
            };
            if (word[j] === guess && (answerarray[j] === "_")) {
              answerarray[j] = guess;
              remainingletters--;
              ww++;
              qqq++;
            };
            if (word[j] === guess && (answerarray[j] !== "_")) {
              ww++;
              qqq++;
            };
          };
          };
          if (ww === 0) {
            man++;
          };
          if (qqq === 0) {
            remaining--;
          };
        }; 
        
      alert(answerarray.join(" "));
      if (remainingletters === 0) {
        alert("Уряяя... Слово було " + word + "!");
      } else if (remaining === 0) {
        alert("Ая-яй, ви використали всі свої спроби і не вгадали, тому давайте спочатку! До речі слово було " + word + "!");
      };
    </script>
  </body>
</html>
