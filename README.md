<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>My Complete Portfolio, Quiz & Blog</title>

  <!-- Shared Styles -->
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      background: #f9f9f9;
      color: #333;
    }
    header, footer {
      background: #333;
      color: #fff;
      text-align: center;
      padding: 1rem;
    }
    section {
      padding: 20px;
      margin: 20px auto;
      max-width: 900px;
      background: #fff;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    h2 {
      margin-top: 0;
    }
    /* Portfolio Styles */
    .navbar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      background: #444;
      padding: 10px 20px;
      color: #fff;
    }
    .nav-links {
      list-style: none;
      display: flex;
      gap: 15px;
    }
    .nav-links li {
      display: inline;
    }
    .nav-links a {
      color: #fff;
      text-decoration: none;
    }
    .hero {
      text-align: center;
      padding: 40px 20px;
      background: #f1f1f1;
    }
    .hero-content span {
      color: #007BFF;
    }
    .btn {
      background: #007BFF;
      color: #fff;
      padding: 10px 15px;
      text-decoration: none;
      border-radius: 5px;
    }
    .about-content {
      display: flex;
      gap: 20px;
      align-items: center;
    }
    .about-content img {
      width: 150px;
      border-radius: 50%;
    }
    .project-grid {
      display: flex;
      gap: 20px;
      flex-wrap: wrap;
    }
    .project-card {
      flex: 1 1 250px;
      background: #f7f7f7;
      padding: 15px;
      border-radius: 8px;
    }
    .contact form {
      display: flex;
      flex-direction: column;
      gap: 10px;
    }
    .contact input, .contact textarea, .contact button {
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 5px;
      font-family: inherit;
    }
    /* Quiz Styles */
    .quiz-box {
      text-align: center;
    }
    .quiz-box button {
      width: 100%;
      margin: 8px 0;
      padding: 10px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      background: #eee;
    }
    .quiz-box button.correct {
      background: #4caf50;
      color: #fff;
    }
    .quiz-box button.wrong {
      background: #e53935;
      color: #fff;
    }
    /* Blog Styles */
    .post {
      background: white;
      padding: 15px;
      margin-bottom: 20px;
      border-radius: 8px;
      box-shadow: 0 0 5px rgba(0,0,0,0.1);
    }
    .post h2 {
      margin-bottom: 10px;
    }
    .post small {
      color: gray;
      font-size: 12px;
    }
  </style>

  <!-- EmailJS SDK -->
  <script src="https://cdn.emailjs.com/dist/email.min.js"></script>
  <script>
    (function(){
      emailjs.init("YOUR_PUBLIC_KEY"); // Replace with your actual key
    })();
  </script>
