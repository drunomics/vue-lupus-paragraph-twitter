# vue-lupus-paragraph-twitter
Example Vue twitter paragraph component.

Note this component serves as example component and is not regularly maintained.


## Install

via npm:
`npm install https://github.com/drunomics/vue-lupus-paragraph-twitter.git`


import it:

```
import PgTwitter from 'vue-lupus-paragraph-twitter';

Vue.component('pg-twitter', PgTwitter);
```

## Properties
You can pass the following props:

- `src` ( string )
  The tweet's url.

## Slots
You can use the following slots

- `title` ( default )
  A title.

## Example
```
<pg-twitter src="#the-twitter-post-link">
  <h3 slot="title">The title value</h3>
</pg-twitter>
```
