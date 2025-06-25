DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>Website Kelas 9B</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background-color: #fff6ec;
      color: #000;
      margin: 0;
      padding: 0;
      transition: background-color 0.3s, color 0.3s;
    }
    body.dark-mode {
      background-color: #1e1e1e;
      color: #f0f0f0;
    }
    header, footer {
      background-color: #a0522d;
      color: white;
      text-align: center;
      padding: 15px;
    }
    nav {
      background-color: #f5d5a1;
      padding: 10px;
      text-align: center;
    }
    .menu-btn {
      margin: 6px;
      padding: 10px 18px;
      background-color: #f0c38e;
      border: none;
      border-radius: 12px;
      font-weight: bold;
      cursor: pointer;
    }
    .menu-btn:hover {
      background-color: #dfa96b;
    }
    #content {
      padding: 25px;
      min-height: 300px;
    }
    .hidden {
      display: none;
    }
    input, textarea {
      padding: 8px;
      width: 100%;
      margin: 5px 0;
    }
    button {
      padding: 8px 15px;
      border-radius: 8px;
      cursor: pointer;
    }
    .toggle-theme {
      background-color: #333;
      color: white;
      border: none;
      float: right;
      margin: -10px 10px 10px 0;
    }
  </style>
</head>
<body>

<header>
  <h1>SMPN 1 PANGKALAN LADA</h1>
  <h2>Website Kelas 9B</h2>
</header>

<nav>
  <button class="menu-btn" onclick="showContent('struktur')">Struktur Kelas</button>
  <button class="menu-btn" onclick="showContent('anggota')">Anggota</button>
  <button class="menu-btn" onclick="showContent('komentar')">Komentar</button>
  <button class="menu-btn" onclick="showContent('login')">Login Admin</button>
  <button class="toggle-theme" onclick="toggleTheme()">🌙/☀️</button>
</nav>

<div id="content">
  <h2>Selamat datang di Website Kelas 9B!</h2>
  <p>Klik menu di atas untuk melihat informasi kelas!</p>
</div>

<footer>
  <p>Website Kelas 9B | By: APutraN</p>
  <p><a href="https://instagram.com/namaakun" target="_blank">Instagram</a> | <a href="https://tiktok.com/@namaakun" target="_blank">TikTok</a></p>
</footer>

<script>
  const comments = [];

  function showContent(menu) {
    let html = "";
    if (menu === 'struktur') {
      html = "<h2>Struktur Kelas</h2><ul><li>Ketua: Putra</li><li>Wakil: Rani</li></ul>";
    } else if (menu === 'anggota') {
      html = "<h2>Anggota Kelas 9B</h2><ol><li>Putra</li><li>Rani</li><li>Budi</li></ol>";
    } else if (menu === 'komentar') {
      html = `
        <h2>Komentar Siswa</h2>
        <form onsubmit="submitComment(event)">
          <input type="text" id="nama" placeholder="Nama" required><br>
          <textarea id="pesan" placeholder="Pesanmu..." required></textarea><br>
          <button type="submit">Kirim</button>
        </form>
        <div id="commentList"></div>
      `;
    } else if (menu === 'login') {
      html = `
        <h2>Login Admin</h2>
        <form onsubmit="adminLogin(event)">
          <input type="password" id="adminPass" placeholder="Password Admin"><br>
          <button type="submit">Login</button>
        </form>
        <div id="adminData" class="hidden">
          <h3>Data Komentar:</h3>
          <pre id="allComments"></pre>
        </div>
      `;
    }
    document.getElementById("content").innerHTML = html;
  }

  function submitComment(e) {
    e.preventDefault();
    const nama = document.getElementById("nama").value;
    const pesan = document.getElementById("pesan").value;
    comments.push({ nama, pesan });
    document.getElementById("commentList").innerHTML += `<p><strong>${nama}</strong>: ${pesan}</p>`;
    document.getElementById("nama").value = "";
    document.getElementById("pesan").value = "";
  }

  function adminLogin(e) {
    e.preventDefault();
    const pass = document.getElementById("adminPass").value;
    if (pass === "admin123") {
      document.getElementById("adminData").classList.remove("hidden");
      document.getElementById("allComments").textContent = JSON.stringify(comments, null, 2);
    } else {
      alert("Password salah!");
    }
  }

  function toggleTheme() {
    document.body.classList.toggle("dark-mode");
  }
</script>

</body>
</html>
