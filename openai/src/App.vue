<template>
  <div id="app">
    <router-view />
  </div>
</template>

<style>
:root {
  --primary: #64B6AC;
  --secondary: #C0FDFB;
  --cardBackground: #5D737E;
  --consoleBackground: #667E8A;
  --background: #2D383D;
  --textArea: #95B8C9;
  --textTitles: #DAFFEF;
  --textSubtitles: #5D737E;
  --textTag: #2F6962;
  --mainTitle: #29403D;
  --wave: #A6FFF5;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
@font-face {
  font-family: "M PLUS Code Latin";
  src: url("./assets/MPLUSCodeLatin-Medium.ttf");
}

body {
  background-color: var(--background);
}

h1, h2, h3, h4, h5, h6 {
  color: var(--textTitles);
  text-align: left;
  padding: 10px;
}

p {
  color: var(--textSubtitles);
}

button {
  width: 100px;
  height: 40px;
  border-radius: 8px;
  border: 1px solid black;
  font-size: 1.2em;
  font-weight: bold;
  padding: 10px;
  cursor: pointer;
  border: none;
  transition: all 0.2s;
}

button:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.5);
  border-radius: 4px;
}


* {
  box-sizing: border-box;
  margin : 0;
  padding : 0;
}

</style>
