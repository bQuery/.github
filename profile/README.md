<div align="center">

<img src="https://raw.githubusercontent.com/bQuery/bQuery/main/assets/bquerry-logo.svg" alt="bQuery.js" height="80" /><br/><br/>

# bQuery.js

**The full-stack web framework that speaks jQuery.**

<a href="https://www.npmjs.com/package/@bquery/bquery"><img src="https://img.shields.io/npm/v/@bquery/bquery?style=flat&logo=npm" alt="npm version"/></a>&nbsp;
<a href="https://bundlephobia.com/package/@bquery/bquery"><img src="https://img.shields.io/bundlephobia/minzip/@bquery/bquery?style=flat" alt="Bundle Size"/></a>&nbsp;
<a href="https://github.com/bQuery/bQuery/blob/main/LICENSE.md"><img src="https://img.shields.io/github/license/bquery/bquery?style=flat" alt="License"/></a><br/>
<a href="https://github.com/bQuery/bQuery/stargazers"><img src="https://img.shields.io/github/stars/bquery/bquery?style=flat&logo=github" alt="Stars"/></a>&nbsp;
<a href="https://github.com/bQuery/bQuery/issues"><img src="https://img.shields.io/github/issues/bquery/bquery?style=flat&logo=github" alt="Issues"/></a>&nbsp;
<a href="https://www.codefactor.io/repository/github/bquery/bquery"><img src="https://www.codefactor.io/repository/github/bquery/bquery/badge" alt="CodeFactor"/></a>&nbsp;
<a href="https://www.jsdelivr.com/package/npm/@bquery/bquery"><img src="https://data.jsdelivr.com/v1/package/npm/@bquery/bquery/badge" alt="jsDelivr"/></a>

---

*Batteries-included TypeScript framework for the modern web — signals, SSR, Web Components,
routing, and more — with a jQuery-inspired API and zero mandatory build step.*

