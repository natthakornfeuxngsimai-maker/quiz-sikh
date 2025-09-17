<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<title>Quiz ศาสนาซิกข์</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Kanit:wght@400;700&display=swap');

  body {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    margin: 0;
    padding: 0;
    font-family: 'Kanit', sans-serif;
    background: linear-gradient(-45deg, #fff2e6, #ffe0b3, #ffd699, #fff5e6);
    background-size: 400% 400%;
    animation: gradientBG 15s ease infinite;
  }

  @keyframes gradientBG {
    0% {background-position:0% 50%;}
    50% {background-position:100% 50%;}
    100% {background-position:0% 50%;}
  }

  .container {
    width: 90%;
    max-width: 1200px;
    background: rgba(255, 248, 240, 0.95);
    border-radius: 25px;
    padding: 50px;
    box-shadow: 0 20px 60px rgba(0,0,0,0.35);
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
  }

  h1 {
    font-size: 2.5rem;
    color: #e67300;
    text-shadow: 2px 2px 5px #ffcc99;
    margin-bottom: 30px;
    animation: bounce 2s infinite;
  }

  @keyframes bounce {
    0%,100%{transform: translateY(0);}
    50%{transform: translateY(-10px);}
  }

  .question {
    font-size: 1.4rem;
    margin-bottom: 25px;
    padding: 20px;
    background: #fff3e0;
    border-radius: 15px;
    box-shadow: inset 0 3px 8px rgba(0,0,0,0.15);
    width: 100%;
    max-width: 900px;
  }

  .options {
    display: flex;
    flex-direction: column;
    gap: 18px;
    width: 100%;
    max-width: 900px;
  }

  button.opt {
    padding: 15px;
    border: none;
    border-radius: 15px;
    cursor: pointer;
    background: linear-gradient(to right, #ffcc80, #ffb84d);
    font-size: 1.1rem;
    font-weight: bold;
    color: #333;
    box-shadow: 0 5px 10px rgba(0,0,0,0.2);
    transition: all 0.4s ease;
    width: 100%;
  }

  button.opt:hover {
    transform: scale(1.08);
    background: linear-gradient(to right, #ffa64d, #ff9933);
    color: #fff;
  }

  button.opt.correct {
    background: linear-gradient(to right, #b3ffb3, #66ff66) !important;
    color: #006600;
    box-shadow: 0 6px 15px rgba(0,128,0,0.4);
    animation: pop 0.5s ease;
  }

  button.opt.wrong {
    background: linear-gradient(to right, #ff9999, #ff4d4d) !important;
    color: #660000;
    box-shadow: 0 6px 15px rgba(255,0,0,0.4);
    animation: shake 0.5s ease;
  }

  #nextBtn {
    margin-top: 30px;
    padding: 14px 25px;
    background: linear-gradient(to right, #ff9933, #e67300);
    border: none;
    border-radius: 15px;
    cursor: pointer;
    color: #fff;
    font-weight: bold;
    font-size: 1.2rem;
    box-shadow: 0 5px 15px rgba(0,0,0,0.25);
    transition: all 0.3s ease;
  }

  #nextBtn:hover {
    transform: scale(1.1);
    background: linear-gradient(to right, #e67300, #cc5200);
  }

  #score {
    margin-top: 20px;
    font-weight: bold;
    font-size: 1.2rem;
    text-align: center;
    background: linear-gradient(to right, #ff9933, #ffcc00, #ff6600);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    animation: rainbow 3s ease infinite;
  }

  @keyframes rainbow {
    0%{background-position:0%;}
    50%{background-position:100%;}
    100%{background-position:0%;}
  }

  @keyframes pop { 0%{transform:scale(1);} 50%{transform:scale(1.2);} 100%{transform:scale(1);} }
  @keyframes shake { 0%{transform:translateX(0);} 25%{transform:translateX(-5px);} 50%{transform:translateX(5px);} 75%{transform:translateX(-5px);} 100%{transform:translateX(0);} }

</style>
</head>
<body>
<div class="container">
  <h1>🕌 Quiz ศาสนาซิกข์</h1>
  <div id="quiz">
    <div class="question" id="qText"></div>
    <div class="options" id="options"></div>
    <button id="nextBtn">ถัดไป</button>
    <div class="score" id="score"></div>
  </div>
</div>

<script>
const questions = [
  {q:"ผู้ก่อตั้งศาสนาซิกข์คือใคร?", choices:["คุรุ นานัก เดฟ","คุรุ อรชัน เดฟ","คุรุ โกวินด์ สิงห์","มหาราชา รันจิต สิงห์"], answer:0},
  {q:"คัมภีร์ศักดิ์สิทธิ์ของศาสนาซิกข์คืออะไร?", choices:["พระคัมภีร์ไบเบิล","อัลกุรอาน","คัมภีร์เวท","คุรุกรั้นถสาฮิบ"], answer:3},
  {q:"Khalsa ถูกก่อตั้งขึ้นในปีใด?", choices:["ค.ศ1469","ค.ศ1604","ค.ศ1699","ค.ศ1947"], answer:2},
  {q:"5K ของชาวซิกข์ ข้อใดไม่ใช่?", choices:["เคช","คังคา","คารา","โรซารี่"], answer:3},
  {q:"สถานที่ศักดิ์สิทธิ์ที่สุดของชาวซิกข์คือที่ใด?", choices:["ทัชมาฮาล","คุรุดวารา","วัดพระแก้วมรกต","นครเมกกะ"], answer:1},
  {q:"ศาสนาซิกข์ก่อตั้งขึ้นในปีค.ศใด?", choices:["ค.ศ1657","ปลายศตวรรษที่15","ค.ศ1320","ค.ศ927"], answer:1},
  {q:"หลักปฏิบัติสามประการของชาวซิกข์คืออะไร?", choices:["สวดมนต์-ทำงานสุจริต-แบ่งปัน","ภาวนา-บวช-ถือศีล","ไหว้พระ-สวดมนต์-นั่งสมาธิ","ทำทาน-เวียนเทียน-สวดคาถา"], answer:0},
  {q:"คุรุ โกวินด์ สิงห์ เป็นคุรุองค์ที่เท่าไร?", choices:["องค์ที่8","องค์ที่9","องค์ที่10","องค์ที่11"], answer:2},
  {q:"คุรุที่เสียชีวิตเพื่อปกป้องสิทธิ์ทางศาสนาคือใคร?", choices:["คุรุ ฮาร์กริชัน","คุรุ เตฆ บาฮาดูร์","คุรุ ราม ดาส ","คุรุ อังคัด เดฟ"], answer:1},
  {q:"Langar คืออะไร?", choices:["การสวดมนต์ตอนเช้า","ครัวชุมชน","การรับน้ำอมฤต","การแต่งงาน"], answer:1},
  {q:"คุรุกรั้นถสาฮิบ มีสถานะอย่างไรหลังคุรุองค์สุดท้าย?", choices:["เทพเจ้า","คุรุชั่วนิรันดร์","ตำราศักดิ์สิทธิ์","นักบุญ"], answer:1},
  {q:"สัญลักษณ์หลักของศาสนาซิกข์คืออะไร?", choices:["ธรรมจักร","ดาวหกแฉก","คันดา","ดอกบัว"], answer:2},
  {q:"เมืองอมฤตสาร์ถูกก่อตั้งโดยคุรุองค์ใด?", choices:["คุรุ ราม ดาส","คุรุ อังคัด เดฟ","คุรุ ฮาร์กริชัน","คุรุ อรชัน"], answer:0},
  {q:"ศาสดาคนสุดท้ายคือใคร?", choices:["คุรุกรั้นถสาฮิบ","คุรุ ฮาร์ ไร","คุรุ โกวินด์ สิงห์","คุรุ อังคัด เดฟ"], answer:0},
  {q:"คุรุ โกวินด์ สิงห์ มีบทบาทสำคัญคืออะไร?", choices:["เสียชีวิตเพื่อปกป้องสิทธิทางศาสนา","ก่อตั้งคณะนักรบ Khalsa และประกาศให้คุรุกรั้นถสาฮิบ เป็นคุรุองค์สุดท้าย","ศาสดาเยาว์ผู้มีบทบาททางจิตวิญญาณ","ก่อตั้งเมืองอมฤตสาร์และสระศักดิ์สิทธิ์"], answer:1}
];

let current=0;
let score=0;

const qText=document.getElementById("qText");
const options=document.getElementById("options");
const nextBtn=document.getElementById("nextBtn");
const scoreEl=document.getElementById("score");

function showQuestion(){
  const q=questions[current];
  qText.textContent=(current+1)+". "+q.q;
  options.innerHTML="";
  q.choices.forEach((c,i)=>{
    const btn=document.createElement("button");
    btn.className="opt";
    btn.textContent=c;
    btn.onclick=()=>checkAnswer(i,btn);
    options.appendChild(btn);
  });
  scoreEl.textContent=`คะแนน: ${score} / ${questions.length}`;
}

function checkAnswer(i,btn){
  const q=questions[current];
  const btns=options.querySelectorAll("button");
  btns.forEach(b=>b.disabled=true);
  if(i===q.answer){
    btn.classList.add("correct");
    score++;
  }else{
    btn.classList.add("wrong");
    btns[q.answer].classList.add("correct");
  }
  scoreEl.textContent=`คะแนน: ${score} / ${questions.length}`;
}

nextBtn.onclick = () => {
  current++;
  if(current < questions.length){
    showQuestion();
  } else {
    options.innerHTML = "";
    nextBtn.style.display = "none";

    let finalMsg = "";
    if(score === questions.length){
      finalMsg = `🎉 คะแนนรวม: ${score} / ${questions.length} — คุณสุดยอดมาก! เท่านี้คุณก็พร้อมจะเป็นคุรุคนต่อไปแล้ว😂`;
    } else if(score > 5){
      finalMsg = `🎉 คะแนนรวม: ${score} / ${questions.length} — คุณทำดีแล้ว!`;
    } else {
      finalMsg = `🎉 คะแนนรวม: ${score} / ${questions.length} — จบแล้วคุณนี่ไม่ได้เรื่องเลย 😅`;
    }

    qText.textContent = finalMsg;
  }
}

showQuestion();
</script>
</body>
</html>
