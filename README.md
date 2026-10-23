# Wongfengchen Developer Blog

A static personal blog based on the [official Astro Blog starter](https://astro.build/themes/details/blog/). It brings writing, projects, and contact information together in one place.

## Run locally

```sh
npm install
npm run dev
```

Run `npm run build` to create a production build in `dist/`.

## Add articles and projects

The **Editor** link in the footer opens `/admin/index.html`. The editor has separate **Articles** and **Projects** collections. Choose **New Article** or **New Project**, fill in the fields, and save.

For local editing, keep two terminals running from the project directory:

```sh
npm run dev
npm run cms
```

Then open `http://localhost:4321/admin/index.html`. The local CMS writes content files to this Git repository. Changes appear on the site when Astro refreshes. Commit the new files when you are ready to publish.

On a deployed site, the editor requires a GitHub repository and an OAuth authentication provider. Before deploying, update `backend.repo` in `public/admin/config.yml` to the actual `owner/repository`, and configure a GitHub OAuth provider for Decap CMS. Only GitHub accounts with write access can publish. Until that connection is configured, use the local editor.

Articles are stored in `src/content/blog/`; projects are stored in `src/content/projects/`.
The project list also includes three credited links to Sebastian Lague's itch.io work as examples of featured projects.
The Digital Logic Sim and Hydraulic Erosion screenshots come from their respective [itch.io project pages](https://sebastian.itch.io/).

## Add images

In the editor, open an article and use **Cover image** to upload an image for the top of the article. To place images inside the article, use the image button in the **Article** Markdown editor. For a project, use **Project image**. All uploads are stored in `public/uploads/` and served from `/uploads/`.

If you edit files manually, put an image in `public/uploads/` and use `coverImage: /uploads/file.jpg` in an article, `image: /uploads/file.jpg` in a project, or `![Description](/uploads/file.jpg)` in article Markdown.

## Publish an article manually

Add a Markdown file to `src/content/blog/`. Its filename becomes the post URL.

```md
---
title: 'Your post title'
description: 'A short summary'
pubDate: 2026-10-23
---

Write your article here.
```

Commit and push the file to trigger a deployment on your connected hosting service. This project does not include a web editor.

## Update contact details

- Name, email, and GitHub: Edit `src/consts.ts`.

## Deploy

Connect this repository to Vercel. Astro should be detected automatically. Use `npm run build` as the build command and `dist` as the output directory. Set the `SITE_URL` environment variable to your actual deployed URL, such as `https://your-domain.vercel.app`. It is used for canonical URLs, RSS, and the sitemap.

For GitHub Pages, build the static site with `npm run build` in a GitHub Actions workflow. A user site (`username.github.io`) or a custom domain is recommended for root-path deployment. Publishing under a repository subpath also requires updating Astro's `base` option and the site's internal links.

## Template credit

Based on the official Astro Blog starter, with a redesigned interface and new content.
