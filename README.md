<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>My Studies</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f0f0f5;
      margin: 0;
      padding: 0;
    }

    header {
      background: #3f51b5;
      color: white;
      padding: 20px;
      text-align: center;
    }

    header input, header select {
      margin-top: 10px;
      padding: 8px;
      width: 200px;
      max-width: 90%;
      border-radius: 5px;
      border: none;
      font-size: 1em;
    }

    main {
      padding: 20px;
      max-width: 900px;
      margin: auto;
    }

    section h2 {
      margin-top: 30px;
    }

    .pdf-list {
      list-style-type: none;
      padding: 0;
    }

    .pdf-list li a {
      display: inline-block;
      margin-bottom: 10px;
      color: #3f51b5;
      text-decoration: none;
    }

    .pdf-list li a:hover {
      text-decoration: underline;
    }

    iframe {
      border: 1px solid #ccc;
      border-radius: 6px;
      margin-top: 10px;
    }

    .form-section {
      margin-top: 30px;
      background: #ffffff;
      padding: 15px;
      border-radius: 8px;
      box-shadow: 0 1px 5px rgba(0,0,0,0.1);
    }

    .form-section input {
      width: 100%;
      padding: 10px;
      margin: 8px 0;
      border: 1px solid #ccc;
      border-radius: 5px;
    }

    .form-section button {
      padding: 10px 20px;
      background-color: #3f51b5;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }

    .form-section button:hover {
      background-color: #2c3b95;
    }
  </style>
</head>
<body>
  <header>
    <h1>📘 My Studies</h1>
    <input type="text" id="searchBox" placeholder="Search PDFs..." />
    <select id="categoryFilter">
      <option value="all">All Subjects</option>
      <option value="science">Science</option>
      <option value="math">Maths</option>
      <option value="english">English</option>
      <option value="history">History</option>
      <option value="geography">Geography</option>
      <option value="politics">Politics</option>
      <option value="current">Current Affairs</option>
    </select>
  </header>

  <main>
    <section class="pdf-viewer-section">
      <h2>📄 PDF Viewer</h2>
      <ul class="pdf-list" id="pdfList">
        <li><a href="#" data-pdf="https://jatin381.github.io/My-Studies/500-GA-Previous-Years-Questions.pdf">500 GA Previous Years' Questions (SSC CHSL)</a></li>
      </ul>
      <iframe id="pdfViewer" src="" width="100%" height="500px" style="display: none;"></iframe>
    </section>

    <section class="form-section">
      <h2>➕ Add New PDF</h2>
      <input type="text" id="pdfTitle" placeholder="PDF Title" />
      <input type="text" id="pdfURL" placeholder="PDF URL (e.g. https://...)" />
      <button onclick="addPDF()">Add PDF</button>
    </section>
  </main>

  <script>
    function refreshPDFLinks() {
      document.querySelectorAll('.pdf-list a').forEach(link => {
        link.onclick = function (e) {
          e.preventDefault();
          const pdf = link.getAttribute('data-pdf');
          const viewer = document.getElementById('pdfViewer');
          viewer.src = pdf;
          viewer.style.display = 'block';
        };
      });
    }

    refreshPDFLinks();

    function addPDF() {
      const title = document.getElementById('pdfTitle').value.trim();
      const url = document.getElementById('pdfURL').value.trim();
      if (!title || !url) return alert("Please enter both PDF title and URL.");

      const list = document.getElementById('pdfList');
      const li = document.createElement('li');
      li.innerHTML = `<a href="#" data-pdf="${url}">${title}</a>`;
      list.appendChild(li);
      refreshPDFLinks();

      document.getElementById('pdfTitle').value = '';
      document.getElementById('pdfURL').value = '';
    }
  </script>
</body>
</html>
