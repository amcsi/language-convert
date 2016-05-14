<template>
  <div>
    <template v-if="active">
      <h2>Edit <span class="highlighted">{{languageConfig.displayName}}</span> here.</h2>
      <textarea if cols="20" rows="1" class="form-control" v-model="code"></textarea>
    </template>
    <template v-else>
      <h2 v-else><span class="highlighted">{{languageConfig.displayName}}</span> output.</h2>
      <textarea cols="20" rows="1" class="form-control" readonly>{{activeCode | convert}}</textarea>

    </template>

  </div>
</template>
<script>
  import config from '../config'

  import js2php from 'js2php'

  /** @class LanguageEditor */
  export default {
    props: {
      active: {
        type: Boolean,
        default: false
      },
      language: {
        type: String,
        validator (language) {
          return !!config.languages[language]
        }
      },
      activeCode: {
        type: String,
        required: true
      },
      code: {
        type: String,
        required: true
      }
    },
    computed: {
      languageConfig ({language}) {
        return config.languages[language]
      }
    },
    filters: {
      convert (value) {
        if (this.language === 'php') {
          try {
            let convertedValue = js2php(value)
            if (convertedValue.indexOf('<?php\n') === 0) {
              convertedValue = convertedValue.substring(5)
            }
            return convertedValue
          } catch (e) {
            return 'Syntax error in source'
          }
        }
      }
    },
    components: {}
  }
</script>
<style scoped>
  .highlighted {
    color: rebeccapurple;
  }

  textarea {
    width: 100%;
    min-height: 100px;
    font-family: monospace;
  }
</style>
