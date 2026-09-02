# la-enhancer

Performance-patched mirror of [ntoombs19's LA Enhancer](https://ntoombs19.github.io/LA-Enhancer/) userscript
for Tribal Wars' Loot Assistant (`screen=am_farm`), hosted here purely so it can be fetched by URL
(`$.getScript` / Tampermonkey `@require`) from [MartynHorslen/scripts](https://github.com/MartynHorslen/scripts)'
`autoloot.user.js`.

All credit for the original script goes to ntoombs19. Patches on top of the archived original:

- Avoid a full-table jQuery `:visible` scan on every farm keydown (`getNextVisibleRow`).
- Batch AJAX-fetched plunder-list pages into a single DOM insert instead of one per row
  (the per-row `tr:last` requery + insert was O(rows²) and stalled the browser on large lists).

## Usage

```js
window.$.getScript('https://martynhorslen.github.io/la-enhancer/laenhancer.js', function () {
  // ready
});
```

## Updating

This file is copied from `scripts/src/laenhancer.js` in the private `scripts` repo. To publish a
change: copy the updated file here, commit, push to `main` — GitHub Pages redeploys automatically.
