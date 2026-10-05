# Sky

**A minimalist, bilingual knowledge wiki where ideas evolve through community contributions.** Sky is a self-contained static app: no server, build step, or backend required.

**Sky 是一个极简的中英双语知识百科，让知识在分享与修改中持续演进。** 应用是独立静态页面，无需服务器、构建步骤或后端。

## Try it

- **Live site:** https://jianheng71.github.io/Sky_panel/
- Open [`sky_v6_final.html`](./sky_v6_final.html) directly in a modern browser, or visit the live site.
- Switch between Chinese and English with the language button in the header.

## Features

- Search and browse articles, with table of contents and infoboxes.
- Seed and edit articles with headings, `@info` JSON, and typed content blocks.
- Suggest edits without replacing the current article; vote on or copy blocks.
- Export and import the local wiki as JSON.
- Responsive home, article, profile, and admin-console views.

## Local-only data

Sky stores articles, language preference, profiles, and edit suggestions in the current browser's `localStorage`. There is no shared database: changes made by one visitor do not appear for other visitors or browsers. Use JSON export/import to move a wiki between browsers.

The console's first-use password is set separately in each browser. It only gates that browser's local console; it is **not** website authentication or a security boundary. Do not use it to protect shared or sensitive data.

## GitHub Pages

GitHub Actions publishes the static app when changes are pushed to `main` or the production branch. The Pages site serves the single-file app as its home page.
