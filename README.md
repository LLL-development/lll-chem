# Chem Balancer

A mobile-friendly game that teaches balancing chemical equations. Adjust the
coefficients until both sides have equal atoms — with live atom-count feedback,
levels of increasing difficulty, and the reaction type revealed for each one.

**Live:** https://lll-chem.pages.dev/  (after first deploy)

## How to play

- Use the − / + buttons to set the coefficient in front of each formula.
- Watch the atom-count chips: each turns green with a ✓ when both sides match.
- Tap **Check** to score it. The simplest whole-number ratio scores highest.
- Stuck? **Reveal** shows the balanced answer (no points, resets streak).

## Structure

```
lll-chem/
├── index.html          the game
├── shared/             brand + i18n (same system as the tools hub)
│   ├── brand.css
│   ├── i18n.js
│   ├── logo.svg
│   └── favicon.svg
└── .github/workflows/deploy.yml
```

## Languages

UI in Japanese (default), English, Simplified/Traditional Chinese, Korean, Malay.
Chemical formulas are language-neutral; reaction-type labels are translated.

## Next ideas

- More equations + a lives/timed challenge mode.
- Element info / "why balancing matters" learn cards.
- Sibling games (guess the correlation, guess the language) could join as a
  learning-games hub, reusing this shared/ setup.
