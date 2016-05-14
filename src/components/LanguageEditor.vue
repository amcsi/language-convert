<template>
    <div v-if="active">Edit <span class="highlighted">{{languageConfig.displayName}}</span> here.</div>
    <div v-else><span class="highlighted">{{languageConfig.displayName}}</span> output.</div>

    <textarea cols="20" rows="1" class="form-control"></textarea>
</template>
<script>
  import config from '../config'
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
      }
    },
    computed: {
      languageConfig ({language}) {
        return config.languages[language]
      }
    },
    components: {}
  }
</script>
<style scoped>
  textarea {
    width: 100%;
    min-height: 100px;
  }
</style>
