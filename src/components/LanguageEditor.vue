<template>
    <div>this is template body</div>

    <textarea cols="20" rows="20"></textarea>
</template>
<script>
  /** @class LanguageEditor */
  const LanguageEditor = {
    data () {
      return {
        msg: 'hello vue'
      }
    },
    components: {}
  }
  export default LanguageEditor
</script>
<style scoped>
  textarea {
    width: 100%;
  }
</style>
