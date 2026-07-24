# Findr

> **Shop smarter, not longer.** *( •̀ᴗ•́ )✧*

Findr is a consumer-first mobile application that helps shoppers discover the **true lowest price** for products across multiple e-commerce platforms. Instead of manually opening dozens of tabs, comparing vouchers, and checking whether a discount is actually real, Findr brings everything together into one clean experience.

Built on top of major marketplaces such as **Shopee**, **Lazada**, and **Amazon**, Findr acts as a unified product discovery layer that helps users make better purchasing decisions with confidence.

---

## Overview

Online shopping has become more competitive than ever. Every platform offers its own promotions, vouchers, flash sales, cashback campaigns, and store-specific discounts. While this creates more opportunities to save money, it also makes shopping surprisingly time consuming.

Findr was created to solve this problem.

Rather than asking users to search every marketplace individually, Findr automatically aggregates product listings, calculates the final checkout price after discounts, and presents the most accurate comparison possible.

The goal is simple.

> Spend less time searching, and more time knowing you're getting the best deal.

---

# Features

## True Lowest Price Engine

Most comparison tools simply compare the listed price.

Findr goes a step further.

It automatically factors in:

- Platform vouchers
- Store vouchers
- Promotional coupons
- Stackable discounts
- Final checkout pricing

Instead of showing the advertised price, Findr displays the **actual amount you'll pay**, making price comparisons far more meaningful.

---

## 90-Day Price History

Not every "sale" is actually a sale.

Many retailers temporarily increase prices before applying discounts, making products appear cheaper than they really are.

Findr tracks up to **90 days of historical pricing**, allowing users to see whether a discount is genuine before making a purchase.

This creates greater transparency and helps users avoid misleading promotions.

---

## Visual Product Scanner

Found something interesting in real life?

Simply point your camera at it.

Using visual recognition workflows inspired by tools like Google Lens, Findr can identify products from:

- Physical objects
- Product packaging
- Images
- Screenshots

The app then searches supported marketplaces and immediately returns matching listings for comparison.

No typing required. *(ᵔᴥᵔ)*

---

## Smart Watchlists

Sometimes the best purchase is the one you **don't** make immediately.

Users can save products into organised watchlists and receive notifications when:

- Prices become genuinely attractive
- Stock becomes available
- Limited inventory appears
- Products meet their desired purchase conditions

Instead of checking listings every day, Findr keeps watch for you.

---

## Trending Deals

Findr continuously surfaces products that are currently experiencing exceptional discounts across supported marketplaces.

Rather than scrolling endlessly through thousands of listings, users can quickly browse categories where meaningful savings are happening right now.

Examples include:

- Electronics
- Beauty
- Fashion
- Home & Living
- Pet Care
- Lifestyle products

---

## Market Forecasting

One of Findr's most unique features is **Findr Pro**, a predictive market forecasting system.

By analysing pricing behaviour and marketplace trends, Findr estimates whether product categories are likely to:

- Increase in price
- Drop in price
- Remain relatively stable

over the coming **30 days**.

Instead of wondering *"Should I buy now or wait?"*, users receive helpful insights to make more informed purchasing decisions.

---

# User Experience

Findr focuses on reducing friction throughout the shopping journey.

The application is designed around a clean, minimal interface with dedicated pages for:

- Product scanning
- Recent scans
- Watchlists
- Trending deals
- Market forecasts
- Settings

Everything is organised to keep important information immediately accessible without overwhelming the user.

---

# Technical Approach

Traditional price comparison websites often rely on extensive web scraping.

While functional, these systems can become fragile whenever retailers redesign their websites or modify their page structure.

Findr takes a more modern approach.

Its backend is designed around serverless infrastructure and secure platform integrations, allowing product information to be queried efficiently without depending on brittle scraping pipelines.

This architecture offers several advantages:

- Faster response times
- Better scalability
- Improved reliability
- Easier maintenance
- Stronger security

Serverless workers, such as those provided through platforms like **Vercel**, help deliver a responsive cross-platform shopping experience while remaining lightweight and scalable.

---

# Why Findr?

Shopping today is no longer just about finding the cheapest listing.

It is about understanding:

- What the **real checkout price** will be
- Whether today's discount is actually legitimate
- If prices are likely to fall next week
- Which marketplace currently offers the best value
- Whether it's worth buying now or waiting

Findr brings all of these answers together into a single application.

---

# Future Ideas

As the platform continues to evolve, potential future improvements include:

- Additional marketplace support
- Regional pricing intelligence
- Cashback comparisons
- AI-powered buying recommendations
- Personalised deal discovery
- Cross-device synchronisation
- Browser extension integration

---

# Built With

- Modern mobile application technologies
- Serverless cloud infrastructure
- Visual product recognition workflows
- Historical pricing analytics
- Predictive market forecasting
- Secure marketplace integrations

---

# Screenshots

| Scan | Watchlist |
|------|-----------|
| Scan products instantly using your camera and compare prices across supported marketplaces. | Organise products into watchlists and receive alerts when prices become genuinely worth buying. |

| Trending | Forecast |
|----------|----------|
| Discover products currently experiencing significant discounts. | View category-level market predictions to help decide whether to buy now or wait. |

---

# Philosophy

Findr isn't trying to encourage more shopping.

It's trying to encourage **better shopping**.

By making pricing more transparent, reducing comparison fatigue, and helping users understand market trends, Findr aims to give consumers the information they need to make smarter purchasing decisions.

Less guessing.

Less searching.

