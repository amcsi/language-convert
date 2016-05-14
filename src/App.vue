<template>
  <div>
    <h1>Language converter</h1>
    <div>
      <div v-for="(languageKey, code) in codes">
        <div class="col-md-6">
          <language-editor :active="active === languageKey" :language="languageKey"
            :active-code="codes[active]" :code.sync="code"></language-editor>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import LanguageEditor from './components/LanguageEditor'

const state = {
  active: 'js',
  codes: {
    js: '',
    php: ''
  }
}

/** @class App */
export default {
  components: {
    LanguageEditor
  },
  data () {
    return state
  },
  computed: {
    php () {
      return state.codes.js
    }
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

#app a {
  color: #42b983;
  text-decoration: none;
}
</style>
