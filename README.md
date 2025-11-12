# Xucxac-demo
Mô phỏng tưng xúc xắc
<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Demo xúc xắc</title>
  <style>
    body { font-family: Arial, sans-serif; text-align: center; background: #222; color: white; }
    button { padding: 10px 20px; border: none; border-radius: 8px; background: #28a745; color: white; margin: 10px; font-size: 18px; }
    #result { font-size: 50px; margin: 20px; }
    #adminPanel { display: none; margin-top: 20px; background: #333; padding: 15px; border-radius: 10px; }
    input { padding: 8px; font-size: 16px; margin: 5px; }
  </style>
</head>
<body>

  <h1>🎲 Mô phỏng tung xúc xắc</h1>
  <p>Nhấn nút để tung xúc xắc!</p>
  <button onclick="rollDice()">Tung xúc xắc</button>
  <div id="result">🎲</div>

  <hr>

  <button onclick="showAdmin()">🔐 Đăng nhập Admin</button>
  <div id="adminLogin" style="display:none;">
    <input type="password" id="adminPass" placeholder="Nhập mật khẩu admin">
    <button onclick="loginAdmin()">Đăng nhập</button>
  </div>

  <div id="adminPanel">
    <h2>👑 Khu vực quản trị</h2>
    <button onclick="reset()">Reset kết quả</button>
    <button onclick="changeColor()">Đổi màu nền</button>
    <p id="adminMsg"></p>
  </div>

  <script>
    const ADMIN_PASSWORD = "admin123"; // 👉 Bạn có thể đổi mật khẩu ở đây
    let diceCount = 0;

    function rollDice() {
      const num = Math.floor(Math.random() * 6) + 1;
      document.getElementById("result").innerText = "🎲 " + num;
      diceCount++;
    }

    function showAdmin() {
      document.getElementById("adminLogin").style.display = "block";
    }

    function loginAdmin() {
      const pass = document.getElementById("adminPass").value;
      if (pass === ADMIN_PASSWORD) {
        document.getElementById("adminLogin").style.display = "none";
        document.getElementById("adminPanel").style.display = "block";
        document.getElementById("adminMsg").innerText = "Chào mừng admin!";
      } else {
        alert("Sai mật khẩu!");
      }
    }

    function reset() {
      diceCount = 0;
      document.getElementById("result").innerText = "🎲";
      document.getElementById("adminMsg").innerText = "Đã reset kết quả.";
    }

    function changeColor() {
      const color = "#" + Math.floor(Math.random()*16777215).toString(16);
      document.body.style.backgroundColor = color;
    }
  </script>

</body>
</html>
