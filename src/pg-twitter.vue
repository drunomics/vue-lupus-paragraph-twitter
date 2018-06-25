<template>
  <div class="paragraph paragraph--twitter">
    <div class="paragraph__field-media">
      <slot
        name="field_media"
        v-html="embedHtml"
      >
      </slot>
      <slot />
    </div>
  </div>
</template>
<script>
  import axios from 'axios';
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
        axios.get('https://publish.twitter.com/oembed?url=' + this.dataTwitterUrl).then(response => {
          this.embedHtml = response.html;
        });
      }
    },
  };
</script>
