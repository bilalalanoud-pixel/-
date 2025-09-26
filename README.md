<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <title>لعبة سباق الفيزياء - الوحدة الثانية</title>
  <style>
    body { font-family: Tahoma, sans-serif; text-align: center; direction: rtl; background: #f9f9f9; }
    h1 { color: #333; }
    #race { margin: 20px auto; width: 80%; height: 200px; border: 2px solid #333; position: relative; background: #fff; }
    .runner { position: absolute; height: 30px; background: #4CAF50; color: white; padding: 5px; border-radius: 5px; }
    #questionBox { margin-top: 20px; display: none; }
    .option { display: block; margin: 10px auto; padding: 10px; background: #eee; border: none; cursor: pointer; width: 60%; border-radius: 8px; }
    .correct { background: #4CAF50; color: white; }
    .wrong { background: #f44336; color: white; }
  </style>
</head>
<body>
  <h1>🏁 لعبة سباق الفيزياء - مراجعة الوحدة الثانية</h1>
  <button onclick="startRace()">ابدأ السباق</button>
  <div id="race"></div>
  <div id="questionBox">
    <h2 id="question"></h2>
    <div id="answers"></div>
    <p id="feedback"></p>
  </div>

  <script>
    const students = ["سارة", "نورة", "ريم", "هند", "لينا", "جود", "العنود", "شهد"];
    const questions = [
      {q:"الحركة الاهتزازية تعتبر …", options:["حركة دورية","حركة انتقالية","حركة منتظمة"], answer:0},
      {q:"الزمن الدوري هو الزمن اللازم ل…", options:["إكمال دورة كاملة","نصف دورة","ربع دورة"], answer:0},
      {q:"الموجة الميكانيكية تحتاج …", options:["وسط مادي","لا تحتاج وسط","تحتاج كهرباء"], answer:0},
      {q:"الصوت يعتبر موجة …", options:["ميكانيكية","ضوئية","كهربائية"], answer:0},
      {q:"الطول الموجي هو المسافة بين …", options:["قمتين متتاليتين","أي نقطتين","بداية ونهاية"], answer:0},
      {q:"من خصائص الموجات:", options:["السعة","التردد","الطول الموجي","كل ما سبق"], answer:3}
    ];

    function startRace() {
      document.getElementById("race").innerHTML = "";
      const randomIndex = Math.floor(Math.random()*students.length);
      const chosen = students[randomIndex];
      const runner = document.createElement("div");
      runner.className = "runner";
      runner.style.top = (30+randomIndex*25) + "px";
      runner.style.left = "0px";
      runner.innerText = chosen;
      document.getElementById("race").appendChild(runner);

      let pos = 0;
      const move = setInterval(()=>{
        if(pos >= 500) {
          clearInterval(move);
          showQuestion();
        } else {
          pos+=10;
          runner.style.left = pos + "px";
        }
      },50);
    }

    function showQuestion(){
      const q = questions[Math.floor(Math.random()*questions.length)];
      document.getElementById("question").innerText = q.q;
      const answersDiv = document.getElementById("answers");
      answersDiv.innerHTML = "";
      document.getElementById("feedback").innerText="";
      q.options.forEach((opt,i)=>{
        const btn = document.createElement("button");
        btn.className = "option";
        btn.innerText = opt;
        btn.onclick=()=>{
          if(i===q.answer){
            btn.className="option correct";
            document.getElementById("feedback").innerText="✔️ إجابة صحيحة";
          } else {
            btn.className="option wrong";
            document.getElementById("feedback").innerText="❌ خطأ، الصحيح: " + q.options[q.answer];
          }
        };
        answersDiv.appendChild(btn);
      });
      document.getElementById("questionBox").style.display="block";
    }
  </script>
</body>
</html>
# -
مدري 