</head>
<body>

  <!-- Portfolio Section -->
  <header>
    <nav class="navbar">
      <div class="logo">MyPortfolio</div>
      <ul class="nav-links" id="nav-links">
        <li><a href="#home">Home</a></li>
        <li><a href="#about">About</a></li>
        <li><a href="#projects">Projects</a></li>
        <li><a href="#contact">Contact</a></li>
        <li><a href="#quiz">Quiz</a></li>
        <li><a href="#blog">Blog</a></li>
      </ul>
    </nav>
  </header>

  <section id="home" class="hero">
    <div class="hero-content">
      <h1>Hello, I'm <span>MR KAMAL</span></h1>
      <p>I am a student enthusiastic about technology and design.</p>
      <a href="#projects" class="btn">View My Work</a>
    </div>
  </section>

  <section id="about" class="about">
    <h2>About Me</h2>
    <div class="about-content">
      <img src="IMG-20250629-WA0004.jpg" alt="Profile Photo">
      <p>I love building interactive, user-friendly web applications and exploring new tools in the tech world.</p>
    </div>
  </section>

  <section id="projects" class="projects">
    <h2>My Projects</h2>
    <div class="project-grid">
      <div class="project-card"><h3>Project 1</h3><p>A simple responsive website.</p></div>
      <div class="project-card"><h3>Project 2</h3><p>JavaScript-based quiz app.</p></div>
      <div class="project-card"><h3>Project 3</h3><p>Personal blog with CMS.</p></div>
    </div>
  </section>

  <section id="contact" class="contact">
    <h2>Contact Me</h2>
    <form id="contact-form">
      <input type="text" id="name" name="user_name" placeholder="Your Name" required>
      <input type="email" id="email" name="user_email" placeholder="Your Email" required>
      <textarea id="message" name="message" placeholder="Your Message" required></textarea>
      <button type="submit">Send</button>
    </form>
    <p id="form-status"></p>
  </section>

  <!-- Quiz Section -->
  <section id="quiz" class="quiz">
    <h2>Random Quiz</h2>
    <div class="quiz-box">
      <h2 id="question">Question will appear here</h2>
      <div id="options"></div>
      <p id="result"></p>
      <button onclick="loadRandomQuestion()">Next Question</button>
    </div>
  </section>

  <!-- Blog Section -->
  <section id="blog" class="blog">
    <h2>My Blog</h2>
    <div class="container" id="postsContainer"></div>
  </section>

  <footer>
    <p>&copy; 2025 MR KAMAL | All rights reserved</p>
  </footer>

  <script>
    // EmailJS Contact Form Handling
    document.getElementById("contact-form").addEventListener("submit", function(e){
      e.preventDefault();
      const form = this;
      emailjs.sendForm('YOUR_SERVICE_ID', 'YOUR_TEMPLATE_ID', form)
        .then(() => {
          document.getElementById("form-status").textContent = "Message sent successfully!";
          form.reset();
        }, (error) => {
          document.getElementById("form-status").textContent = "Error sending message.";
          console.error("EmailJS error:", error);
        });
    });

    // Quiz Logic
    const questions = [
      {q:"What is the capital of India?", options:["Mumbai","Delhi","Chennai","Kolkata"], answer:"Delhi"},
      {q:"Which is the largest planet?", options:["Earth","Mars","Jupiter","Saturn"], answer:"Jupiter"},
      {q:"Who wrote Ramayana?", options:["Valmiki","Vyasa","Tulsidas","Kalidasa"], answer:"Valmiki"},
      {q:"Which gas do humans breathe in?", options:["Carbon Dioxide","Oxygen","Nitrogen","Helium"], answer:"Oxygen"},
      {q:"What is 5 × 6?", options:["25","30","35","20"], answer:"30"}
    ];

    function loadRandomQuestion() {
      const randomQuestion = questions[Math.floor(Math.random() * questions.length)];
      document.getElementById("question").textContent = randomQuestion.q;
      const optionsDiv = document.getElementById("options");
      optionsDiv.innerHTML = "";
      document.getElementById("result").textContent = "";
      randomQuestion.options.forEach(opt => {
        const btn = document.createElement("button");
        btn.textContent = opt;
        btn.onclick = () => {
          if(opt === randomQuestion.answer){
            btn.classList.add("correct");
            document.getElementById("result").textContent = "✅ Correct!";
          } else {
            btn.classList.add("wrong");
            document.getElementById("result").textContent = "❌ Wrong! Correct answer: " + randomQuestion.answer;
          }
          Array.from(optionsDiv.children).forEach(b => b.disabled = true);
        };
        optionsDiv.appendChild(btn);
      });
    }
    window.onload = loadRandomQuestion;

    // Blog Loading
    function loadPosts() {
      const postsContainer = document.getElementById("postsContainer");
      const posts = JSON.parse(localStorage.getItem("blogPosts")) || [
        { title: "Welcome Post", content: "This is the first blog post.", date: new Date() }
      ];
      postsContainer.innerHTML = "";
      posts.reverse().forEach(post => {
        const postEl = document.createElement("div");
        postEl.classList.add("post");
        postEl.innerHTML = `
          <h2>${post.title}</h2>
          <small>${new Date(post.date).toLocaleString()}</small>
          <p>${post.content}</p>
        `;
        postsContainer.appendChild(postEl);
      });
    }
    loadPosts();
  </script>

</body>
</html>
