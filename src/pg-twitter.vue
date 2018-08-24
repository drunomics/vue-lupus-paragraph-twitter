<template>
  <div class="paragraph paragraph--twitter">
    <div class="paragraph__field-media" v-html="embedHtml">
    </div>
  </div>
</template>
<script>
  import axios from 'axios';
  import jsonpAdapter from 'axios-jsonp';
  export default {
    name: 'PgTwitter',
    props: {
      dataTwitterUrl: { type: String, default: () => '' },
    },
    data() {
      return {
        embedHtml: '',
      }
    },
    created() {
      if (this.dataTwitterUrl !== '') {
        axios.get('https://publish.twitter.com/oembed?url=' + this.dataTwitterUrl, {adapter: jsonpAdapter,}).then(response => {
          this.embedHtml = response.data.html;
          // The response HTML from instagram contains this script tag already,
          // but via v-html it does not get executed so we need to add this element here manually.
          const script = document.createElement('script')
          script.src = '//platform.twitter.com/widgets.js'
          document.head.appendChild(script)
        });
      }
    },
  };
</script>