Better value. *(˶ᵔ ᵕ ᵔ˶)*

---

---

# Running the Prototype

Open `index.html`. That's it.

Double-click it, drag it into a browser tab, or serve the folder — all three work. React and the three typefaces are vendored into `vendor/`, so the prototype makes **no network requests at all** and renders identically on a plane, on venue wifi, or off a USB stick.

## Responsive behaviour

The prototype adapts to whatever it's opened on:

| Device | Behaviour |
|--------|-----------|
| Desktop / laptop | Phone frame on a dark stage, auto-fitted to the window so it's never clipped on a short screen and fills a large monitor |
| Tablet | Same framed stage — the layout is phone-width by design, so stretching it wide looks wrong |
| Phone | Frame dissolves. The app fills the viewport edge to edge like any responsive site, notch and home-indicator safe areas respected |

Scaling is handled by `--findr-scale` (computed in `<head>`) and the breakpoint lives in the stylesheet inside `<helmet>`. Both are commented — the design size is `390 × 844`.

---

# Finding things

Search tolerates typos. It tries an exact match first — across full product names, individual words, and informal names like "airpods", "xm4" or "dog food" — and only then falls back to fuzzy matching.

The fuzzy pass uses Damerau-Levenshtein distance, which counts a transposition (`sonu` → `sony`) as a single edit rather than two. Adjacent-key slips are the most common typo on a touch keyboard, so that distinction matters more than it sounds. Tolerance scales with word length: one edit on a short word, up to three on a long one, so `sonu` finds Sony but `sock` doesn't.

When the best candidate is close but not certain, Findr offers it — **Did you mean Sony WH-1000XM4?** — rather than guessing silently or claiming nothing was found.

| Typed | Result |
|-------|--------|
| `soony`, `sonu` | suggests Sony WH-1000XM4 |
| `nintedo` | suggests Nintendo Switch OLED |
| `airpo`, `lulu`, `skii` | opens the product directly |
| `qwertyuiop` | no match |

---

# Guided tour

**Settings → Show me around** walks through all seventeen features: what the scanner is for, how vouchers stack, how to spot a fake sale, what the forecast graphs mean, and where the accessibility controls live.

The dark ground is drawn as a very large box-shadow spreading outward from the highlighted rectangle, which leaves a real hole rather than a lighter patch — whatever is being described stays at full contrast underneath. Steps that describe a whole screen dim everything and centre the card instead.

The engine switches screen, opens whatever needs opening (the forecast charts only exist inside an expanded category), scrolls the anchor into view, measures it in the frame's own coordinate space, and draws around it. Measurement accounts for the desktop frame's `transform: scale()`, so the hole lands correctly on a large monitor as well as a phone. The card takes whichever side of the hole has more room and caps its height to that space.

The tour temporarily unlocks Pro so the forecast graphs can be explained, and restores the previous tier when it ends.

---

# Accessibility

Findr keeps its normal look by default. **Settings → Vision & readability** holds a single master switch, and everything else lives behind it.

## Accessibility mode

**Off** — the default. PaperDesign exactly as authored: the warm cream ground, the soft greys, the original accent hues, and the compact layout. Nothing is compromised to accommodate a mode nobody has asked for.

**On** — every foreground colour deepens until it is comfortably readable, and the app moves to the comfortable layout for more breathing room. Density remains overridable under Appearance; the mode sets it, it doesn't lock it.

## Contrast

Three levels, available once the mode is on:

| Level | Ground | Worst contrast anywhere |
|-------|--------|------------------------|
| **Paper** | Cream, grid intact | 4.79:1 |
| **High** | White, hairlines become edges | 6.15:1 |
| **Higher** | Pure white, no tinted surfaces, accents near-black | 9.90:1 |

Paper is the tier most people who need help will live in: it still looks like Findr, it just stops being faint. High and Higher trade the paper away for progressively more separation, ending at a ground with no tint anywhere and accents dark enough to read as mass rather than hue.

## Text size

Five steps from 100% to 175%. The slider is paired with large **A** / **A** steppers on either side, because a slider alone is hard work with a tremor or arthritis — both drive the same setting, and the slider is fully keyboard operable. A live preview built from a real product row shows the effect before you leave the screen.

Every size in the app is `calc(Npx * var(--ts))`, so nothing is left behind when text grows. Fixed-height rows became minimum heights so they expand instead of clipping, and the bottom navigation scales more gently and wraps rather than crushing five labels into 390px.

## Colour-blind friendly

Findr signals price drops in green and rises in red, which is the exact pair red–green colour blindness collapses — roughly 1 in 12 men. This moves the semantic pair to blue and orange, distinct under deuteranopia, protanopia and tritanopia. The ↓ / ↑ arrows and the wording already carry the meaning without colour at all.

## Colour

Four accents — Moss, Slate, Plum, Clay — labelled by name rather than shown as a bare swatch, since a swatch is no use if you can't tell swatches apart. Each has a value per contrast tier, darkening as the ground lightens.

## Verification

Every text node on every screen is measured programmatically against **WCAG 2.1 AA** (4.5:1 body, 3:1 large text), compositing translucent backgrounds properly, across all seven accessibility configurations and at every text size. All pass. Interactive targets meet the 44px minimum and keyboard focus is visible throughout.

Tier 0 is deliberately exempt: as authored, PaperDesign's muted grey sits at 2.6:1. That is the design, and it is what the master switch exists to change.

---

## License

This project is licensed under the repository's chosen license.

Please refer to the `LICENSE` file for more information.
