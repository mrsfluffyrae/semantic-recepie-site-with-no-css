# Simple Plate: Semantic Recipe Site

A hand-written HTML5 site with no CSS framework and no JavaScript.
`style.css` is only for legibility (font, spacing, focus outlines, table borders).

## Pages

| File | Purpose |
|------|---------|
| `index.html` | Homepage: intro section plus an `article` card for each recipe |
| `recipes/pancakes.html` | Recipe page |
| `recipes/tomato-pasta.html` | Recipe page |
| `recipes/spiced-chicken-stew.html` | Recipe page with 21 ingredients and a very long title |
| `contact.html` | Accessible contact form |
| `style.css` | Small legibility stylesheet |
| `images/` | Simple SVG illustrations |

Open `index.html` in a browser; no server is needed.

## How the requirements are met

- **Semantic elements:** every page uses `header`, `nav`, `main`, `section`, `footer`, and recipes and homepage cards use `article`.
- **Headings:** one `h1` per page. Recipe pages go `h1` > `h2` (Ingredients, Method, Nutrition). The homepage goes `h1` > `h2` > `h3`. The site name in the header is a `p`, not a heading, so there is never a second `h1`.
- **Lists:** ingredients use `ul`, method steps use `ol`.
- **Form:** every control has a `label` linked by `for`/`id`. Types used: `text`, `email`, `radio`, `select`, `textarea`. Fields are grouped with `fieldset`/`legend`, including the radio group. The email hint is linked with `aria-describedby`.
- **Images and table:** every `img` has descriptive `alt` text. Each recipe has a nutrition table with a `caption`, `thead`, and `th scope="col"` / `th scope="row"`.
- **Navigation:** identical on every page, with `aria-current="page"` on the current link. A "Skip to main content" link appears when you press Tab.
- **Stretch goal:** recipe pages carry schema.org `Recipe` microdata (name, image, times, yield, ingredients, instructions).

## Edge cases

| Edge case | How it degrades gracefully |
|-----------|----------------------------|
| Many ingredients | Stew page has 21 ingredients; the list flows into columns (`columns: 16rem`) and becomes one column on narrow screens |
| Long title in navigation | The nav is a flex list with `flex-wrap`, so the long stew title wraps onto its own line instead of overflowing |
| Form submitted empty | `required` attributes make the browser stop the submit and name the missing field; no JavaScript is needed |

## Keyboard test

Tab order on the contact form: skip link, navigation links, name, email, reason (arrow keys move between radios), recipe select, message, Send button. Focus is shown with a thick orange outline.

## Validation

All five pages were checked with the W3C Nu HTML Checker (`vnu.jar`) and returned no errors or warnings:

```
java -jar vnu.jar --skip-non-html index.html contact.html recipes/*.html
```

You can also check each page by uploading it at https://validator.w3.org/#validate_by_upload.

## Notes

The form uses `action="mailto:..."` so it works without a server. In a real site, replace it with the URL of a form-handling script and keep the `required` attributes (and also validate on the server).
