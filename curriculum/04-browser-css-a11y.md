# 04 — Browser, CSS, accessibility

## Модель рендера (коротко)

HTML → DOM; CSS → CSSOM; вместе render tree → **layout (reflow)** → **paint** → **composite**.

Менять layout-триггерящие свойства (width, top, font-size…) дорого пачками. Transform/opacity чаще остаются на композиторе.

Critical rendering path / FOUC / font loading — знать на уровне «что замедляет first paint».

## DOM & events

- Bubbling vs capturing; `stopPropagation` vs `preventDefault`.
- Event delegation — зачем на списках.
- `addEventListener` options: `{ once, passive, capture }`.
- Reflow thrash: читать layout (`offsetHeight`) после записи стилей в цикле.

## CSS must

- Cascade / specificity / inheritance — не «магия !important».
- Flex vs Grid: одномерный vs двумерный layout.
- Responsive: mobile-first, container queries (хотя бы слышал).
- Stacking context / z-index — почему «z-index: 9999 не помог».
- Logical properties (`margin-inline`) — плюс для i18n (stretch).

## Accessibility (не optional на хороших собесах)

- Семантика: `button` vs `div onClick`.
- Keyboard: focus order, `:focus-visible`, Esc/Enter.
- ARIA — усиливает семантику, не заменяет.
- Имена доступности (accessible name) у контролов.
- Контраст, motion (`prefers-reduced-motion`).

На machine coding часто режет: модалка без focus trap / без Esc.

## Network (FE view)

- HTTP caching headers на уровне «зачем ETag / Cache-Control».
- CORS — кто проверяет (браузер), preflight.
- Cookies vs bearer token в SPA (кратко trade-offs).

## Мини-чеклист

- [ ] Объясню layout vs paint vs composite
- [ ] Сверстаю карточку на Flex/Grid без паники
- [ ] Модалка: focus trap + Esc + aria-modal
- [ ] Delegation на 1000 строк списка

## Дальше

→ [05-react-model.md](05-react-model.md) · [07-performance.md](07-performance.md)
