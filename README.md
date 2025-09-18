<!doctype html>
<html lang="th">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>หนังสือศาสนาซิกข์</title>
<style>
html,body{margin:0;padding:0;width:100%;height:100%;font-family:"Sarabun","Noto Sans Thai",sans-serif;background:#fff8f0;}
.book{width:100vw;height:100vh;overflow:hidden;position:relative;background:linear-gradient(180deg,#fff8f0,#ffe6cc);}
.page{position:absolute;inset:0;background:rgba(255,248,240,0.95);display:flex;flex-direction:column;align-items:center;justify-content:flex-start;padding:50px;box-sizing:border-box;transition:transform 0.5s ease, opacity 0.5s ease;border-radius:20px;box-shadow:0 10px 30px rgba(0,0,0,0.1);}
.page h1,h2,h3{margin:0 0 12px 0;color:#d36f2f;text-align:center;}
.page h1{font-size:36px;}
.page h3{font-size:20px;color:#e0905f;}
.page .text{max-width:700px;line-height:1.8;color:#333;font-size:17px;text-align:left;white-space:pre-line;}
.off-left{transform:translateX(-100%);opacity:0;}
.off-right{transform:translateX(100%);opacity:0;}
.center{transform:translateX(0);opacity:1;}
.temple{width:90%;max-width:700px;margin-top:30px;}
.footer{position:absolute;bottom:20px;font-size:14px;color:#b36f3f;}
.cover-footer{margin-top:30px;text-align:center;font-size:18px;color:#d36f2f;line-height:1.5;}
</style>
</head>
<body>
<div class="book" id="book"></div>
<script>
const templeSVG = `
<svg class="temple" viewBox="0 0 800 500" xmlns="http://www.w3.org/2000/svg" fill="none" stroke="#d36f2f" stroke-width="4" stroke-linecap="round" stroke-linejoin="round">
  <rect x="200" y="300" width="400" height="120" rx="12"/>
  <path d="M220 300 L400 180 L580 300Z"/>
  <path d="M400 180 C400 120 500 120 540 180"/>
  <path d="M400 180 C400 120 300 120 260 180"/>
  <path d="M400 90 L400 40"/>
  <circle cx="400" cy="30" r="10"/>
  <path d="M220 420 H580"/>
  <path d="M150 420 L160 360 Q180 340 160 300 Q180 320 200 290" stroke-opacity="0.5"/>
  <path d="M650 420 L640 360 Q620 340 640 300 Q620 320 600 290" stroke-opacity="0.5"/>
</svg>`;

const pages = [
{title:"ศาสนาซิกข์",content:`<div class="cover-footer">
เสนอ ครู เกษม<br>
ผู้จัดทำ: ณัฐกรณ์ เฟืองศิไม
</div>`,art:templeSVG},
{title:"คำนำ",content:`ศาสนาซิกข์เป็นศาสนาในอินเดียที่ก่อตั้งขึ้นในปลายศตวรรษที่ 15 ที่แคว้นปัญจาบ เน้นการระลึกถึงพระเจ้าองค์เดียว การทำความดี และการใช้ชีวิตอย่างเท่าเทียมและซื่อสัตย์

หนังสือเล่มนี้รวบรวมข้อมูลสำคัญเกี่ยวกับศาสนาซิกข์ ทั้งศาสดา คัมภีร์ สาวก ศาสนสถาน และสัญลักษณ์ เพื่อให้ผู้อ่านได้เข้าใจอย่างกระชับและชัดเจน`},
{title:"สารบัญ",content:`1. ศาสดา
2. คัมภีร์
3. สาวก / ผู้ศรัทธา
4. ศาสนสถาน
5. สัญลักษณ์
6. บรรณานุกรม`},
{title:"ศาสดา",content:`• คุรุ นานัก เดฟ เป็นผู้ก่อตั้งศาสนา ท่านเกิดในปี ค.ศ. 1469 และสอนว่ามนุษย์ทุกคนเท่าเทียมกัน พระเจ้ามีเพียงองค์เดียว และการดำเนินชีวิตต้องเต็มไปด้วยความเมตตาและความยุติธรรม

• ศาสนาซิกข์มีคุรุทั้งหมด 10 องค์
1. คุรุ นานัก เดฟ – ผู้ก่อตั้ง, เน้นการระลึกถึงพระเจ้า ความเท่าเทียม และชีวิตที่ปฏิบัติได้จริง
2. คุรุ อังคัด เดฟ – ส่งเสริมการใช้อักษรและการศึกษา
3. คุรุ อมัร ดาส – ขยายระบบครัวชุมชน Langar และรวมชุมชน
4. คุรุ ราม ดาส – ก่อตั้งเมืองอมฤตสาร์และสระศักดิ์สิทธิ์
5. คุรุ อรชัน – รวบรวมบทสวดและสร้างวัดทอง Harmandir Sahib; เสียชีวิตเพื่อศาสนา
6. คุรุ ฮาร์โกบินด์ – ยกระดับอำนาจทางโลกและจิตวิญญาณ
7. คุรุ ฮาร์ ไร – รักษาและสืบทอดคำสอน
8. คุรุ ฮาร์กริชัน – ศาสดาเยาว์ผู้มีบทบาททางจิตวิญญาณ
9. คุรุ เตฆ บาฮาดูร์ – เสียชีวิตเพื่อปกป้องสิทธิทางศาสนา
10. คุรุ โกวินด์ สิงห์ – ก่อตั้งคณะนักรบ Khalsa และประกาศให้คัมภีร์ Guru Granth Sahib เป็นคุรุองค์สุดท้าย`},
{title:"คัมภีร์",content:`• Guru Granth Sahib เป็นคัมภีร์ศักดิ์สิทธิ์และถือเป็นคุรุองค์สุดท้าย
• ประกอบด้วยคำสอนจากคุรุซิกข์หลายองค์และนักบุญจากศาสนาอื่น เน้นความเมตตา การเสียสละ และการระลึกถึงพระเจ้า
• คัมภีร์จะถูกวางอย่างสง่างามในคุรุดวาราและใช้ในการสวดมนต์และขับร้องบทเพลงศาสนา`},
{title:"สาวก / ผู้ศรัทธา",content:`• ผู้ศรัทธาเรียกว่า ซิกข์ หมายถึงผู้เรียนรู้หรือผู้ติดตาม
• สาวกซิกข์แบ่งเป็นสองกลุ่มหลัก:
  1. นักบวช – ปฏิบัติศีลเคร่งครัด ยึดถือหลักคำสอนและ 5K
  2. ฆราวาส – ปฏิบัติในชีวิตประจำวัน แบ่งปันและช่วยเหลือผู้อื่น
• หลักปฏิบัติสามประการ:
  • ระลึกถึงพระเจ้าเสมอ
  • ทำงานสุจริต
  • แบ่งปันทรัพย์และช่วยเหลือผู้คน
• Khalsa (คณะนักรบซิกข์) ก่อตั้งโดยคุรุ โกวินด์ สิงห์ เพื่อสร้างอัตลักษณ์และยึดถือศีล 5K`},
{title:"ศาสนสถาน",content:`• คุรุดวารา คือสถานที่ประกอบพิธี สวดมนต์ และรับประทานอาหารร่วมกัน
• วัดทอง Harmandir Sahib เมืองอมฤตสาร์ เป็นศูนย์กลางทางจิตวิญญาณของชาวซิกข์ มีสระศักดิ์สิทธิ์ล้อมรอบและเป็นที่วางคัมภีร์ Guru Granth Sahib
• Langar คือครัวชุมชนที่เปิดให้ทุกคนไม่แบ่งเชื้อชาติหรือชนชั้น รับประทานอาหารร่วมกันเป็นการปฏิบัติเรื่องความเท่าเทียมและการแบ่งปัน`,art:templeSVG},
{title:"สัญลักษณ์",content:`• คันดา Khanda – สัญลักษณ์ศาสนาซิกข์ ประกอบด้วยดาบสองเล่ม วงกลม และดาบตรงกลาง แสดงถึงความยุติธรรม พลัง และความเป็นหนึ่งเดียวของพระเจ้า
• 5K – เครื่องหมายประจำตัวชาวซิกข์ที่รับศีล Khalsa:
  1. เคช (Kesh) – ไว้ผมไม่ตัด
  2. คังคา (Kanga) – หวีไม้เพื่อความสะอาด
  3. คารา (Kara) – กำไลเหล็ก แทนพระเจ้าและวินัย
  4. คัชเชรา (Kachera) – กางเกงในนักรบ แสดงความบริสุทธิ์และพร้อม
  5. คิรปาน (Kirpan) – ดาบสั้น แทนความกล้าหาญและความยุติธรรม`},
{title:"บรรณานุกรม",content:`• Guru Granth Sahib
• แหล่งข้อมูลวิชาการเกี่ยวกับ Sikhism
• เว็บไซต์การศึกษาเกี่ยวกับ Harmandir Sahib`},
{title:"",content:"",art:templeSVG} // ปกหลัง
];

const book=document.getElementById('book');
let current=0;
function render(){
  book.innerHTML='';
  pages.forEach((p,i)=>{
    const el=document.createElement('div');
    el.className='page '+(i<current?'off-left':i>current?'off-right':'center');
    el.innerHTML=`<h1>${p.title}</h1>${p.subtitle?`<h3>${p.subtitle}</h3>`:''}<div class="text">${(p.content||'').replace(/\n/g,'<br>')}</div>${p.art||''}<div class="footer">หน้า ${i+1} / ${pages.length}</div>`;
    book.appendChild(el);
  });
}
render();
function goTo(n){if(n<0||n>=pages.length)return;current=n;render();}
let startX=0,tracking=false;
book.addEventListener('touchstart',e=>{startX=e.touches[0].clientX;tracking=true;});
book.addEventListener('touchend',e=>{if(!tracking)return;tracking=false;const dx=e.changedTouches[0].clientX-startX;if(Math.abs(dx)>50){if(dx<0) goTo(current+1);else goTo(current-1);}});
window.addEventListener('keydown',e=>{if(e.key==="ArrowRight") goTo(current+1);if(e.key==="ArrowLeft") goTo(current-1);});
</script>
</body>
</html>