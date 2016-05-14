<template>
  <h1>Language converter</h1>
  <div>
    <div class="col-md-6">
      <language-editor language="js"></language-editor>
    </div>
    <div class="col-md-6">
      <language-editor language="php"></language-editor>
    </div>
  </div>
</template>

<script>
import LanguageEditor from './components/LanguageEditor'

/** @class App */
export default {
  components: {
    LanguageEditor
  }
}
</script>

<style>
html {
  height: 100%;
}

body {
  height: 100%;
}

#app {
  color: #2c3e50;
  margin-top: -100px;
  max-width: 600px;
  font-family: Source Sans Pro, Helvetica, sans-serif;
  text-align: center;
}

#app a {
  color: #42b983;
  text-decoration: none;
}

.logo {
  width: 100px;
  height: 100px
}
</style>
