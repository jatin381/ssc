<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Study Resource Hub</title>
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

    .qa-item {
      background: white;
      padding: 15px;
      margin: 10px 0;
      border-radius: 8px;
      box-shadow: 0 1px 4px rgba(0,0,0,0.1);
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
  </style>
</head>
<body>
  <header>
    <h1>📘 Study Resource Hub</h1>
    <input type="text" id="searchBox" placeholder="Search questions..." />
    <select id="categoryFilter">
      <option value="all">All Subjects</option>
      <option value="science">Science</option>
      <option value="math">Math</option>
    </select>
  </header>

  <main>
    <section class="pdf-viewer-section">
      <h2>📄 PDF Viewer</h2>
      <ul class="pdf-list">
        <li><a href="#" data-pdf="https://example.com/science-notes.pdf">Science Notes</a></li>
        <li><a href="#" data-pdf="https://example.com/math-questions.pdf">Math Questions</a></li>
      </ul>
      <iframe id="pdfViewer" src="" width="100%" height="500px" style="display: none;"></iframe>
    </section>

    <section id="qaSection">
      <h2>❓ Questions & Answers</h2>

      <div class="qa-item" data-category="science">
        <h3>What is Photosynthesis?</h3>
        <p><strong>Answer:</strong> Photosynthesis is the process by which green plants make their food using sunlight.</p>
      </div>

      <div class="qa-item" data-category="math">
        <h3>What is the Pythagorean Theorem?</h3>
        <p><strong>Answer:</strong> In a right-angled triangle, a² + b² = c².</p>
      </div>

      <div class="qa-item" data-category="science">
        <h3>What is Newton's First Law?</h3>
        <p><strong>Answer:</strong> An object in motion stays in motion unless acted on by a force.</p>
      </div>

      <div class="qa-item" data-category="math">
        <h3>What is an Equation?</h3>
        <p><strong>Answer:</strong> A statement showing two expressions are equal, like x + 2 = 5.</p>
      </div>
    </section>
  </main>

  <script>
    // PDF Viewer
    document.querySelectorAll('.pdf-list a').forEach(link => {
      link.addEventListener('click', e => {
        e.preventDefault();
        const pdf = link.getAttribute('data-pdf');
        const viewer = document.getElementById('pdfViewer');
        viewer.src = pdf;
        viewer.style.display = 'block';
      });
    });

    // Search & Filter
    const searchBox = document.getElementById('searchBox');
    const categoryFilter = document.getElementById('categoryFilter');
    const qaItems = document.querySelectorAll('.qa-item');

    function filterQuestions() {
      const search = searchBox.value.toLowerCase();
      const category = categoryFilter.value;

      qaItems.forEach(item => {
        const question = item.querySelector('h3').textContent.toLowerCase();
        const matchesSearch = question.includes(search);
        const matchesCategory = category === 'all' || item.dataset.category === category;

        item.style.display = matchesSearch && matchesCategory ? 'block' : 'none';
      });
    }

    searchBox.addEventListener('input', filterQuestions);
    categoryFilter.addEventListener('change', filterQuestions);
  </script>
</body>
</html>
