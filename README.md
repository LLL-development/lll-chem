# Chem Balancer

A mobile-friendly game that teaches balancing chemical equations. Adjust the coefficients
until both sides have equal atoms — with live atom-count feedback, hints, and an
explanation of what each reaction really does.

**Live:** https://lll-chem.pages.dev/

## Features

- **Live atom counting** — every element shows `left / right` and turns green when balanced
- **Hint system** — reveals which element to balance first, at a small score cost
- **Answer explanation** — the balanced equation, the reaction type, and the solving strategy
- **States of matter** — every species labelled `(s)`, `(l)`, `(g)`, or `(aq)`
- **Real-world context** — each reaction explained in plain language ("this is what happens when you light a gas stove")
- **Conservation of mass** — molar masses on each side shown to be equal, proving the law numerically
- **Daily challenge** — one equation per day, the same for everyone, no server required
- **Achievements** — first balance, 5-streak, no-hint level, level cleared, daily done
- **Lives & scoring** — three lives per level; the simplest whole-number ratio scores highest
- **Periodic table strip** — tap an element for its name, atomic number, and the game compounds it appears in
- **Learning sections** — how to play, why balancing matters, and a reaction-type glossary
- **Dark mode** — follows the device setting, remembered across visits
- **Six languages** — Japanese (default), English, Simplified/Traditional Chinese, Korean, Malay

## How to play

1. Look at the atom counts below the equation — each shows `left / right`.
2. Use the − and + buttons to set the coefficient in front of each formula.
3. When every count matches (all green ✓), press **Check**. The simplest ratio scores highest.
4. Stuck? **Hint** names the element to balance first. **Reveal** shows the answer.

## Running locally

No build step and no dependencies — it is plain HTML, CSS, and JavaScript.

```bash
npx serve .
```

Then open the printed `localhost` URL. A static server is required because the page
loads shared files from `shared/`; opening `index.html` directly over `file://` will not work.

## Architecture

```
lll-chem/
├── index.html                  the game — markup, styles, level data, and logic
├── shared/                     shared with the other LLL tools
│   ├── brand.css               palette, dark theme, common UI
│   ├── i18n.js                 language list, translations, switcher
│   ├── theme.js                light/dark theme engine
│   ├── logo.svg
│   └── favicon.svg
└── .github/workflows/deploy.yml  deploys to Cloudflare Pages on merge to main
```

## Adding an equation

Each entry in `LEVELS` holds the species on both sides, the balanced answer, the
reaction type, and the element to balance first:

```js
{
  L: [{ f: "CH₄", a: { C:1, H:4 }, s: "g", m: 16.043 }, ...],
  R: [{ f: "CO₂", a: { C:1, O:2 }, s: "g", m: 44.009 }, ...],
  ans: [1, 2, 1, 2],     // balanced coefficients
  rxn: "combustion",     // reaction type (translated)
  first: "C",            // element the hint points to
  id: "methane"          // key into the real-world description table
}
```

`a` is the atom count per formula, `s` the state of matter, and `m` the molar mass.
Hints and explanations are generated from translated templates, so a new equation
needs one entry — not one sentence per language.

## Data

Molar masses are derived from IUPAC standard atomic weights. Every equation in the
bank has been verified to balance by atom count and to conserve mass.

## License

MIT
