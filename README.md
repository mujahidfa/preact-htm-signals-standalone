# Preact + HTM + Preact Signals standalone
[![](https://data.jsdelivr.com/v1/package/npm/preact-htm-signals-standalone/badge)](https://www.jsdelivr.com/package/npm/preact-htm-signals-standalone)

A single, standalone version of [Preact](https://github.com/preactjs/preact), [HTM](https://github.com/developit/htm) and [Preact Signals](https://github.com/preactjs/signals). No external dependencies, just one single file.

One single file that you can use via [CDN](https://cdn.jsdelivr.net/npm/preact-htm-signals-standalone/dist/standalone.js) or [download locally](https://github.com/mujahidfa/preact-htm-signals-standalone/blob/main/dist/standalone.js) for offline use.

## Usage
### Direct CDN import in HTML
```html
<div id="app"></div>
<script type="module">
  import { html, render, signal } from "https://cdn.jsdelivr.net/npm/preact-htm-signals-standalone/dist/standalone.js";

  const count = signal(0);

  function App() {
    return html`
      <div>
        <h1 class>Hello World!</h1>
        <button onClick=${() => (count.value += 1)}>
          Increment with signal
        </button>
        <p>Counter: ${count}</p>
      </div>
    `;
  }

  render(html`<${App} />`, document.getElementById("app"));
</script>
```
### Via npm (not recommended)
I don't recommend installing this package via NPM. It's best to install [Preact](https://github.com/preactjs/preact), [HTM](https://github.com/developit/htm) and [Preact Signals](https://github.com/preactjs/signals) separately:
```sh
npm install preact htm @preact/signals
# or yarn
yarn add preact htm @preact/signals
# or pnpm
pnpm install preact htm @preact/signals
```

## Motivation and goals
My main motivation is to be able to download the entirety of Preact + HTM + Preact Signals offline in a single file.

You can absolutely do the following (and it works fine):
```html
<script type="module">
import { h, render } from 'https://cdn.skypack.dev/preact';
import htm from 'https://cdn.skypack.dev/htm';
import { signal } from 'https://cdn.skypack.dev/@preact/signals';
const html = htm.bind(h);
</script>
```

or go shorter and do this:
```html
<script type="module">
import { html, render } from "https://esm.sh/htm/preact";
import { signal } from "https://esm.sh/@preact/signals";
</script>
```

or even shorter (via [npm.reversehttp.com](https://npm.reversehttp.com/), thanks [Jason Miller](https://github.com/developit) for the tool!):
```html
<script type="module">
import { html, render, signal } from "https://npm.reversehttp.com/preact,htm/preact,@preact/signals";
</script>
```

However, due to my work limitations (i.e. my internal Preact apps run on restricted corp intranet), having a downloadable, offline version is required, hence the need for a prebundled, no-dependency, single script that I can easily download and use offline.

Simply put, my ideal situation looks like this (made possible by this project):
```html
<script type="module">
// Download the prebundled scripts locally for offline use
import { html, render, signal } from "./preact-htm-signals-standalone.js";
</script>
```

Inspired by the [standalone version of Preact + HTM](https://github.com/developit/htm#installation).

All rights belong to [Preact](https://github.com/preactjs/preact), [HTM](https://github.com/developit/htm) and [Preact Signals](https://github.com/preactjs/signals) owners/maintainers.

## Building from source
Install and bundle them (via [Microbundle](https://github.com/developit/microbundle)):
```
git clone https://github.com/mujahidfa/preact-htm-signals-standalone.git
cd preact-htm-signals-standalone
pnpm i
pnpm run bundle
```