<!-- index.html -->

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>AidenOXis - Data Science Enthusiast</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <header>
    <h2>Hi 👋! My name is AidenOXis and I'm a Data Science Enthusiast, from [Your Location]</h2>
  </header>

  <section>
    <p>👀 I’m interested in Data Science, Video Games, and 3D Rendering</p>
    <p>🌱 I’m currently learning Java and Python</p>
    <p>💞️ I’m looking to collaborate with those who are interested in my ideas</p>
    <p>📫 How to reach me: on Telegram</p>
    <p>😄 Pronouns: he/him</p>
  </section>

  <section>
    <h2>Stats</h2>
    <img src="https://github-readme-stats.vercel.app/api?username=AidenOXis&hide_title=false&hide_rank=false&show_icons=true&include_all_commits=true&count_private=true&disable_animations=false&theme=dracula&locale=en&hide_border=false" alt="Stats graph" />
    <img src="https://github-readme-stats.vercel.app/api/top-langs?username=AidenOXis&locale=en&hide_title=false&layout=compact&card_width=320&langs_count=5&theme=dracula&hide_border=false" alt="Languages graph" />
  </section>

  <section>
    <h2>Skills</h2>
    <ul>
      <li><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" alt="JavaScript logo" /></li>
      <li><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg" alt="TypeScript logo" /></li>
      <li><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg" alt="React logo" /></li>
      <li><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" alt="HTML5 logo" /></li>
      <li><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" alt="CSS3 logo" /></li>
      <li><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" alt="Python logo" /></li>
      <li><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/csharp/csharp-original.svg" alt="C# logo" /></li>
    </ul>
  </section>

  <section>
    <h2>Links</h2>
    <ul>
      <li><a href="https://www.youtube.com/" target="_blank"><img src="https://img.shields.io/static/v1?message=YouTube&logo=youtube&label=&color=FF0000&logoColor=white&labelColor=&style=for-the-badge" alt="YouTube logo" /></a></li>
      <li><a href="https://www.instagram.com/" target="_blank"><img src="https://img.shields.io/static/v1?message=Instagram&logo=instagram&label=&color=E4405F&logoColor=white&labelColor=&style=for-the-badge" alt="Instagram logo" /></a></li>
      <li><a href="https://www.twitch.tv/" target="_blank"><img src="https://img.shields.io/static/v1?message=Twitch&logo=twitch&label=&color=9146FF&logoColor=white&labelColor=&style=for-the-badge" alt="Twitch logo" /></a></li>
      <li><a href="https://discord.com/" target="_blank"><img src="https://img.shields.io/static/v1?message=Discord&logo=discord&label=&color=7289DA&logoColor=white&labelColor=&style=for-the-badge" alt="Discord logo" /></a></li>
      <li><a href="mailto:your-email@gmail.com"><img src="https://img.shields.io/static/v1?message=Gmail&logo=gmail&label=&color=D14836&logoColor=white&labelColor=&style=for-the-badge" alt="Gmail logo" /></a></li>
           <li><a href="https://www.linkedin.com/in/your-profile" target="_blank"><img src="https://img.shields.io/static/v1?message=LinkedIn&logo=linkedin&label=&color=0077B5&logoColor=white&labelColor=&style=for-the-badge" alt="LinkedIn logo" /></a></li>
    </ul>
  </section>

  <footer>
    <img src="https://raw.githubusercontent.com/maurodesouza/maurodesouza/output/snake.svg" alt="Snake animation" />
  </footer>

</body>
</html>

<!-- styles.css -->

body {
  font-family: Arial, sans-serif;
  margin: 20px;
}

header {
  background-color: #f0f0f0;
  padding: 20px;
  text-align: center;
}

section {
  margin-bottom: 20px;
}

h2 {
  margin-top: 0;
}

ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

li {
  display: inline-block;
  margin-right: 20px;
}

a {
  text-decoration: none;
  color: #337ab7;
}

a:hover {
  color: #23527c;
}

img {
  max-width: 100%;
  height: auto;
  margin: 20px;
}

/* Add more styles as needed */

<!-- workflow.yml -->

name: Generate snake animation

on:
  schedule:
    - cron: "* */12 * * *"
  workflow_dispatch:
  push:
    branches:
      - master

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: generate snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: dist/snake.svg?palette=github-dark

      - name: deploy to GitHub Pages
        uses: actions/checkout@v2
        uses: actions/setup-node@v2
        run: |
          npm install
          npm run build
          npm run deploy
