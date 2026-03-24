# bQuery

<p align="center">
  <strong>Type-safe querying and reusable UI for modern data-driven applications.</strong>
</p>

<p align="center">
  bQuery combines a query-focused core with a modern UI layer to help teams
  build structured, maintainable, and polished software faster.
</p>

<p align="center">
  <a href="https://github.com/bQuery/bQuery">
    <img
      src="https://img.shields.io/badge/Core-bQuery-111827?style=for-the-badge"
      alt="bQuery Core"
    >
  </a>
  <a href="https://github.com/bQuery/ui">
    <img
      src="https://img.shields.io/badge/UI-bQuery%20UI-2563eb?style=for-the-badge"
      alt="bQuery UI"
    >
  </a>
  <a href="https://bquery.flausch-code.de/">
    <img
      src="https://img.shields.io/badge/Docs-Live-16a34a?style=for-the-badge"
      alt="Documentation"
    >
  </a>
  <a href="https://bquery.github.io/ui/">
    <img
      src="https://img.shields.io/badge/UI%20Preview-Storybook-f43f5e?style=for-the-badge"
      alt="UI Preview"
    >
  </a>
</p>

<p align="center">
  <a href="https://github.com/bQuery/bQuery/stargazers">
    <img
      src="https://img.shields.io/github/stars/bQuery/bQuery?style=flat-square"
      alt="bQuery stars"
    >
  </a>
  <a href="https://github.com/bQuery/ui/stargazers">
    <img
      src="https://img.shields.io/github/stars/bQuery/ui?style=flat-square"
      alt="ui stars"
    >
  </a>
  <a href="https://github.com/bQuery/bQuery/issues">
    <img
      src="https://img.shields.io/github/issues/bQuery/bQuery?style=flat-square"
      alt="core issues"
    >
  </a>
  <a href="https://github.com/bQuery/ui/issues">
    <img
      src="https://img.shields.io/github/issues/bQuery/ui?style=flat-square"
      alt="ui issues"
    >
  </a>
  <a href="https://github.com/bQuery/bQuery/blob/main/LICENSE">
    <img
      src="https://img.shields.io/github/license/bQuery/bQuery?style=flat-square"
      alt="license"
    >
  </a>
</p>

---

## About

bQuery is an open-source ecosystem for building data-centric applications with a
focus on clear query workflows, reusable UI patterns, and a modern developer
experience.

The organization currently centers around two core projects:

- [`bQuery`](https://github.com/bQuery/bQuery) — the query-focused core
- [`ui`](https://github.com/bQuery/ui) — reusable UI components and interface
  tooling

Together, they provide a strong foundation for internal tools, dashboards,
admin panels, analytics interfaces, and other data-heavy applications.

---

## Projects

### `bQuery`
The core project of the ecosystem.

It is designed to support structured, maintainable, and developer-friendly data
workflows.

- Repository: https://github.com/bQuery/bQuery
- Documentation: https://bquery.flausch-code.de/

### `ui`
A reusable UI layer for building consistent and polished frontends around
data-driven workflows.

- Repository: https://github.com/bQuery/ui
- UI Preview: https://bquery.github.io/ui/

---

## Why bQuery?

bQuery aims to make complex data-oriented software easier to build and maintain.

### Clear structure
Organize querying logic in a way that stays understandable as projects grow.

### Reusable building blocks
Use consistent UI components and patterns instead of rebuilding the same pieces
again and again.

### Better developer experience
Work with APIs and tooling designed to be ergonomic, practical, and easy to
integrate.

### Built for real applications
Especially useful for projects with tables, filters, forms, search, data
management, and operational workflows.

---

## Example

Illustrative example of the ecosystem in action:

```ts
import { query } from "bquery";

const users = query("users")
  .select(["id", "name", "email"])
  .where("active", "=", true)
  .orderBy("name", "asc");
```

```tsx
import { DataTable, FilterBar, SearchInput } from "@bquery/ui";

export function UsersPage() {
  return (
    <>
      <SearchInput placeholder="Search users..." />
      <FilterBar />
      <DataTable />
    </>
  );
}
```

> These snippets are illustrative and intended for the organization profile.
> Refer to the individual repositories for exact APIs, installation details, and
> production usage.

---

## Use Cases

bQuery is a good fit for:

- admin dashboards
- internal tools
- analytics frontends
- CRUD-heavy applications
- data explorers
- developer tooling
- back-office and operations platforms

---

## Get Started

### Explore the core
- GitHub: https://github.com/bQuery/bQuery
- Docs: https://bquery.flausch-code.de/

### Explore the UI library
- GitHub: https://github.com/bQuery/ui
- Preview: https://bquery.github.io/ui/

---

## Contributing

Contributions are welcome across the ecosystem.

You can help by:

- reporting bugs
- proposing features
- improving documentation
- submitting pull requests
- sharing feedback on APIs, UX, and DX

For project-specific discussions, please use the corresponding repository:

- https://github.com/bQuery/bQuery
- https://github.com/bQuery/ui

---

## Quick Links

- Core repository: https://github.com/bQuery/bQuery
- UI repository: https://github.com/bQuery/ui
- Documentation: https://bquery.flausch-code.de/
- UI preview: https://bquery.github.io/ui/

---

<p align="center">
  <a href="https://github.com/bQuery/bQuery">Explore Core</a>
  ·
  <a href="https://github.com/bQuery/ui">Explore UI</a>
  ·
  <a href="https://bquery.flausch-code.de/">Read Docs</a>
  ·
  <a href="https://bquery.github.io/ui/">View UI Preview</a>
</p>
