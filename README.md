# vue-lupus-paragrpah-twitter
Vue twitter paragraph component.



## Install

via npm:
`npm install https://github.com/drunomics/vue-lupus-paragraph-twitter.git`


import it:

```
import { PgTwitter } from 'vue-lupus-paragraph-twitter';

Vue.component('pg-twitter', PgTwitter);
```

## Options
You can pass options via props:

```
<pg-twitter
  type="{{ type }}"
  data-twitter-url="/twitter/url"
>
```
- `data-twitter-url` ( string )
  The pin's url.