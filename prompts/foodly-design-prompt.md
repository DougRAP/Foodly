Design and build the first real version of **Foodly** as ONE self-contained HTML file (inline CSS + JS, no build step, no frameworks; Google Fonts allowed). Output the file, nothing else.

## What Foodly is
A mobile-first web app for millennial parents (35–45, full-time job, kids, mental load of "what's for dinner" every week). Promise: **pick the week's dinners in 2 minutes, groceries ordered at the best price.** Price: $7/mo.

## Screens (all in the one file, switch between them with JS)
1. **Landing** (public): what it is, who it's for, 3 benefits, a phone mockup of the picker, pricing, Sign up / Log in buttons. Must work on both phone and desktop.
2. **Log in / Sign up**: email + password, Google button, "Continue with Apple". UI only, no real auth.
3. **Setup** (4 quick steps): who's eating (adults, kids w/ name+age) → loves/avoids (tap chips) → your stores + how you get groceries (Delivery / Pickup / In-store, ranked) → weeknight cook time + weekly budget.
4. **Dinner Picker** (the core): modes Everyday / Holiday / Party. Shows ~6 dinner ideas; tap to add to the week; **More ideas** replaces the ones not picked with fresh ones (never repeat). Family favorites row. Done locks the week. Include a mic button + "read aloud" toggle for hands-free use in the car.
5. **Week**: the picked dinners by day; buttons for **Let the kids vote** (pass-the-phone, big 😍 🙂 🤢 buttons, no reading needed for a 5-year-old) and **Rate** (faces per family member after dinner; 4+ becomes a favorite).
6. **Grocery list**: auto-built from the picked dinners, grouped by store section, each item has a **Have it** check; "Scan fridge & pantry" (📷, simulate) pre-checks items and asks about staples it didn't see; add by voice/text.
7. **Order**: her first-choice store/method first with estimated total, a backup option, this week's sale items, "Clip digital coupons", one button "Send cart to <store>" (stub). Note: she pays in the store app; we fill the cart.

Use fake but realistic data (~20 dinners with emoji or illustrations, ingredients w/ store sections). All state in memory.

## Design brief, non-negotiable
- **Do not fall back on defaults.** No Inter/Roboto/Arial/system-ui, no white or light-gray page, no gray bordered cards, no #000 text, no Tailwind-looking blue buttons, no generic SaaS gradient. If it could be any startup, start over.
- Pick a distinct, named visual direction for this brand (warm, appetizing, a little playful, grown-up, not childish) and commit to it: a real color system (background is a colour, not white), a display font with personality + a readable body font, a consistent radius/shadow/spacing scale, and motion (tap feedback, card enter, sheet transitions).
- Mobile first: 390px wide is the primary target; thumb-reachable primary actions; bottom tab bar in the app; landing responsive up to desktop.
- Food should look delicious: big imagery per dinner (emoji at large scale is fine, or inline SVG illustrations), generous whitespace, one clear primary action per screen.
- Feel like a product from 2026 people would pay $7/mo for, not a wireframe or template.
- Accessible: 4.5:1 contrast on text, 44px tap targets, visible focus.

Before writing code, state in a 5-line comment at the top of the file: direction name, palette (hex), fonts, and the one idea that makes it feel like Foodly.
