# Sky

**A minimalist, bilingual knowledge wiki where ideas evolve through community contributions.** Sky is a static frontend backed by Supabase for shared articles, edit proposals, and administrator authentication.

**Sky 是一个极简的中英双语知识百科，让知识在分享与修改中持续演进。** 前端部署在 GitHub Pages，文章、修改建议和管理员身份验证由 Supabase 提供。

## Try it

- **Live site:** https://jianheng71.github.io/Sky_panel/
- Visit the live site; shared content requires the configured Supabase project.
- Switch between Chinese and English with the language button in the header.
- Open the **后台入口 / Admin** button in the top-right, or go directly to https://jianheng71.github.io/Sky_panel/#admin.

## Features

- Search and browse articles, with table of contents and infoboxes.
- Seed and edit articles with headings, `@info` JSON, and typed content blocks.
- Suggest edits without replacing the current article; vote on or copy blocks.
- Export and import the shared wiki as JSON.
- Responsive home, article, profile, and admin-console views.
- The supplied Sky artwork, cropped to a transparent PNG, plus light and dark transparent logo variants.

## Shared database and administrator setup

The Supabase project URL and publishable key are configured in the static frontend. A publishable key is designed to be public; database row-level security, not the key, protects writes. Never place a Supabase secret/service-role key in this repository or frontend.

1. In the Supabase SQL Editor, run [`supabase/setup.sql`](./supabase/setup.sql).
2. In Supabase **Authentication → Users**, create and confirm the administrator email/password account.
3. Copy that user's UUID. In the SQL Editor, authorize only that account:

   ```sql
   insert into public.sky_admins (user_id)
   values ('PASTE_AUTH_USER_UUID_HERE');
   ```

4. Open the **后台入口 / Admin** button or https://jianheng71.github.io/Sky_panel/#admin and sign in with the Supabase account.

Articles, votes, and edit suggestions are stored in Supabase and shared with all visitors. Public visitors can read articles, submit edit suggestions, and vote; only UUIDs listed in `sky_admins` can publish, import, or delete articles. Language preference and the Supabase login session remain browser-local. The JSON importer upserts into the shared database; it does not remove rows absent from the imported file. The admin console also has a one-click option to migrate `sky_wiki_db` articles from this browser's earlier local-only version.

## GitHub Pages

GitHub Actions publishes the static app when changes are pushed to `main` or the production branch. The Pages site serves the single-file app as its home page.
