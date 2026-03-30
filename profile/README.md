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
and **SPA routing** — without a mandatory build step.

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

- 🌳 **Tree-shakeable** — import only what you need
- 🔷 **TypeScript-first** — full types and strong IDE support
- 📦 **Modular** — core stays small, extras are opt-in
- 🔒 **Security-focused** — DOM writes are sanitized by default; Trusted Types supported
- ⚡ **Zero-build** — works straight from a CDN with ES Modules

---

## 📐 Architecture

```text
@bquery/bquery
├── core/        ~11.3 KB  ─  Selectors, DOM manipulation, events, utilities
├── reactive/     ~0.3 KB  ─  Signals, computed, effects
├── component/    ~1.9 KB  ─  Lightweight Web Components with props
├── motion/       ~4.0 KB  ─  View transitions, FLIP, springs, timelines
├── security/                ─  Sanitizer, CSP, Trusted Types
├── platform/                ─  Storage, cache, notifications
├── router/       ~2.2 KB  ─  SPA routing, navigation guards
├── store/                   ─  State management, persistence
└── view/                    ─  Declarative DOM bindings (bq-text, bq-for, bq-if…)
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
  render({ username }) {
    return `<div class="card"><h2>${username}</h2></div>`;
  },
});
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
