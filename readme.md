
# auto example svelte

## creation process

initialise repo

```
pnpm init -y
```

add `vite.config.js`

```js
import { defineConfig } from 'vite'
import { svelte } from '@sveltejs/vite-plugin-svelte'

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [svelte()]
})
```

install libraries

```
pnpm i -D vite svelte @sveltejs/vite-plugin-svelte
pnpm i @autolib/auto
```

create `index.html`

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" href="/favicon.ico" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>auto example svelte</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/app/main.js"></script>
  </body>
</html>
```

create `app/main.js`

```js
import App from './App.svelte'

const app = new App({
  target: document.getElementById('root')
})

export default app
```

create `app/state.js`

```js
import auto from '@autolib/auto';

let _ = auto({

	first_name: 'Jim',
	last_name: 'Cricket',
	name: (_) => _.first_name + ' ' + _.last_name
})

export default _;
````

create `app/App.svelte`

```svelte
<script>
	import _ from './state.js';
	let { name } = _['#'];
</script>

<p>Hello {$name}</p>
```

create `.gitignore`

```
.DS_Store
node_modules/
```

## installing (after clone)

just run

```
pnpm i
```

## running

just run

```
vite
```

and a server should popup (normally `localhost:3000`).
just browse to that.

## automatic refresh

because of `vite` you can change the source
and everything will reload in the browser
as soon as you save.
