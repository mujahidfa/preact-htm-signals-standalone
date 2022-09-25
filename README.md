# Preact + HTM + Preact Signals standalone
A single, standalone version of [Preact](https://github.com/preactjs/preact), [HTM](https://github.com/developit/htm) and [Preact Signals](https://github.com/preactjs/signals). No external dependencies, just one single file.

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

Main motivation is to use Preact + HTM + Preact Signals directly via CDN in a single script tag/import without any build step. Inspired by the [standalone version of Preact + HTM](https://github.com/developit/htm#installation).

All rights belong to [Preact](https://github.com/preactjs/preact), [HTM](https://github.com/developit/htm) and [Preact Signals](https://github.com/preactjs/signals) owners/maintainers.

## Building from source
Install and bundle them (via [Microbundle](https://github.com/developit/microbundle)):
```
git clone https://github.com/mujahidfa/preact-htm-signals-standalone.git
cd preact-htm-signals-standalone
pnpm i
pnpm run bundle
```