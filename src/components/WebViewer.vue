<template>
  <div ref='viewer'></div>
</template>

<script>
import WebViewer from '@pdftron/pdfjs-express'

export default {
  name: 'WebViewer',
  props: {
    path: String,
    url: String
  },
  mounted: function () {
        WebViewer({
            path: this.path,
            initialDoc: this.url,
          }, this.$refs.viewer).then((instance) => {
            instance.disableFeatures([instance.Feature.Print, instance.Feature.Copy, instance.Feature.Download]);
          });
    }
}
  document.addEventListener('keyup', (e) => {
    if (e.key == 'PrintScreen') {
      navigator.clipboard.writeText('');
    }
  });
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
div {
  width: 100%; 
  height: 100vh;
}
</style>
