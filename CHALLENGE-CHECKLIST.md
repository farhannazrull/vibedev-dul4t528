# Challenge Quality Checklist

## 1. Accessibility (critical — judge rubrik selalu ada ini)

Semua `<input>` harus punya `<label for="id">` eksplisit (jangan cuma placeholder).
- [ ] `label for` cocok dengan `id` input
- [ ] `aria-label` atau `aria-labelledby` di button/icon-only controls
- [ ] `aria-describedby` menghubungkan input ke error/status message
- [ ] `role="alert"` di error message live region
- [ ] `role="status"` di status output
- [ ] `role="radiogroup"` di radio group, dibungkus `<fieldset>` + `<legend>`
- [ ] `role="img"` + `aria-label` di visualizations (chart, bar, dll)
- [ ] Setiap section punya heading (`h1-h3`) + `aria-labelledby`
- [ ] `focus-visible` style jelas (bukan cuma `outline: none`)
- [ ] Semantic HTML: `<header>`, `<main>`, `<section>`, `<form>` — jangan cuma `<div>` semua

## 2. Validation & Error Handling (critical — jangan silent return)

- [ ] Validation function **terpisah** dari render/event handler
- [ ] Error message muncul di UI (jangan cuma `console.log` atau `return`)
- [ ] Range check: min/max reasonable + pesan spesifik (e.g. "Enter a weight between 15–350 kg")
- [ ] Empty/invalid input → jangan diam, kasih placeholder atau error
- [ ] `try/catch` di `JSON.parse` localStorage
- [ ] `catch` fallback ke empty array/default value
- [ ] Silent return di handle function = **otomatis kena potong**

## 3. Visual & UX (jangan bikin user bingung)

- [ ] Warna yang berbeda harus punya **makna yang berbeda**
- [ ] Dua status berbeda (e.g. "too low" vs "too high") **jangan pakai warna yang sama**
- [ ] Jangan tampilkan marker/indicator di posisi default yang misleading — sembunyikan sampai user input
- [ ] Hover/active states di semua interactive element
- [ ] Responsive: test di 3 ukuran (mobile, tablet, desktop)
- [ ] Loading state: kalo ada async (font, API, image) — kasih fallback visual
- [ ] Empty state jelas: "No destinations yet" bukan table kosong / blank

## 4. Code Quality

- [ ] Named functions (jangan semua anonymous inline)
- [ ] Pure functions dipisah dari DOM (testable, like `classifyPressure`, `findBracket`)
- [ ] `esc()` sanitizer untuk semua `innerHTML` injection (gunakan `textContent` dulu)
- [ ] `'use strict'` di tiap IIFE
- [ ] Event listener: perhatikan duplikasi — kasih flag atau delegasi kalo render ulang
- [ ] `render()` jangan campur logic dengan DOM mutation (pisah compute vs render)
- [ ] JSDoc minimal di function publik: parameter + return type

## 5. Arsitektur (biar judge nilai Technical Craft tinggi)

Idealnya pisah menjadi 3 bagian dalam file:
```
/* ── Data / Pure Logic ── */
constants, lookup tables, pure functions

/* ── DOM / Rendering ── */  
DOM refs, render functions, event wiring

/* ─── Init ─── */
load, render(), event listeners
```

Kalo pake modules (`<script type="module">`) — nilai Technical Craft naik drastis.

## 6. Automation (extra credit)

- [ ] Minimal 1 test file: test pure functions dengan `console.assert()`

```js
// quick-test.js
console.assert(classifyPressure(80, [90,110]) === 'under', 'under test');
console.assert(classifyPressure(100, [90,110]) === 'ideal', 'ideal test');
console.assert(classifyPressure(120, [90,110]) === 'over', 'over test');
```

Bisa di-run pake `node quick-test.js` atau buka di browser.
Judge lihat effort testing = poin tambahan **meskipun brief ga minta**.

## 7. Final sanity check (sebelum submit)

```
[ ] Semua input punya label
[ ] Ga ada emoji/icon yang conflicting
[ ] Warna error/danger beda dengan warning
[ ] Coba input kosong → ada feedback
[ ] Coba input invalid → ada feedback
[ ] Coba localStorage corrupt → ga crash
[ ] Hard refresh → state masih jalan (kalo pake localStorage)
[ ] Keyboard navigation: Tab through all controls
[ ] Screen reader: forms announce correctly
```

---

**Rule of thumb**: Anggap judge akan test dengan:
1. Tab navigation (keyboard only)
2. Screen reader (VoiceOver / NVDA)
3. Input kosong, invalid, ekstrim (0, negative, huge number)
4. Resize dari 320px sampai 1920px
5. Reload / refresh untuk persistence
6. Corrupt localStorage / missing data
