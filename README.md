<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>NewsApp</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins&display=swap" rel="stylesheet">
  <style>
    :root {
      --bg: linear-gradient(120deg, #f6d365 0%, #fda085 100%);
      --text: #333;
      --card-bg: #ffffffee;
      --nav-bg: #4b2c5e;
      --footer-bg: #3d1c49;
    }
    body.dark-mode {
      --bg: #121212;
      --text: #fff;
      --card-bg: #1e1e1e;
      --nav-bg: #1e1e1e;
      --footer-bg: #1e1e1e;
    }

    body {
      font-family: 'Poppins', sans-serif;
      margin: 0;
      padding: 0;
      background: var(--bg);
      color: var(--text);
      transition: all 0.3s ease;
      scroll-behavior: smooth;
    }

    nav {
      background: var(--nav-bg);
      color: white;
      padding: 15px;
      text-align: center;
      position: sticky;
      top: 0;
      z-index: 999;
    }

    nav a {
      color: white;
      margin: 10px;
      text-decoration: none;
      font-weight: bold;
    }

    nav a:hover {
      text-decoration: underline;
    }

    .theme-toggle {
      background: none;
      border: none;
      color: #fff;
      font-size: 18px;
      cursor: pointer;
      position: absolute;
      top: 18px;
      right: 20px;
    }

    .search-bar {
      text-align: center;
      padding: 20px;
    }

    .search-bar input {
      width: 80%;
      max-width: 400px;
      padding: 10px;
      border-radius: 8px;
      border: 1px solid #ccc;
    }

    .grid {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 20px;
      padding: 20px;
    }

    .card {
      background: var(--card-bg);
      border-radius: 10px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      overflow: hidden;
      width: 300px;
      padding: 15px;
      transition: transform 0.3s, opacity 0.3s;
      animation: fadeInUp 1s ease forwards;
      opacity: 0;
      transform: translateY(20px);
    }

    .card:hover {
      transform: scale(1.05);
    }

    .card img {
      width: 100%;
      height: 180px;
      object-fit: cover;
      border-radius: 10px;
      margin-bottom: 10px;
    }

    .card h3 {
      margin: 0 0 10px;
      color: var(--text);
    }

    footer {
      background: var(--footer-bg);
      color: white;
      text-align: center;
      padding: 15px;
      margin-top: 30px;
    }

    @keyframes fadeInUp {
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    @media (max-width: 768px) {
      .grid {
        flex-direction: column;
        align-items: center;
      }

      .search-bar input {
        width: 90%;
      }
    }

    .feedback-section {
      background: var(--card-bg);
      padding: 30px;
      margin-top: 40px;
      border-radius: 10px;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
      width: 80%;
      max-width: 600px;
      margin-left: auto;
      margin-right: auto;
      text-align: center;
    }

    .feedback-section h2 {
      color: var(--text);
    }

    .feedback-section form input, 
    .feedback-section form textarea {
      width: 100%;
      padding: 12px;
      margin: 10px 0;
      border-radius: 5px;
      border: 1px solid #ccc;
      box-sizing: border-box;
    }

    .feedback-section form button {
      background-color: #4b2c5e;
      color: white;
      padding: 12px 20px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }

    .feedback-section form button:hover {
      background-color: #3a1a3d;
    }

    #loader {
      position: fixed;
      width: 100%;
      height: 100%;
      background: #fff;
      z-index: 9999;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .loader-icon {
      border: 6px solid #f3f3f3;
      border-top: 6px solid #4b2c5e;
      border-radius: 50%;
      width: 40px;
      height: 40px;
      animation: spin 1s linear infinite;
    }

    @keyframes spin {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    #backToTopBtn {
      display: none;
      position: fixed;
      bottom: 30px;
      right: 30px;
      z-index: 99;
      font-size: 18px;
      background-color: #4b2c5e;
      color: white;
      border: none;
      border-radius: 50%;
      padding: 10px 15px;
      cursor: pointer;
      box-shadow: 0 4px 10px rgba(0,0,0,0.3);
    }

    #backToTopBtn:hover {
      background-color: #3a1a3d;
    }
  </style>
</head>
<body>
  <div id="loader"><div class="loader-icon"></div></div>

  <nav>
    <a href="#home">Home</a>
    <a href="#sports">Sports</a>
    <a href="#politics">Politics</a>
    <a href="#education">Education</a>
    <a href="#technology">Tech</a>
    <a href="#entertainment">Entertainment</a>
    <a href="#health">Health</a>
    <a href="#business">Business</a>
    <a href="#travel">Travel</a>
    <a href="#weather">Weather</a>
    <button class="theme-toggle" onclick="toggleTheme()">🌗</button>
  </nav>

  <div class="search-bar">
    <input type="text" id="searchInput" onkeyup="searchNews()" placeholder="Search news...">
  </div>

  <section id="home" style="text-align:center;">
    <h2>Welcome to Newscity</h2>
    <p>Your colorful and animated daily source of the latest news!</p>
  </section>

  <div class="grid">
    <div class="card" id="sports">
      <img src="https://images.unsplash.com/photo-1521412644187-c49fa049e84d" alt="Sports">
      <h3>Sports!</h3>
      <p>Sports encompass a wide range of physical activities, often competitive and organized, that involve skill, competition, and rules. They can be played individually or in teams, and offer opportunities for physical fitness, skill development, and enjoyment. Sports can also be a source of entertainment for spectators.</p>
    </div>

    <div class="card" id="politics">
      <img src="https://images.unsplash.com/photo-1583847268964-b28dc8f51f92" alt="Politics">
      <h3>Politics</h3>
      <p>Politics is about making agreements between people so that they can live together in groups such as tribes, cities, or countries. In large groups, such as countries, some people may spend a lot of their time making such agreements. These people are called politicians.</p>
    </div>

    <div class="card" id="education">
      <img src="https://images.unsplash.com/photo-1588072432836-e10032774350" alt="Education">
      <h3>Education</h3>
      <p>Education encompasses formal, non-formal, and informal learning, all focused on acquiring knowledge, skills, and values. It's a systematic process that helps individuals develop and become more knowledgeable and capable. Education plays a crucial role in shaping individuals and society, impacting everything from personal development to economic growth and social progress.</p>
    </div>

    <div class="card" id="technology">
      <img src="https://images.unsplash.com/photo-1518770660439-4636190af475" alt="Technology">
      <h3>Tech</h3>
      <p>Today's AI news includes OpenAI doubling rate limits for GPT-4 models, OpenAI's image generator becoming accessible to businesses worldwide via API, and Ray-Ban Meta smart glasses rolling out in India soon, says The Economic Times. Additionally, AI chatbot traffic is surging, China is automating factories with robots, and AI is transforming core business for Indian enterprises.</p>
    </div>

    <div class="card" id="entertainment">
      <img src="https://images.unsplash.com/photo-1530182342684-c75f9ed421dd" alt="Entertainment">
      <h3>Entertainment</h3>
      <p>ANORA took home five Oscars including wins for Best Picture, Directing (Sean Baker) and Actress in a Leading Role (Mikey Madison). New talents rise as .</p>
    </div>

    <div class="card" id="health">
      <img src="https://images.unsplash.com/photo-1604690631191-6111c870ad97" alt="Health">
      <h3>Health</h3>
      <p>World Immunisation Week 2025: As measles continues to create a rampage in the US, WHO underscores the importance of vaccines. Mental health awareness leads to major wellness campaigns.</p>
    </div>

    <div class="card" id="business">
      <img src="https://images.unsplash.com/photo-1518779578993-ec3579fee39f" alt="Business">
      <h3>Business</h3>
      <p>Experts expect the Nifty 50 to consolidate with key support in the 24,000–23,900 zone; however, on the higher side, 24,550 is expected to act as the resistance zone. The Bank Nifty needs to sustain above 54,700 in the short term for a rebound toward 56,100, but if it falls below this level, selling pressure may emerge. Tech sector drives global stock market growth this quarter.</p>
    </div>

    <div class="card" id="travel">
      <img src="https://images.unsplash.com/photo-1507525428034-b723cf961d3e" alt="Travel">
      <h3>Travel</h3>
      <p>Baga Beach, nestled along the sun-kissed coastline of North Goa, is a vibrant and captivating destination that beckons travellers from around the world. Explore hidden gems and trending destinations for your next trip.</p>
    </div>

    <div class="card" id="weather">
      <img src="https://images.unsplash.com/photo-1501630834273-4b5604d2ee31" alt="Weather">
      <h3>Weather</h3>
      <p>The ongoing heatwave is expected to intensify across several parts of India, with multiple regions on high alert. Residents are urged to take necessary precautions as scorching temperatures and hot, humid conditions persist throughout the week.</p>
    </div>
  </div>

  <div class="feedback-section" id="feedback">
    <h2>Customer Feedback</h2>
    <p>We value your thoughts! Please provide your feedback below.</p>
    <form action="#" method="POST">
      <input type="text" name="name" placeholder="Your Name" required />
      <input type="email" name="email" placeholder="Your Email" required />
      <textarea name="message" placeholder="Your Message" rows="5" required></textarea>
      <button type="submit">Submit Feedback</button>
    </form>
  </div>

  <footer>
    <p>&copy; 2025 NewsApp. All rights reserved.</p>
  </footer>

  <button onclick="scrollToTop()" id="backToTopBtn" title="Go to top">↑</button>

  <script>
    function toggleTheme() {
      document.body.classList.toggle('dark-mode');
      localStorage.setItem("theme", document.body.classList.contains('dark-mode') ? "dark" : "light");
    }

    function loadTheme() {
      const theme = localStorage.getItem("theme");
      if (theme === "dark") {
        document.body.classList.add("dark-mode");
      }
    }

    function searchNews() {
      const input = document.getElementById("searchInput").value.toLowerCase();
      const cards = document.querySelectorAll(".card");
      cards.forEach(card => {
        const content = card.innerText.toLowerCase();
        card.style.display = content.includes(input) ? "block" : "none";
      });
    }

    function scrollToTop() {
      window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    window.onscroll = function () {
      document.getElementById("backToTopBtn").style.display = window.pageYOffset > 100 ? "block" : "none";
    };

    window.onload = function () {
      loadTheme();
      setTimeout(() => document.getElementById("loader").style.display = "none", 1000);
    }
  </script>
</body>
</html>
