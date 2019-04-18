<template>
  <div id="app">
    <header>
      <router-link to="/" class="main-header"><h1>Is it your birthday!?</h1></router-link>
    </header>
    <router-view/>
  </div>
</template>

<style>
html {
  box-sizing: border-box;
}
*, *:before, *:after {
  box-sizing: inherit;
}

html, body {
  margin: 0;
  padding: 0;
  height: 100%;
}

body {
  background: lavender;

}

header {
  background-color: lavender;
  margin: 0;
  height: 100%;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0;
}

.main-header {
  text-decoration: none;
  color: black;
}

.input-form {
  max-width: 400px;
  margin: auto;
}

</style>
