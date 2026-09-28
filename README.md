# signalnoiseandbeyond.com

The main site. Landing page plus three sections. Tools live in a separate
`minions` repo.

```
/                  landing page (self-contained, own styles)
/patterns/         data science portfolio
/grain/            photography
/musings/          blog (stub)
/assets/css/       shared styles for the section pages
CNAME              signalnoiseandbeyond.com
.nojekyll          skip Jekyll — delete this if you adopt Jekyll for the blog
```

## One-time setup

**1. Name the repo correctly.** It must be `<your-github-username>.github.io`,
exactly. That's what makes GitHub serve it at the root of the domain instead
of a subpath. Push everything in this folder to its root.

**2. Turn on Pages.** Settings → Pages → Source: *Deploy from a branch* →
`main` / `(root)`.

**3. Add the domain before touching DNS.** Settings → Pages → Custom domain →
`signalnoiseandbeyond.com` → Save. Do this first. If you configure DNS while
the domain is unclaimed on GitHub's side, someone else can take a subdomain
on it.

**4. Add DNS records at your registrar.**

| Type | Name | Value |
|---|---|---|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| AAAA | @ | 2606:50c0:8000::153 |
| AAAA | @ | 2606:50c0:8001::153 |
| AAAA | @ | 2606:50c0:8002::153 |
| AAAA | @ | 2606:50c0:8003::153 |
| CNAME | www | `<your-username>.github.io` |

Propagation can take up to 24 hours, usually much less.

**5. Tick "Enforce HTTPS"** once the certificate provisions. The checkbox stays
greyed out until DNS resolves, so come back to it.

## Editing

**Projects** — `patterns/index.html`. Copy one `<li>` block per project. The
shape is deliberate: title, what the problem was, what you built, what
changed. The outcome line gets the yellow rule.

**Photos** — put files in `grain/photos/` and add a `<figure>` per photo.
There's a commented example in the file. Resize the long edge to ~2000px
first; Pages caps a repo around 1 GB and single files at 100 MB. If the
gallery outgrows that, move the images to Cloudflare R2 or Backblaze B2 and
point the `src` at those URLs.

**Blog** — currently a stub with an empty state. Two routes when you're ready,
both described in a comment inside `musings/index.html`.

## Design notes

The landing page carries its own styles inline. It's the only page with the
sky gradient, and keeping it self-contained means it renders instantly with no
stylesheet round-trip.

Everything else shares `assets/css/site.css`. Palette is periwinkle `#C6CCEE`,
blush `#F4DCE0`, butter `#F2C96B`, indigo ink `#332E52`, cool paper `#F8F7FC`.
Type is Gabarito for display, Karla for body.

The only animation is the landing page smiley — it rises in, the smile draws
itself, and it blinks roughly every seven seconds. All of it is disabled under
`prefers-reduced-motion`.
