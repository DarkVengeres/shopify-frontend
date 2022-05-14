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
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
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

* {
  box-sizing: border-box;
  margin : 0;
  padding : 0;
}

</style>
