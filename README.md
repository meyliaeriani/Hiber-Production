<!DOCTYPE html>
<html lang="id">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Halaman Belajar</title>
    <style>
      body {
        font-family: sans-serif;
        margin: 0;
        background-color: #F1E9E6;
      }

      /* Header */
      .header {
        background-color: #F1E9E6;
        padding: 20px;
        box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
      }

      .logo {
        max-height: 50px;
        margin-right: 10px;
      }

      .blog-title {
        font-size: 1.5em;
        font-weight: bold;
        display: inline-block;
        line-height: 50px;
      }

      /* Navigasi */
      .nav-tabs {
        list-style: none;
        padding: 0;
        margin: 0;
        display: flex;
        overflow-x: auto;
      }

      .nav-tabs li {
        margin-right: 10px;
      }

      .nav-tabs a {
        display: block;
        padding: 10px 15px;
        text-decoration: none;
        color: #C49488;
        background-color: #F4DAB5;
        border-radius: 5px 5px 0 0;
        border: 1px solid #F2B892;
        transition: background-color 0.3s, color 0.3s;
      }

      .nav-tabs a:hover {
        background-color: #F2B892;
        color: #DD8A62;
      }

      .nav-tabs a.active {
        background-color: #E1CDC6;
        border-bottom: 2px solid #E1CDC6;
        color: #DD8A62;
      }

      /* Layout Flexbox untuk Sidebar dan Konten */
      .main-content {
        display: flex;
        margin: 20px;
      }

      #sidebar {
        width: 250px;
        background-color: #F4DAB5;
        padding: 20px;
        margin-right: 20px;
        border-radius: 8px;
        border-right: 1px solid #F2B892;
      }

      #content {
        flex-grow: 1;
        padding: 20px;
        background-color: #FFFFFF;
        border-radius: 8px;
      }

      /* Postingan */
      .post {
        border: 1px solid #F2B892;
        padding: 15px;
        margin-bottom: 15px;
        background-color: #FFFFFF;
        border-radius: 8px;
        box-shadow: 2px 2px 5px rgba(0, 0, 0, 0.1);
      }

      .post h3 {
        color: #DD8A62;
      }

      .post-content {
        margin-top: 10px;
      }

      .post-content p {
        text-align: justify;
      }

      /* Editor */
      #editor-container {
        display: none;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.5);
        z-index: 1000;
        display: flex;
        justify-content: center;
        align-items: center;
      }

      #editor {
        background-color: #FFFFFF;
        padding: 20px;
        border-radius: 8px;
        width: 80%;
        max-height: 90vh;
        overflow-y: auto;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      }

      #editor textarea {
        width: 100%;
        min-height: 300px;
        margin-bottom: 10px;
        box-sizing: border-box;
        padding: 10px;
        border: 1px solid #DD8A62;
        border-radius: 5px;
      }

      #editor input[type="text"] {
        width: 100%;
        margin-bottom: 10px;
        box-sizing: border-box;
        padding: 10px;
        border: 1px solid #DD8A62;
        border-radius: 5px;
      }

      #editor button {
        padding: 10px 20px;
        border: none;
        border-radius: 5px;
        background-color: #DD8A62;
        color: white;
        cursor: pointer;
      }

      /* Toolbar untuk Editor */
      .toolbar {
        display: flex;
        gap: 10px;
        margin-bottom: 10px;
        flex-wrap: wrap;
      }

      .toolbar button {
        padding: 5px 10px;
        background-color: #F4DAB5;
        border: 1px solid #DD8A62;
        border-radius: 5px;
        cursor: pointer;
        font-size: 16px;
      }

      .toolbar button:hover {
        background-color: #DD8A62;
        color: white;
      }

      .toolbar select {
        padding: 5px;
        font-size: 16px;
      }

      .toolbar input[type="file"] {
        display: none;
      }
    </style>
  </head>

  <body>
    <!-- Header -->
    <header class="header">
      <img src="logo.jpg" alt="Logo Halaman Belajar" class="logo">
      <span class="blog-title">Halaman Belajar</span>
      <nav>
        <ul class="nav-tabs">
          <li><a href="index.htm" class="active">Beranda</a></li>
          <li><a href="kelas-x.htm">Kelas X</a></li>
          <li><a href="kelas-xi.htm">Kelas XI</a></li>
          <li><a href="kelas-xii.htm">Kelas XII</a></li>
          <li><a href="soal.htm">Soal</a></li>
          <li><a href="cerita.htm">Cerita</a></li>
          <li><a href="tentang-kami.htm">Tentang Kami</a></li>
          <li><a href="kontak.htm">Kontak</a></li>
        </ul>
      </nav>
    </header>

    <!-- Konten Utama dengan Layout Flexbox -->
    <div class="main-content">
      <!-- Sidebar -->
      <div id="sidebar">
        <h2>Daftar Postingan</h2>
        <ul id="post-list"></ul>
        <button id="tambah-btn">Tambah Postingan</button>
      </div>

      <!-- Konten Blog -->
      <div id="content">
        <h1>Blog</h1>
        <div id="post-container"></div>
      </div>
    </div>

    <!-- Editor Postingan -->
    <div id="editor-container">
      <div id="editor">
        <!-- Toolbar untuk formatting teks -->
        <div class="toolbar">
          <!-- Text Format Toolbar -->
          <button onclick="document.execCommand('bold')">B</button>
          <button onclick="document.execCommand('italic')">I</button>
          <button onclick="document.execCommand('underline')">U</button>

          <!-- Alignment Buttons -->
          <button onclick="document.execCommand('justifyLeft')">Align Left</button>
          <button onclick="document.execCommand('justifyCenter')">Center</button>
          <button onclick="document.execCommand('justifyRight')">Align Right</button>

          <!-- Hyperlink Button -->
          <button onclick="addHyperlink()">Link</button>

          <!-- Table Button -->
          <button onclick="insertTable()">Table</button>

          <!-- Font Size & Family -->
          <select onchange="document.execCommand('fontSize', false, this.value)">
            <option value="3">Medium</option>
            <option value="5">Large</option>
            <option value="7">Huge</option>
          </select>
        </div>
        <h2>Tambah/Edit Postingan</h2>
        <input type="text" id="judul-input" placeholder="Judul Postingan">
        <br>
        <div contenteditable="true" id="isi-input" placeholder="Isi Postingan" style="min-height: 200px; border: 1px solid #DD8A62; padding: 10px; border-radius: 5px;"></div>
        <br>
        <button id="simpan-btn">Simpan</button>
        <button id="batal-btn">Batal</button>
      </div>
    </div>

    <script>
      let postingan = [];
      let editingIndex = -1;
      const postList = document.getElementById('post-list');
      const postContainer = document.getElementById('post-container');
      const tambahBtn = document.getElementById('tambah-btn');
      const editorContainer = document.getElementById('editor-container');
      const judulInput = document.getElementById('judul-input');
      const isiInput = document.getElementById('isi-input');
      const simpanBtn = document.getElementById('simpan-btn');
      const batalBtn = document.getElementById('batal-btn');

      function tampilkanPostingan() {
        postContainer.innerHTML = '';
        postList.innerHTML = '';
        postingan.forEach((post, index) => {
          const postDiv = document.createElement('div');
          postDiv.className = 'post';
          postDiv.innerHTML = `
            <h3>${post.judul}</h3>
            <div class="post-content">
              <p>${post.isi}</p>
              <button onclick="editPostingan(${index})">Edit</button>
              <button onclick="hapusPostingan(${index})">Hapus</button>
            </div>`;
          const listItem = document.createElement('li');
          const link = document.createElement('a');
          link.href = "#";
          link.textContent = post.judul;
          listItem.appendChild(link);
          postList.appendChild(listItem);
          postContainer.appendChild(postDiv);
        });
      }

      function tampilkanEditor(judul = '', isi = '') {
        judulInput.value = judul;
        isiInput.innerHTML = isi;
        editorContainer.style.display = 'flex';
      }

      function sembunyikanEditor() {
        editorContainer.style.display = 'none';
        editingIndex = -1;
      }

      tambahBtn.addEventListener('click', () => {
        tampilkanEditor();
      });

      function editPostingan(index) {
        editingIndex = index;
        tampilkanEditor(postingan[index].judul, postingan[index].isi);
      }

      function hapusPostingan(index) {
        if (confirm("Apakah Anda yakin ingin menghapus postingan ini?")) {
          postingan.splice(index, 1);
          tampilkanPostingan();
        }
      }

      simpanBtn.addEventListener('click', () => {
        const judul = judulInput.value;
        const isi = isiInput.innerHTML;
        if (judul && isi) {
          if (editingIndex === -1) {
            postingan.push({ judul, isi });
          } else {
            postingan[editingIndex] = { judul, isi };
          }
          tampilkanPostingan();
          sembunyikanEditor();
        }
      });

      batalBtn.addEventListener('click', sembunyikanEditor);

      // Fungsi untuk menambah hyperlink
      function addHyperlink() {
        const url = prompt("Masukkan URL:");
        if (url) {
          document.execCommand('createLink', false, url);
        }
      }

      // Fungsi untuk menyisipkan tabel
      function insertTable() {
        const rows = prompt("Jumlah baris:");
        const cols = prompt("Jumlah kolom:");
        if (rows && cols) {
          const table = document.createElement("table");
          for (let i = 0; i < rows; i++) {
            const tr = document.createElement("tr");
            for (let j = 0; j < cols; j++) {
              const td = document.createElement("td");
              td.textContent = `Baris ${i+1} Kolom ${j+1}`;
              tr.appendChild(td);
            }
            table.appendChild(tr);
          }
          document.execCommand('insertHTML', false, table.outerHTML);
        }
      }

      tampilkanPostingan(); 
    </script>
  </body>
</html>
