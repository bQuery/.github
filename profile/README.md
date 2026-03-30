<div align="center">

<img src="https://raw.githubusercontent.com/bQuery/bQuery/refs/heads/main/assets/bquerry-logo.svg" height="120rem" width="auto" />

# bQuery

**The jQuery for the Modern Web Platform.**

[![npm version](https://img.shields.io/npm/v/@bquery/bquery?style=flat-square&color=CB3837&logo=npm)](https://www.npmjs.com/package/@bquery/bquery)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)](https://opensource.org/licenses/MIT)
[![TypeScript](https://img.shields.io/badge/TypeScript-first-3178C6?style=flat-square&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Zero Build](https://img.shields.io/badge/Zero-Build-8B5CF6?style=flat-square)](#)
[![GitHub Org](https://img.shields.io/badge/GitHub-bQuery-181717?style=flat-square&logo=github)](https://github.com/bQuery)

---

**Slim · Modular · Reactive · Secure · Zero-build**

A TypeScript-first library that combines jQuery's beloved DOM workflow
with modern features like **signals**, **Web Components**, **motion utilities**,
**SPA routing**, **forms**, **i18n**, **accessibility**, **drag & drop**, **media signals**,
**SSR**, and **20 dedicated entry points** — without a mandatory build step.

[📖 Documentation](https://bquery.flausch-code.de/) •
[🧩 UI Components](https://bquery.github.io/ui/) •
[📦 npm](https://www.npmjs.com/package/@bquery/bquery)

</div>

---

## 🏗️ Projects

| Repository | Description | Links |
|:---:|:---|:---:|
| **[bQuery](https://github.com/bQuery/bQuery)** | Core library — DOM manipulation, reactivity, components, motion, routing, and more | [Docs](https://bquery.flausch-code.de/) · [npm](https://www.npmjs.com/package/@bquery/bquery) |
| **[ui](https://github.com/bQuery/ui)** | UI component showcase built with bQuery | [Docs](https://bquery.github.io/ui/) |

---

## ✨ Why bQuery?

- 🌳 **Tree-shakeable** — import only what you need from 20 dedicated entry points
- 🔷 **TypeScript-first** — full types and strong IDE support
- 📦 **Modular** — core stays small, extras are opt-in
- 🔒 **Security-focused** — DOM writes are sanitized by default; Trusted Types supported
- ⚡ **Zero-build** — works straight from a CDN with ES Modules
- 🧪 **Storybook-ready** — default components with dedicated story template helpers

---

## 📐 Architecture

```text
@bquery/bquery
├── core/                    ─  Selectors, DOM manipulation, events, traversal, utilities
├── reactive/                ─  Signals, computed, effects, async data, fetch composables
├── component/               ─  Web Components with scoped reactivity & Shadow DOM control
├── storybook/               ─  Safe story template helpers with boolean-attribute shorthand
├── motion/                  ─  Transitions, FLIP, morphing, parallax, typewriter, springs
├── security/                ─  Sanitizer, CSP, Trusted Types, trusted fragments
├── platform/                ─  Storage, cache, cookies, page meta, announcers, config
├── router/                  ─  SPA routing, constrained params, guards, <bq-link>
├── store/                   ─  State management, persistence, migrations, action hooks
├── view/                    ─  Declarative DOM bindings (bq-text, bq-for, bq-if…)
├── forms/                   ─  Reactive form state with sync/async validation
├── i18n/                    ─  Reactive locales, interpolation, pluralization, formatting
├── a11y/                    ─  Focus traps, live regions, roving tabindex, skip links
├── dnd/                     ─  Draggable elements, droppable zones, sortable lists
├── media/                   ─  Reactive viewport, network, battery, geolocation signals
├── plugin/                  ─  Global plugin registration for directives & components
├── devtools/                ─  Runtime inspection for signals, stores, components
├── testing/                 ─  Component mounting, mock helpers, async test utilities
└── ssr/                     ─  Server-side rendering, hydration, store serialization
```

---

## 🚀 Quick Start

### Install via npm

```bash
npm install @bquery/bquery
```

### Or use directly from CDN (zero-build)

```html
<script type="module">
  import { $, signal } from 'https://unpkg.com/@bquery/bquery@1/dist/full.es.mjs';

  const count = signal(0);
  $('#counter').text(`Count: ${count.value}`);
</script>
```

---

## 💡 Examples

### Core — DOM & Events

```ts
import { $, $$ } from '@bquery/bquery/core';

// jQuery-style selectors & chaining
$('#box')
  .addClass('active')
  .css({ opacity: '0.8' })
  .attr('data-state', 'ready');

// Event delegation for dynamic content
$('#list').delegate('click', '.item', (event, target) => {
  console.log('Clicked:', target.textContent);
});

// New in 1.7.0: jQuery-parity helpers
const pos = $('#box').position();
const width = $('#box').outerWidth(true);
```

### Reactivity — Signals

```ts
import { signal, computed, effect } from '@bquery/bquery/reactive';

const count = signal(0);
const doubled = computed(() => count.value * 2);

effect(() => console.log(`Count: ${count.value}, Doubled: ${doubled.value}`));

count.value++; // → "Count: 1, Doubled: 2"
```

### Components — Web Components

```ts
import { component } from '@bquery/bquery/component';

component('user-card', {
  props: {
    username: { type: String, required: true },
  },
  // New in 1.7.0: Shadow DOM mode control
  shadow: 'open',
  // New in 1.7.0: attribute observation & lifecycle hooks
  observeAttributes: ['username'],
  onAttributeChanged(name, oldVal, newVal) {
    console.log(`${name} changed: ${oldVal} → ${newVal}`);
  },
  render({ props }) {
    return `<div class="card"><h2>${props.username}</h2></div>`;
  },
});
```

### Router — SPA Navigation

```ts
import { createRouter, navigate, useRoute } from '@bquery/bquery/router';

const router = createRouter({
  routes: [
    { path: '/', name: 'home', component: HomePage },
    // New in 1.7.0: regex-constrained params
    { path: '/user/:id(\\d+)', name: 'user', component: UserPage },
    // New in 1.7.0: redirectTo
    { path: '/old-path', redirectTo: '/new-path' },
    { path: '*', component: NotFound },
  ],
});

// New in 1.7.0: fine-grained route signals
const route = useRoute();
```

### Store — State Management

```ts
import { createStore, createPersistedStore } from '@bquery/bquery/store';

const counterStore = createStore({
  id: 'counter',
  state: () => ({ count: 0 }),
  actions: {
    increment() { this.count++; },
  },
});

// New in 1.7.0: action hooks
counterStore.$onAction(({ name, args, after }) => {
  after(() => console.log(`${name} completed`));
});

// New in 1.7.0: expanded persistence options
const settingsStore = createPersistedStore({
  id: 'settings',
  state: () => ({ theme: 'dark' }),
  key: 'app-settings',
  version: 2,
  migrate: (state, version) => ({ ...state, migrated: true }),
});
```

### Motion — Animations

```ts
import { animate, morphElement, parallax, typewriter } from '@bquery/bquery/motion';

await animate(card, {
  keyframes: [{ opacity: 0 }, { opacity: 1 }],
  options: { duration: 300 },
});

// New in 1.7.0
morphElement(source, target, { duration: 500 });
parallax('#bg', { speed: 0.5 });
typewriter('#text', 'Hello, world!', { speed: 50 });
```

### View — Declarative Bindings

```html
<p bq-text="count"></p>
<button bq-on:click="increment">+1</button>
<ul>
  <li bq-for="item in items" bq-text="item"></li>
</ul>
<input bq-model="count" type="number" />
<div bq-if="count > 5">Count is high!</div>
```

```ts
import { mount } from '@bquery/bquery/view';
import { signal } from '@bquery/bquery/reactive';

const count = signal(0);
const items = signal(['Apple', 'Banana', 'Cherry']);

mount('#app', {
  count,
  items,
  increment: () => count.value++,
});
```

### New in 1.7.0 — First-class Module Entry Points

```ts
// All new dedicated entry points available since 1.7.0
import { createForm, required, email } from '@bquery/bquery/forms';
import { createI18n } from '@bquery/bquery/i18n';
import { trapFocus, rovingTabIndex } from '@bquery/bquery/a11y';
import { draggable, droppable, sortable } from '@bquery/bquery/dnd';
import { mediaQuery, useViewport, clipboard } from '@bquery/bquery/media';
import { use } from '@bquery/bquery/plugin';
import { enableDevtools, inspectSignals } from '@bquery/bquery/devtools';
import { renderComponent, fireEvent, waitFor } from '@bquery/bquery/testing';
import { renderToString, hydrateMount } from '@bquery/bquery/ssr';
```

---

## 🌐 Browser Support

| Browser | Version | Support |
|---------|---------|---------|
| Chrome  | 90+     | ✅ Full |
| Firefox | 90+     | ✅ Full |
| Safari  | 15+     | ✅ Full |
| Edge    | 90+     | ✅ Full |

---

## 🤝 Contributing

We welcome contributions! Check out the individual repos for guidelines:

- [bQuery Core](https://github.com/bQuery/bQuery)
- [bQuery UI](https://github.com/bQuery/ui)

---

## 📄 License

All projects in this organization are licensed under the **MIT License**.

---

<div align="center">

Made with ❤️ by the **bQuery** team

[Website](https://bquery.flausch-code.de/) · [GitHub](https://github.com/bQuery) · [npm](https://www.npmjs.com/package/@bquery/bquery)

</div>
