<template>
  <div class="paragraph paragraph--twitter">
    <slot name="title" />
    <div class="twitter-post" v-html="embedHtml">
    </div>
  </div>
</template>
<script>
import axios from 'axios'
import jsonpAdapter from 'axios-jsonp'
export default {
  name: 'PgTwitter',
  props: {
    src: { type: String, default: () => '' }
  },
  data () {
    return {
      embedHtml: ''
    }
  },
  created () {
    if (this.dataUrl !== '') {
      axios.get('https://publish.twitter.com/oembed?url=' + this.src, { adapter: jsonpAdapter }).then(response => {
        this.embedHtml = response.data.html
        // The response HTML from instagram contains this script tag already,
        // but via v-html it does not get executed so we need to add this element here manually.
        const script = document.createElement('script')
        script.src = '//platform.twitter.com/widgets.js'
        script.async = true
        document.head.appendChild(script)
      })
    }
  }
}
</script>
