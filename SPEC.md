# Foodly — v1 Spec

**Problem:** A busy parent spends too much mental energy every week deciding dinners, building a grocery list, and shopping at a good price.
**Promise:** Pick the week's dinners in 2 minutes, and have the groceries ordered at the best price.
**User:** Millennial parents running a household (e.g. a 38-year-old with a full-time job, a 5-year-old, a 16-year-old, and a partner who doesn't plan).
**Price:** $6–8/mo, pitched as "saves time + $20/week."

## Principles
- Simple. Tapping, not typing. No forms after setup.
- Learns the family over time. Starts random and becomes tailored.
- Phone-first web app (PWA, installable to the home screen).

## 1. Setup (one time, ~2 min, editable later)
- Household: number of adults and kids, and ages.
- Likes, dislikes, allergies, diet (quick chips + optional free text).
- Weeknight cook time (15 / 30 / 45+ min) and weekly budget.
- **Shopping preferences:** stores she uses, and order method ranked by preference (delivery / pickup / in-store). Her first choice is shown first, with a backup option.

## 2. Dinner Picker (the core loop)
- **Mode:** Everyday · Holiday · Party (party asks for guest count). Each mode produces different kinds of suggestions.
- The app shows ~6 dinner cards (name, photo/emoji, time, rough cost).
- She taps a card to **add it to the week**. **More ideas** generates a fresh batch, excluding meals already picked or already shown.
- Repeat until she has as many as she wants (usually 5–6). **Done** locks the week.
- **Favorites tab:** she can pick from past top-rated meals.
- **Learning:**
  - The first week's suggestions are varied and random-ish, based on her setup answers.
  - After dinner (next morning prompt), she gives each meal 1–5 stars.
  - Suggestions shift toward what the family rates highly. "More ideas" keeps offering *new* meals in that style rather than repeats.

## 3. Grocery List
- Built automatically from the locked meals, with ingredients merged and quantities summed.
- Sorted by store section.
- Each item has a **"Have it"** checkbox. Checked items are dropped from the order.
- Optional **pantry photo**: she snaps the fridge/pantry, and the app pre-checks items it sees and asks about staples it doesn't ("Didn't see eggs — out?").
- She can add extra items ("milk, paper towels").

## 4. Ordering at the Best Price
- The app shows her preferred store/method first with an estimated total, plus a backup option.
- **Order online:** one tap sends the cart to the store. She reviews and pays in the store's app; we can't take payment on her behalf (store API limit).
  - Instacart API: creates a ready cart at her chosen store (many chains).
  - Kroger-family API: real prices + sale prices, adds items to her Kroger cart.
  - Walmart: cart link.
- **In-store:** shopping list by aisle, with this week's sale items flagged and a link to the store's digital coupons.
- Meal suggestions are nudged toward items on sale where price data exists (Kroger v1).

## 5. Bonuses: hands-free + kids
- **Hands-free:** voice commands ("add tacos", "more ideas", "done"), and replies read aloud so it works while driving.
- **Kids join in:** pass-the-phone voting (😍 🙂 🤢, no reading needed for little ones), a vote link texted to teens, and everyone rates dinner with faces.

## Out of scope (v1)
Chores/family delegation, calendar, SMS, cross-store coupon apps (Ibotta etc. — no open API), fully automatic checkout.

## Tech
Next.js (TypeScript) PWA · Postgres (Prisma) · Claude API (meal generation, pantry photo vision) · Instacart Developer Platform · Kroger API · Stripe · hosted on Netlify. Repo: github.com/DougRAP/Foodly.
Step 0: clickable wireframe in `prototype/` to pick the dinner-picker style before building.

## Build Steps
1. Scaffold app + Setup screen
2. Dinner Picker (modes, pick, More ideas, Done)
3. Ratings + Favorites + learning
4. Grocery list with "Have it"
5. Pantry photo pre-check
6. Ordering: Instacart → Kroger prices/sales/cart → Walmart link → in-store list
7. Accounts + Stripe subscription
8. PWA polish, test with your daughter
