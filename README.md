<h1 align="center">Hola 💕, soy Celeste</h1>

###

<div align="center">
  <img height="200" src="https://soyhorizonte.com/wp-content/uploads/2020/10/JS-by-SoyHorizonte.gif"  />
</div>

###

<br clear="both">

<p align="center">💕FRONT-END DEVELOPER💕</p>

###

<h2 align="center">SOBRE MI</h2>

###

<br clear="both">

<p align="left">Desarrolladora frontend recientemente graduada de un bootcamp intensivo en Desarrollo Front-end. <br>Mi pasión por la tecnología y el diseño de interfaces web me ha llevado a adquirir habilidades en HTML, CSS, JavaScript, Bootstrap, SASS, Vue.js, Vuex, Firebase y jQuery. <br> Estoy emocionada por aplicar mis conocimientos en proyectos innovadores y seguir creciendo en el campo del desarrollo web.</p>

###

<br clear="both">

<img src="https://raw.githubusercontent.com/Celeste941/Celeste941/output/snake.svg" alt="Snake animation" />

###

<h2 align="left">TECNOLOGIAS</h2>

###

<div align="left">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" height="40" alt="html5 logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" height="40" alt="css3 logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" height="40" alt="javascript logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vuejs/vuejs-original.svg" height="40" alt="vuejs logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/sass/sass-original.svg" height="40" alt="sass logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/bootstrap/bootstrap-original.svg" height="40" alt="bootstrap logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" height="40" alt="git logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/npm/npm-original-wordmark.svg" height="40" alt="npm logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg" height="40" alt="nodejs logo"  />
</div>

###

<h2 align="left">CONTACTO</h2>

###

<div align="left">
  <a href="https://www.linkedin.com/in/ana-celeste-perez-oviedo-29bb0218a/" target="_blank">
    <img src="https://raw.githubusercontent.com/maurodesouza/profile-readme-generator/master/src/assets/icons/social/linkedin/default.svg" width="52" height="40" alt="linkedin logo"  />
  </a>
  <a href="https://wa.me/56979368299" target="_blank">
    <img src="https://raw.githubusercontent.com/maurodesouza/profile-readme-generator/master/src/assets/icons/social/whatsapp/default.svg" width="52" height="40" alt="whatsapp logo"  />
  </a>
</div>

###
name: Generate snake animation

on:
  schedule: # execute every 12 hours
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


      - name: push snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
