<!DOCTYPE html><html lang="th">
<head>
  <meta charset="UTF-8" />
  <title>เว็บสะสมแต้ม</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <style>
    body { font-family: sans-serif; background:#f5f5f5; padding:20px }
    .card { background:#fff; padding:20px; border-radius:12px; max-width:420px; margin:auto }
    input, button { padding:10px; border-radius:8px; margin:4px; width:100% }
    button { border:none }
  </style>
</head>
<body>
  <div class="card">
    <h2>ระบบสะสมแต้ม</h2><label>ชื่อผู้ใช้</label>
<input id="username" placeholder="กรอกชื่อ" />
<button onclick="saveUser()">บันทึกชื่อ</button>

<p>ผู้ใช้: <b id="showUser">-</b></p>
<p>แต้มของคุณ: <b id="points">0</b></p>

<button onclick="addPoint()">➕ เพิ่มแต้ม</button>
<button onclick="redeem()">🎁 แลกของ (10 แต้ม)</button>
<button onclick="resetAll()">♻️ รีเซ็ต</button>

  </div>  <script>
    let points = Number(localStorage.getItem('points')) || 0;
    let user = localStorage.getItem('user') || '-';

    document.getElementById('points').innerText = points;
    document.getElementById('showUser').innerText = user;

    function saveUser() {
      const u = document.getElementById('username').value;
      if(u){
        localStorage.setItem('user', u);
        document.getElementById('showUser').innerText = u;
      }
    }

    function addPoint() {
      points++;
      localStorage.setItem('points', points);
      document.getElementById('points').innerText = points;
    }

    function redeem() {
      if(points >= 10) {
        points -= 10;
        alert('แลกของสำเร็จ!');
      } else {
        alert('แต้มไม่พอ');
      }
      localStorage.setItem('points', points);
      document.getElementById('points').innerText = points;
    }

    function resetAll(){
      if(confirm('ล้างข้อมูลทั้งหมด?')){
        localStorage.clear();
        location.reload();
      }
    }
  </script></body>
</html>
