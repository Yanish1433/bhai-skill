# Design direction: avoiding the AI look

bhai's design stance: every visual decision should be **chosen**, not defaulted. AI-generated design looks generic because models fall back to the most common patterns in their training data. The fix is making real decisions before anything gets built.

## The AI tells to avoid (and what to do instead)

| Tell | Why it reads as AI | Do instead |
|---|---|---|
| Inter (or Roboto, Geist, system font) as the only font | It's the default in templates and tutorials, so it signals nobody chose a font | Pick a display font with character and pair it with a readable body font |
| Purple/indigo-to-blue gradients, gradient headline text | The single most recognised AI default | A palette of 4–6 named colors with clear roles; solid colors; at most one purposeful gradient |
| Centered hero + headline + button, then three equal feature cards with icons | Could belong to any product | A layout driven by the product's content: show the real product, use asymmetry, vary section rhythm |
| Bento grids used just because they're trendy | Overused filler | Use a grid only when the content really is a set of comparable items |
| Same rounded corners and soft shadow on everything, cards inside cards | Flat, noisy hierarchy | A deliberate radius and elevation system; fewer containers |
| Colored left border on cards, pill "eyebrow" labels above every heading | Recognised AI fingerprints | Use hierarchy from type size, weight and spacing |
| Grey low-contrast body text | Looks soft, hurts readability | Body text that meets WCAG AA contrast |
| Glassmorphism, neon glow, blob backgrounds | Decoration with no meaning | Texture or imagery that relates to the product |
| Vague copy ("Empower your business", "Unlock your potential") | Generic copy is one of the strongest AI signals | Specific, concrete words about what the product does for whom |
| The "second wave": cream background + terracotta accent, or near-black + one acid-green highlight | What AI produces when told to "look less AI" | Derive colors from the product's own world, audience and brand |
| Stock photos, fake "John Doe / Acme" placeholders | Instantly fake | Real product screenshots, real (or plausibly realistic, labeled) sample data |

## How to write the design direction section

Give concrete choices, each with a one-line reason:

1. **Concept:** 2–3 words for the feeling (e.g. "workshop, tactile, confident"), tied to the users and product, not to trends.
2. **Typography:** a display font and a body font by real name (Google Fonts, Fontshare, or similar free sources unless the user has a budget), plus a basic size scale. Avoid repeating the same pairing across different ideas.
3. **Color:** 4–6 named colors with hex values and roles (background, surface, text, primary action, accent, feedback). Check text contrast.
4. **Layout:** the shape of the key screens. What's the hero (ideally the real product in action)? How do sections vary in rhythm?
5. **3D and motion:** see below.
6. **References:** 2–4 real sites or products worth studying, and what specifically to learn from each.
7. **Avoid list:** the tells above that this product is most at risk of.

## 3D and motion

The user likes animated 3D design. bhai supports it, with one rule: **3D where it adds value, with a lighter fallback.** Heavy 3D can be slow on phones and weak connections, so:

- Use 3D for one or two strong moments (a hero object, a product visual, an interactive explainer), not on every section.
- Tools to suggest, with trade-offs: **Three.js / React Three Fiber** (full control, code-heavy), **Spline** (fast to design visually, heavier exports), **GSAP** (scroll and timeline animation), CSS transforms for small touches.
- Always plan: lazy-load 3D scenes, show a static image or video poster first, simplify or swap to an image on small screens, and respect `prefers-reduced-motion`.
- Motion should explain or reward (show how something works, confirm an action), not just decorate.

## Design audit (existing products)

Go through the tells table above against the real product. For each problem found, name the exact screen or component and give the specific fix.
