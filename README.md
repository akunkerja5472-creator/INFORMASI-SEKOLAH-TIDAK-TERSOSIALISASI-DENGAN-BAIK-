# INFORMASI-SEKOLAH-TIDAK-TERSOSIALISASI-DENGAN-BAIK-
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>Contoh Berkas</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 20px;
    }
    textarea {
      width: 100%;
      height: 150px;
      margin-top: 10px;
    }
    button {
      margin-top: 10px;
      padding: 8px 15px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      background: #007BFF;
      color: white;
    }
  </style>
</head>
<body>
  <h1>Contoh Bekerja dengan Berkas</h1>

  <!-- Input untuk memilih file -->
  <input type="file" id="fileInput"><br>

  <!-- Tempat menampilkan isi file -->
  <textarea id="fileContent" placeholder="Isi berkas akan muncul di sini..."></textarea><br>

  <!-- Tombol untuk simpan isi textarea jadi file -->
  <button onclick="simpanFile()">Simpan ke File</button>

  <script>
    const fileInput = document.getElementById("fileInput");
    const fileContent = document.getElementById("fileContent");

    // Baca file yang dipilih
    fileInput.addEventListener("change", () => {
      const file = fileInput.files[0];
      const reader = new FileReader();

      reader.onload = (e) => {
        fileContent.value = e.target.result;
      };

      if (file) {
        reader.readAsText(file);
      }
    });

    // Simpan isi textarea ke file baru
    function simpanFile() {
      const isi = fileContent.value;
      const blob = new Blob([isi], { type: "text/plain" });
      const link = document.createElement("a");

      link.href = URL.createObjectURL(blob);
      link.download = "hasil.txt";
      link.click();
    }
  </script>
</body>
</html>
