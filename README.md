# 🧺 Green Basket Mart

A single-page online grocery store built with plain **HTML, CSS and JavaScript**, styled with **Tailwind CSS** and animated with **GSAP**. No build step, no dependencies to install: open the file and it runs.

## Features

- **Animated hero:** the headline slides up line by line, then the buttons and floating produce emojis pop in. The emojis keep drifting and shift slightly with your cursor.
- **Product catalog:** 16 products across four aisles (Fruit, Vegetables, Dairy, Pantry).
- **Filter and search:** switch aisles or search by name. The grid re-animates each time the list changes.
- **Add-to-cart animation:** the product emoji flies into the cart button, the button bounces, and a toast confirms the add.
- **Cart drawer:** slides in from the right, with quantity controls, subtotal, delivery fee and total.
- **Delivery rule:** free delivery on orders of ₹499 or more, otherwise ₹40.
- **Place order:** clears the cart and shows a confirmation (no real payment).
- **Light and dark theme:** follows your system setting, with a manual toggle in the header.
- **Responsive and accessible:** works from phones to desktops, has visible keyboard focus, and turns off motion for people who prefer reduced motion.

## Tech stack

| Purpose | Tool |
| --- | --- |
| Structure | HTML5 |
| Styling | Tailwind CSS 3.4.17 (Play CDN) plus a small custom CSS block |
| Animation | GSAP 3.12.5 (cdnjs) |
| Logic | Vanilla JavaScript |
| Fonts | Bricolage Grotesque and DM Sans (Google Fonts) |

## Getting started

1. Save the code as `index.html`.
2. Open it in any modern browser (double-click, or serve it with any static server).
3. You need an internet connection the first time, because Tailwind, GSAP and the fonts load from CDNs.

To serve it locally:

```bash
# Python
python3 -m http.server 8000

# or Node
npx serve .
```

Then visit `http://localhost:8000`. for python
`http://localhost:3000` for Node

## Project structure

```
.
├── index.html   # markup, styles and scripts in one file
└── README.md
```

If you prefer separate files, move the `<style>` block into `style.css` and the last `<script>` block into `script.js`, then link them from `index.html`.

## Customizing

### Add or edit products

Products live in the `P` array in the script:

```js
{ id: 17, n: 'Green tea', e: '🍵', p: 150, u: '100 g', c: 'Pantry' }
```

| Key | Meaning |
| --- | --- |
| `id` | Unique number |
| `n` | Product name |
| `e` | Emoji shown as the product image |
| `p` | Price |
| `u` | Unit or pack size |
| `c` | Category (must match an entry in the `cats` array) |

### Add a new aisle

Add the name to the `cats` array, then use it as the `c` value on your products.

### Change colors

Edit the CSS variables at the top of the `<style>` block. Light values are in `:root`, dark values are in the two dark-theme rules:

```css
:root { --paper: #fff8e8; --ink: #1c2a1f; --leaf: #1f6b42; --tomato: #e8452c; --butter: #ffd75e; }
```

### Change currency or delivery rules

- Currency symbol: the `money()` function.
- Free-delivery threshold and fee: the `sub>=499` check and the `40` value inside `drawCart()`.

### Use real product photos

Replace the emoji inside the `.em` span in `render()` with an `<img>` tag pointing to your own image files.

## Known limitations

- The cart is kept in memory only, so refreshing the page empties it.
- "Place order" is a demo and does not take payment or send data anywhere.
- Tailwind's Play CDN is meant for prototypes. For production, install Tailwind with its CLI and compile your CSS.

## Ideas for next steps

- Save the cart with `localStorage`
- Product detail pop-ups and a wishlist
- A checkout form with address and delivery slot
- Scroll-triggered animations using GSAP ScrollTrigger
- A backend or API for real products and orders

## License

Free to use and modify for personal and commercial projects.
