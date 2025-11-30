# *Welcome to Matthew & Velia Wedding Celebration*

<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Cari Meja Anda – Pernikahan</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <div class="container">
    <h1>Selamat Datang di Pernikahan</h1>
    <p>Silakan cari nama Anda untuk mengetahui nomor meja duduk.</p>
    <input type="text" id="searchInput" placeholder="Ketik nama Anda..." />
    <div id="result"></div>
  </div>

  <script src="data.js"></script>
  <script src="script.js"></script>
</body>
</html>

const dataTamu = [
  { nama: "Andi Wijaya", meja: "5", keterangan: "Keluarga Pria" },
  { nama: "Siti Nurhaliza", meja: "8", keterangan: "VIP" },
  { nama: "Budi Santoso", meja: "12", keterangan: "Rekan Kerja" },
  { nama: "Dewi Lestari", meja: "3", keterangan: "Teman SMA" },
  { nama: "Rudi Hartono", meja: "7", keterangan: "Keluarga Wanita" }
];


document.getElementById("searchInput").addEventListener("input", function () {
  const input = this.value.toLowerCase().trim();
  const resultDiv = document.getElementById("result");

  if (input.length < 2) {
    resultDiv.innerHTML = "";
    return;
  }

  const hasil = dataTamu.filter(t => t.nama.toLowerCase().includes(input));

  if (hasil.length > 0) {
    resultDiv.innerHTML = hasil.map(t =>
      `<div class="card">
        <h2>${t.nama}</h2>
        <p>Anda duduk di <strong>Meja ${t.meja}</strong></p>
        <p><em>${t.keterangan}</em></p>
      </div>`
    ).join("");
  } else {
    resultDiv.innerHTML = "<p>Nama tidak ditemukan. Coba periksa kembali ejaan nama Anda.</p>";
  }
});



body {
  font-family: sans-serif;
  background: #f9f9f9;
  padding: 2rem;
  text-align: center;
}
.container {
  max-width: 500px;
  margin: auto;
  background: white;
  padding: 2rem;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0,0,0,0.1);
}
input {
  width: 100%;
  padding: 1rem;
  font-size: 1rem;
  margin-top: 1rem;
}
.card {
  background: #f0f0f0;
  margin-top: 1rem;
  padding: 1rem;
  border-radius: 6px;
}


