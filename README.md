<!DOCTYPE html>
<html>
<head>
  <title>예약 링크 열기</title>
</head>
<body>
  <h2>예약된 시간에 링크 자동 접속</h2>
  <label>URL: <input type="text" id="url" placeholder="https://example.com"></label><br><br>
  <label>시간: <input type="time" id="time"></label><br><br>
  <button onclick="schedule()">예약</button>

  <script>
    function schedule() {
      const url = document.getElementById('url').value;
      const time = document.getElementById('time').value;

      const now = new Date();
      const [hh, mm] = time.split(":").map(Number);
      const target = new Date(now.getFullYear(), now.getMonth(), now.getDate(), hh, mm, 0, 0);
      
      const delay = target - now;
      if (delay <= 0) {
        alert("미래 시간을 선택하세요");
        return;
      }

      alert("예약되었습니다!");
      setTimeout(() => {
        window.open(url, "_blank");
      }, delay);
    }
  </script>
</body>
</html>
