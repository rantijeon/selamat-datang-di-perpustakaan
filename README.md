
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Aplikasi Peminjaman Buku</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-image: url('https://images.unsplash.com/photo-1524995997946-a1c2e315a42f');
      background-size: cover;
      background-position: center;
      color: #fff;
      margin: 0;
      padding: 0;
    }

    .container {
      max-width: 600px;
      margin: auto;
      padding: 10px;
      padding-bottom: 80px;
    }

    .card {
      background: rgba(0, 0, 0, 0.7);
      padding: 20px;
      border-radius: 10px;
    }

    h2, h3 {
      text-align: center;
      color: pink;
    }

    .form-group {
      margin-bottom: 15px;
    }

    .form-group label {
      display: block;
      margin-bottom: 5px;
      color: pink;
      font-weight: bold;
    }

    input, textarea {
      width: 100%;
      padding: 8px;
      border-radius: 5px;
      border: none;
      color: #000;
      box-sizing: border-box;
    }

    .btn {
      background-color: black;
      border: 2px solid pink;
      padding: 10px 15px;
      border-radius: 5px;
      cursor: pointer;
      color: pink;
      font-weight: bold;
      margin: 5px;
    }

    .btn:hover {
      background-color: #222;
    }

    .books {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      justify-content: center;
    }

    .book {
      cursor: pointer;
      border: 2px solid transparent;
      transition: border 0.3s;
    }

    .book img {
      width: 100px;
      height: 150px;
      border-radius: 5px;
    }

    .book.selected {
      border: 2px solid pink;
    }

    .riwayat-item {
      background: rgba(255, 192, 203, 0.2);
      padding: 10px;
      margin-bottom: 10px;
      border-radius: 5px;
      color: white;
    }

    .hidden {
      display: none;
    }

    .footer-nav {
      position: fixed;
      bottom: 0;
      left: 0;
      right: 0;
      background: rgba(0, 0, 0, 0.9);
      padding: 10px;
      text-align: center;
    }

    @media (max-width: 600px) {
      .btn {
        width: 100%;
      }

      .footer-nav {
        display: flex;
        flex-direction: column;
        gap: 5px;
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <!-- Halaman Form -->
    <div id="formPage" class="card">
      <h2>Form Peminjaman Buku</h2>
      <form id="borrowForm">
        <div class="form-group">
          <label for="nama">Nama</label>
          <input type="text" id="nama" />
        </div>
        <div class="form-group">
          <label for="nim">NIM</label>
          <input type="text" id="nim" />
        </div>
        <div class="form-group">
          <label for="prodi">Prodi</label>
          <input type="text" id="prodi" />
        </div>
        <div class="form-group">
          <label for="tglPinjam">Tanggal Peminjaman</label>
          <input type="date" id="tglPinjam" />
        </div>
        <div class="form-group">
          <label for="tglKembali">Tanggal Kembalian</label>
          <input type="date" id="tglKembali" />
        </div>
        <div class="form-group">
          <label for="keperluan">Keperluan</label>
          <textarea id="keperluan"></textarea>
        </div>
        <div style="text-align:center;">
          <button type="button" class="btn" onclick="lanjutKePilihBuku()">Simpan</button>
        </div>
      </form>
    </div>

    <!-- Halaman Pilih Buku -->
    <div id="bukuPage" class="card hidden">
      <h2>Pilih Buku</h2>
      <h3>Teknik</h3>
      <div class="books">
        <div class="book" data-title="Buku Mesin"><img src="https://iili.io/36hKTgt.jpg" /></div>
        <div class="book" data-title="Buku Codingan C++"><img src="https://iili.io/36XbeTP.jpg" /></div>
        <div class="book" data-title="Buku Python"><img src="https://iili.io/36h3R4t.jpg" /></div>
        <div class="book" data-title="Buku Metode Penelitian"><img src="https://iili.io/36hdd9j.jpg" /></div>
      </div>

      <h3>Ilmu Keperawatan</h3>
      <div class="books">
        <div class="book" data-title="Buku Gizi"><img src="https://iili.io/36hYOHG.jpg"></div>
        <div class="book" data-title="Buku Kesehatan"><img src="https://iili.io/36h0dJe.jpg"></div>
        <div class="book" data-title="Buku Psikologi"><img src="https://iili.io/36hVmsj.jpg"></div>
        <div class="book" data-title="Buku Keperawatan Kritis"><img src="https://iili.io/36hhAVs.jpg"></div>
        <div class="book" data-title="Buku Kegawatdaruratan"><img src="https://iili.io/36hNHR2.jpg"></div>
        <div class="book" data-title="Buku Komunitas"><img src="https://iili.io/36hOfII.jpg"></div>
        <div class="book" data-title="Buku Promkes"><img src="https://iili.io/36heqyQ.jpg"></div>
        <div class="book" data-title="Buku Klinis"><img src="https://iili.io/36hkBls.jpg"></div>
        <div class="book" data-title="Buku Jiwa"><img src="https://iili.io/36hvApR.jpg"></div>
        <div class="book" data-title="Buku Pediatri"><img src="https://iili.io/36h8rSs.jpg"></div>
      </div>

      <h3>Tarbiyah dan Keguruan</h3>
      <div class="books">
        <div class="book" data-title="Buku Agama"><img src="https://iili.io/36h69tf.jpg"></div>
        <div class="book" data-title="Buku Agama Islam"><img src="https://iili.io/36hPzen.jpg"></div>
        <div class="book" data-title="Buku Ulumul Qur'an dan Hadits"><img src="https://iili.io/36hs1ob.jpg"></div>
      </div>

      <h3>Ekonomi dan Bisnis</h3>
      <div class="books">
        <div class="book" data-title="Buku Sejarah Ekonomi"><img src="https://iili.io/36hDS8Q.jpg"></div>
        <div class="book" data-title="Buku Kepemimpinan"><img src="https://iili.io/36hmdmB.jpg"></div>
        <div class="book" data-title="Buku Akuntansi"><img src="https://iili.io/36hyTiX.jpg"></div>
        <div class="book" data-title="Buku Manajemen"><img src="https://iili.io/36jH5u4.jpg"></div>
        <div class="book" data-title="Buku Bisnis"><img src="https://iili.io/36jJP5b.jpg"></div>
      </div>
    </div>


    <!-- Halaman Riwayat -->
    <div id="riwayatPage" class="card hidden">
      <h2>Riwayat Peminjaman</h2>
      <div id="riwayatList"></div>
    </div>
  </div>

  <!-- Navigasi bawah -->
  <div class="footer-nav">
    <button class="btn" onclick="tampilkanHalaman('formPage')">Form</button>
    <button class="btn" onclick="tampilkanHalaman('bukuPage')">Pilih Buku</button>
    <button class="btn" onclick="tampilkanHalaman('riwayatPage')">Riwayat</button>
  </div>

  <script>
    const books = document.querySelectorAll('.book');
    const form = document.getElementById('borrowForm');
    let formDataSementara = {};

    function tampilkanHalaman(halamanId) {
      document.getElementById('formPage').classList.add('hidden');
      document.getElementById('bukuPage').classList.add('hidden');
      document.getElementById('riwayatPage').classList.add('hidden');
      document.getElementById(halamanId).classList.remove('hidden');
    }

    function ambilDataForm() {
      return {
        nama: document.getElementById('nama').value,
        nim: document.getElementById('nim').value,
        prodi: document.getElementById('prodi').value,
        tglPinjam: document.getElementById('tglPinjam').value,
        tglKembali: document.getElementById('tglKembali').value,
        keperluan: document.getElementById('keperluan').value
      };
    }

    function lanjutKePilihBuku() {
      const data = ambilDataForm();
      if (!data.nama || !data.nim || !data.prodi || !data.tglPinjam || !data.tglKembali) {
        alert("Harap lengkapi semua data terlebih dahulu.");
        return;
      }
      formDataSementara = data;
      tampilkanHalaman('bukuPage');
    }

    books.forEach(book => {
      book.addEventListener('click', () => {
        books.forEach(b => b.classList.remove('selected'));
        book.classList.add('selected');
        const judul = book.getAttribute('data-title');

        const dataLengkap = {
          ...formDataSementara,
          judulBuku: judul
        };

        let riwayat = JSON.parse(localStorage.getItem('riwayatPeminjaman')) || [];
        riwayat.push(dataLengkap);
        localStorage.setItem('riwayatPeminjaman', JSON.stringify(riwayat));

        tampilkanRiwayat();
        tampilkanHalaman('riwayatPage');
        form.reset();
        formDataSementara = {};
      });
    });

    function tampilkanRiwayat() {
      const list = document.getElementById('riwayatList');
      const riwayat = JSON.parse(localStorage.getItem('riwayatPeminjaman')) || [];
      list.innerHTML = "";
      riwayat.forEach((item, index) => {
        list.innerHTML += `
          <div class="riwayat-item">
            <strong>No:</strong> ${index + 1}<br>
            <strong>Nama:</strong> ${item.nama}<br>
            <strong>NIM:</strong> ${item.nim}<br>
            <strong>Judul Buku:</strong> ${item.judulBuku}<br>
            <strong>Tanggal Pinjam:</strong> ${item.tglPinjam} → <strong>Kembali:</strong> ${item.tglKembali}<br>
            <strong>Keperluan:</strong> ${item.keperluan}
          </div>
        `;
      });
    }

    window.onload = function () {
      tampilkanRiwayat();
      tampilkanHalaman('formPage');
    };
  </script>
</body>
</html>