[📖 Documentation](https://bquery.flausch-code.de/) •
[🧩 UI Components](https://bquery.github.io/ui/) •
[📦 npm](https://www.npmjs.com/package/@bquery/bquery)

</div>

---

> **New in 1.11.0:** Runtime-agnostic SSR now adds DOM-free fallback rendering, `renderToStringAsync()`, `renderToStream()`, `renderToResponse()`, runtime adapters, hydration strategies, store snapshots, and resumability hooks, alongside the new `@bquery/bquery/server` entry point for dependency-free backend routing and WebSocket sessions.

## 🏗️ Projects

| Repository | Description | Links |
|:---:|:---|:---:|
| **[bQuery](https://github.com/bQuery/bQuery)** | Core library — DOM manipulation, reactivity, components, motion, routing, and more | [Docs](https://bquery.flausch-code.de/) · [npm](https://www.npmjs.com/package/@bquery/bquery) |
| **[ui](https://github.com/bQuery/ui)** | UI component showcase built with bQuery | [Docs](https://bquery.github.io/ui/) |

---

## ✨ Highlights

- 🌐 **Full-stack by default** — signals, SSR, routing, server middleware, Web Components, and 15+ modules ship together
- 🌳 **Tree-shakeable** — import only what you need from 21 dedicated entry points
- 🔷 **TypeScript-first** — full types and strong IDE support
- 📦 **Modular** — core stays small, extras are opt-in
- 🔒 **Security-focused** — DOM writes are sanitized by default; Trusted Types and CSP helpers built in
- ⚡ **Zero-build** — works straight from a CDN with ES Modules, UMD, or IIFE builds
- 🧪 **Storybook-ready** — default components with dedicated story template helpers
- 🔁 **Reactive data across the stack** — fetch composables, HTTP clients, WebSocket / SSE, and REST helpers plug directly into signals

---

## 📐 Architecture

```text
@bquery/bquery
├── core/          ─  Selectors, DOM manipulation, events, traversal, utilities
├── reactive/      ─  Signals, computed, effects, async data, fetch composables, HTTP, WS/SSE
├── concurrency/   ─  Zero-build worker tasks, RPC, pools, collection helpers, pipelines (Experimental)
├── component/     ─  Web Components with scoped reactivity & configurable Shadow DOM
├── storybook/     ─  Safe story template helpers with boolean-attribute shorthand
├── motion/        ─  View transitions, FLIP, morphing, parallax, typewriter, springs, timelines
├── security/      ─  HTML sanitization, Trusted Types, CSP helpers, trusted fragments
├── platform/      ─  Storage, cache, cookies, page meta, announcers, notifications, config
├── router/        ─  SPA routing, constrained params, redirects, guards, <bq-link>
├── store/         ─  Signal-based state management, persistence, migrations, action hooks
├── view/          ─  Declarative DOM bindings (bq-text, bq-for, bq-if, bq-aria…)
├── forms/         ─  Reactive form state with sync/async validation and submit handling
├── i18n/          ─  Reactive locales, interpolation, pluralization, lazy loading, Intl formatting
├── a11y/          ─  Focus traps, live regions, roving tabindex, skip links, audits
├── dnd/           ─  Draggable elements, droppable zones, sortable lists
├── media/         ─  Reactive viewport, network, battery, geolocation, clipboard, DOM observers
├── plugin/        ─  Global plugin registration for custom directives & Web Components
├── devtools/      ─  Runtime inspection for signals, stores, components, timelines
├── testing/       ─  Component mounting, mock helpers, async test utilities
├── ssr/           ─  Runtime-agnostic SSR (Node ≥ 24, Deno, Bun), streaming, hydration (Experimental)
└── server/        ─  Backend routing, middleware, safe response helpers, WebSocket sessions (Experimental)
```

---

## 🚀 Quick Start

### Install via npm / bun / pnpm

```bash
# npm
npm install @bquery/bquery

# bun
bun add @bquery/bquery

# pnpm
pnpm add @bquery/bquery
```

### Or use directly from CDN (zero-build)

#### ES Modules (recommended)

```html
<script type="module">
  import { $, signal } from 'https://unpkg.com/@bquery/bquery@1/dist/full.es.mjs';

  const count = signal(0);
  $('#counter').text(`Count: ${count.value}`);
</script>
```

#### UMD (global variable)

```html
<script src="https://unpkg.com/@bquery/bquery@1/dist/full.umd.js"></script>
<script>
  const { $, signal } = bQuery;
  const count = signal(0);
</script>
```

---

## 💡 Examples

### Core — DOM & Events

```ts
import { $, $$ } from '@bquery/bquery/core';

$('#save').on('click', (event) => {
  console.log('Saved', event.type);
});

// Event delegation for dynamic content
$('#list').delegate('click', '.item', (event, target) => {
  console.log('Item clicked', target.textContent);
});

// jQuery-style chaining
$('#box').addClass('active').css({ opacity: '0.8' }).attr('data-state', 'ready');

$$('.container').find('.item').addClass('found');
```

### Reactivity — Signals

```ts
import { signal, computed, effect, watch, watchDebounce, batch, linkedSignal } from '@bquery/bquery/reactive';

const count = signal(0);
const doubled = computed(() => count.value * 2);

effect(() => console.log(`Count: ${count.value}, Doubled: ${doubled.value}`));

watchDebounce(count, (newVal) => console.log('Debounced:', newVal), 150);

batch(() => { count.value++; count.value++; });

const first = signal('Ada');
const last = signal('Lovelace');
const fullName = linkedSignal(
  () => `${first.value} ${last.value}`,
  (next) => { [first.value, last.value] = next.split(' '); }
);
```

### Components — Web Components

```ts
import { component, safeHtml, bool } from '@bquery/bquery/component';
import { sanitizeHtml, trusted } from '@bquery/bquery/security';

const badge = trusted(sanitizeHtml('<span class="badge">Active</span>'));

component('user-card', {
  props: {
    username: { type: String, required: true },
    age: { type: Number, validator: (v) => v >= 0 && v <= 150 },
  },
  state: { count: 0 },
  render({ props, state }) {
    return safeHtml`
      <button class="user-card" ${bool('disabled', state.count > 3)}>
        ${badge}
        <span>Hello ${props.username}</span>
      </button>
    `;
  },
});
```

### Router — SPA Navigation

```ts
import { createRouter, navigate, currentRoute } from '@bquery/bquery/router';
import { effect } from '@bquery/bquery/reactive';

const router = createRouter({
  routes: [
    { path: '/', name: 'home', component: HomePage },
    { path: '/user/:id', name: 'user', component: UserPage },
    { path: '/old-path', redirectTo: '/new-path' },
    { path: '*', component: NotFound },
  ],
});

router.beforeEach(async (to) => {
  if (to.path === '/admin' && !isAuthenticated()) {
    await navigate('/login');
    return false;
  }
});

effect(() => console.log('Current path:', currentRoute.value.path));
```

### Store — State Management

```ts
import { createStore, createPersistedStore, defineStore, watchStore } from '@bquery/bquery/store';

const counterStore = createStore({
  id: 'counter',
  state: () => ({ count: 0 }),
  getters: { doubled: (state) => state.count * 2 },
  actions: { increment() { this.count++; } },
});

const useCounter = defineStore('counter', {
  state: () => ({ count: 0 }),
  actions: { increment() { this.count++; } },
});

const settingsStore = createPersistedStore({
  id: 'settings',
  state: () => ({ theme: 'dark', language: 'en' }),
});
```

### Motion — Animations

```ts
import { animate, spring, transition, keyframePresets } from '@bquery/bquery/motion';

await transition({
  update: () => { $('#content').text('Updated'); },
  classes: ['page-transition'],
  skipOnReducedMotion: true,
});

await animate(card, {
  keyframes: keyframePresets.pop(),
  options: { duration: 240, easing: 'ease-out' },
});

const x = spring(0, { stiffness: 120, damping: 14 });
x.onChange((value) => { element.style.transform = `translateX(${value}px)`; });
await x.to(100);
```

### SSR & Server (New in 1.11.0)

```ts
import { renderToString, renderToResponse, createSSRContext } from '@bquery/bquery/ssr';
import { createServer } from '@bquery/bquery/server';

// Server-side rendering (Node ≥ 24, Deno, Bun)
const ctx = createSSRContext({ request: new Request('http://localhost/') });
ctx.head.add({ title: 'Home' });
ctx.assets.module('/app.js');
const response = await renderToResponse(
  '<html><head></head><body><p bq-text="label"></p></body></html>',
  { label: 'Hello' },
  { context: ctx, etag: true }
);

// Express-inspired backend routing
const app = createServer();
app.get('/hello/:name', (ctx) => ctx.json({ name: ctx.params.name }));
```

### All Entry Points

```ts
import { $, $$ } from '@bquery/bquery/core';
import { signal, computed, effect, useFetch, useWebSocket } from '@bquery/bquery/reactive';
import { runTask, createRpcWorker, createTaskPool } from '@bquery/bquery/concurrency';
import { component, defineComponent, registerDefaultComponents } from '@bquery/bquery/component';
import { storyHtml, when } from '@bquery/bquery/storybook';
import { animate, spring, transition } from '@bquery/bquery/motion';
import { sanitize, sanitizeHtml, trusted } from '@bquery/bquery/security';
import { storage, useCookie, definePageMeta, useAnnouncer } from '@bquery/bquery/platform';
import { createRouter, navigate } from '@bquery/bquery/router';
import { createStore, defineStore } from '@bquery/bquery/store';
import { mount, createTemplate } from '@bquery/bquery/view';
import { createForm, required, email } from '@bquery/bquery/forms';
import { createI18n } from '@bquery/bquery/i18n';
import { trapFocus, rovingTabIndex } from '@bquery/bquery/a11y';
import { draggable, droppable, sortable } from '@bquery/bquery/dnd';
import { mediaQuery, useViewport, useIntersectionObserver } from '@bquery/bquery/media';
import { use } from '@bquery/bquery/plugin';
import { enableDevtools, inspectSignals } from '@bquery/bquery/devtools';
import { renderComponent, fireEvent, waitFor } from '@bquery/bquery/testing';
import { renderToString, hydrateMount } from '@bquery/bquery/ssr';
import { createServer } from '@bquery/bquery/server';
```

---

## 📋 Modules at a Glance

| Module | Status | Description |
|---|---|---|
| **Core** | Stable | Selectors, DOM manipulation, events, traversal, and typed utilities |
| **Reactive** | Stable | Signals, computed, effects, async data, HTTP clients, polling, pagination, WebSocket / SSE |
| **Concurrency** | Experimental | Zero-build worker tasks, RPC helpers, worker pools, collection helpers, fluent pipelines |
| **Component** | Stable | Typed Web Components with scoped reactivity and configurable Shadow DOM |
| **Storybook** | Beta | Safe story template helpers with boolean-attribute shorthand |
| **Motion** | Stable | View transitions, FLIP, morphing, parallax, typewriter, springs, and timelines |
| **Security** | Stable | HTML sanitization, Trusted Types, CSP helpers, and trusted fragment composition |
| **Platform** | Stable | Storage, cache, cookies, page metadata, announcers, and shared runtime config |
| **Router** | Stable | SPA routing, constrained params, redirects, guards, `useRoute()`, and `<bq-link>` |
| **Store** | Stable | Signal-based state management, persistence, migrations, and action hooks |
| **View** | Beta | Declarative DOM bindings with `bq-*` directives for content, classes, forms, errors, ARIA |
| **Forms** | Beta | Reactive form state with sync/async validation and submit handling |
| **i18n** | Beta | Reactive locales, interpolation, pluralization, lazy loading, and Intl formatting |
| **A11y** | Beta | Focus traps, live-region announcements, roving tabindex, skip links, and audits |
| **DnD** | Beta | Draggable elements, droppable zones, and sortable lists |
| **Media** | Beta | Reactive browser/device signals for viewport, network, battery, geolocation, clipboard |
| **Plugin** | Beta | Global plugin registration for custom directives and Web Components |
| **Devtools** | Beta | Runtime inspection helpers for signals, stores, components, and timelines |
| **Testing** | Beta | Component mounting, mock signal/router helpers, and async test utilities |
| **SSR** | Experimental | Runtime-agnostic SSR (Node ≥ 24, Deno, Bun), streaming, hydration islands |
| **Server** | Experimental | Express-inspired backend routing, middleware, safe response helpers, WebSocket sessions |

---

## 🌐 Browser & Runtime Support

| Browser | Version | Support |
|---------|---------|---------|
| Chrome  | 90+     | ✅ Full |
| Firefox | 90+     | ✅ Full |
| Safari  | 15+     | ✅ Full |
| Edge    | 90+     | ✅ Full |

> **No IE support** by design.
>
> Server-side runtimes: **Node.js ≥ 24**, **Bun ≥ 1.3.13**, and **Deno 2** are supported for SSR and server modules.

---

## 🤝 Contributing

We welcome contributions! Check out the individual repos for guidelines:

- [bQuery Core](https://github.com/bQuery/bQuery)
- [bQuery UI](https://github.com/bQuery/ui)

---

## 🤖 AI Agent Support

This project provides dedicated context files for AI coding agents:

- **[AGENT.md](https://github.com/bQuery/bQuery/blob/main/AGENT.md)** — Architecture, module API reference, coding conventions, common tasks
- **[llms.txt](https://github.com/bQuery/bQuery/blob/main/llms.txt)** — Compact LLM-optimized project summary

---

## 📄 License

All projects in this organization are licensed under the **MIT License**.

---

<div align="center">

Made with ❤️ by the **bQuery** team

[Website](https://bquery.flausch-code.de/) · [GitHub](https://github.com/bQuery) · [npm](https://www.npmjs.com/package/@bquery/bquery)

</div>
