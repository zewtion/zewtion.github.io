<template>
  <div class="app-container">
    <editor v-model="vContent" :config="editorConfig" />
  </div>
</template>

<script>
// require('ckeditor4-vue/dist/ckeditor')
import CKEditor from 'ckeditor4-vue/dist/legacy'

export default {
  name: 'EditorSample',
  components: { editor: CKEditor.component },
  data() {
    return {
      editorUrl: '/ckeditor4/ckeditor.js',
      vContent: '<p> welcome fnd </p>',
      editorConfig: {}
    }
  }
}
</script>

<style></style>
