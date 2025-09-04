# Cnn-Clone
cnn-clone/
│── index.html        (Homepage with featured + categories)
│── category.html     (Category page)
│── article.html      (Single article page)
│── style.css         (Styling)
│── script.js         (Dummy data + navigation logic)
│── README.md         (Setup instructions for GitHub/Netlify)
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CNN Clone - Homepage</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header>
    <h1>CNN Clone</h1>
    <nav>
      <a href="index.html">Home</a>
      <a href="category.html?type=world">World</a>
      <a href="category.html?type=sports">Sports</a>
      <a href="category.html?type=technology">Technology</a>
      <a href="category.html?type=entertainment">Entertainment</a>
    </nav>
  </header>

  <main>
    <section id="featured">
      <h2>Featured News</h2>
      <div id="featured-news"></div>
    </section>

    <section id="categories">
      <h2>Latest Headlines</h2>
      <div id="news-list"></div>
    </section>
  </main>

  <footer>
    <p>© 2025 CNN Clone - Built for Demo</p>
  </footer>

  <script src="script.js"></script>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CNN Clone - Category</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header>
    <h1>CNN Clone</h1>
    <nav>
      <a href="index.html">Home</a>
    </nav>
  </header>

  <main>
    <h2 id="category-title"></h2>
    <div id="category-news"></div>
  </main>

  <footer>
    <p>© 2025 CNN Clone</p>
  </footer>

  <script src="script.js"></script>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CNN Clone - Article</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header>
    <h1>CNN Clone</h1>
    <nav>
      <a href="index.html">Home</a>
    </nav>
  </header>

  <main>
    <article id="article-content"></article>
  </main>

  <footer>
    <p>© 2025 CNN Clone</p>
  </footer>

  <script src="script.js"></script>
</body>
</html>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
}
header {
  background: #cc0000;
  color: #fff;
  padding: 10px;
}
header h1 {
  margin: 0;
}
nav a {
  color: white;
  margin: 0 10px;
  text-decoration: none;
}
main {
  padding: 20px;
}
#featured-news, #news-list, #category-news {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 15px;
}
.news-card {
  border: 1px solid #ddd;
  padding: 10px;
  border-radius: 8px;
  background: #f9f9f9;
  cursor: pointer;
}
.news-card:hover {
  background: #eee;
}
footer {
  background: #222;
  color: white;
  text-align: center;
  padding: 10px;
}
// Dummy News Data
const newsData = [
  { id: 1, title: "World Leaders Meet for Summit", category: "world", content: "Full article about world leaders." },
  { id: 2, title: "Sports Championship Results", category: "sports", content: "Full article about sports." },
  { id: 3, title: "New Tech Breakthrough Announced", category: "technology", content: "Full article about technology." },
  { id: 4, title: "Entertainment Awards Night", category: "entertainment", content: "Full article about entertainment." }
];

// Render Homepage
if (document.getElementById("featured-news")) {
  const featured = document.getElementById("featured-news");
  const list = document.getElementById("news-list");

  // First one featured
  featured.innerHTML = `
    <div class="news-card" onclick="openArticle(${newsData[0].id})">
      <h3>${newsData[0].title}</h3>
      <p>${newsData[0].content.substring(0, 50)}...</p>
    </div>
  `;

  // Rest in list
  list.innerHTML = newsData.slice(1).map(item => `
    <div class="news-card" onclick="openArticle(${item.id})">
      <h3>${item.title}</h3>
      <p>${item.content.substring(0, 50)}...</p>
    </div>
  `).join("");
}

// Render Category Page
if (document.getElementById("category-news")) {
  const params = new URLSearchParams(window.location.search);
  const category = params.get("type");
  const title = document.getElementById("category-title");
  title.innerText = category.toUpperCase() + " News";

  const categoryNews = document.getElementById("category-news");
  categoryNews.innerHTML = newsData.filter(n => n.category === category)
    .map(item => `
      <div class="news-card" onclick="openArticle(${item.id})">
        <h3>${item.title}</h3>
        <p>${item.content.substring(0, 50)}...</p>
      </div>
    `).join("");
}

// Render Article Page
if (document.getElementById("article-content")) {
  const params = new URLSearchParams(window.location.search);
  const id = parseInt(params.get("id"));
  const article = newsData.find(n => n.id === id);

  if (article) {
    document.getElementById("article-content").innerHTML = `
      <h2>${article.title}</h2>
      <p>${article.content}</p>
    `;
  }
}

// Navigation Function
function openArticle(id) {
  window.location.href = `article.html?id=${id}`;
}
# CNN Clone

A functional news website inspired by CNN.

## Features
- Homepage with featured news and headlines
- Categories: World, Sports, Technology, Entertainment
- Article page with full news content
- Responsive design

## Setup
1. Clone this repo:
   ```bash
   git clone https://github.com/your-username/cnn-clone.git

---

👉 Ab tum is project ko GitHub pe upload karo aur Netlify se deploy kar do.  
Ek proper **functional repository + hosted CNN clone site** ready ho jaegi.  

Chaho to main tumhe **GitHub pe push karne aur Netlify pe deploy karne ke exact steps** bhi bata dun?
