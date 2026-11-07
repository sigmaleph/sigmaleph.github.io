# sigmaleph blog (Hugo)

## Everyday commands (run inside this folder)

- `hugo server`: live preview at http://localhost:1313, refreshes as you edit.
- `hugo server -D`: same, but also shows posts marked `draft: true`.
- `hugo new content posts/my-post-title.md`: start a new post (it begins as a draft).
- `hugo`: build the real site into `public/`. That folder is what gets uploaded to a host.

## Where things live

- `hugo.toml`: site title, author, menu links, final web address (`baseURL`).
- `content/posts/`: one Markdown file per post.
- `content/about.md`, `content/_index.md`: the About page and the front-page intro.
- `layouts/`: the HTML templates (page skeleton, post page, list pages).
- `static/css/style.css`: the look. Anything in `static/` is copied as-is to the site.
- `archetypes/default.md`: the template used by `hugo new`.
