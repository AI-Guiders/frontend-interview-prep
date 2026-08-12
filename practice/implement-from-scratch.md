# Practice — implement from scratch

Цель: руками, без копипаста из чата. Таймер. После — сравни с эталоном (свой рефактор ок).

## Правила

1. Только docs + MDN / React docs — не StackOverflow «готовое решение».
2. TypeScript по умолчанию.
3. После сдачи себе: 5 bullets «что бы улучшил».
4. Sprint: 3 задачи; Standard: все.

## Tier A (обязательный минимум)

### A1. Debounced search box

- Input + список результатов из mock API (`setTimeout` + random delay).
- Debounce 300ms.
- Отмена устаревшего ответа (seq id или `AbortController`).
- Loading / empty / error.

### A2. Accessible tabs

- Клавиатура: стрелки, Home/End.
- `role="tablist" | tab | tabpanel"`, `aria-selected`.
- Фокус management.

### A3. Modal

- Open/close, focus trap (хотя бы первый/последний focusable + Esc).
- `aria-modal`, restore focus на trigger.
- Backdrop click optional.

### A4. Paginated table

- Client-side sort + filter.
- Pagination controls.
- URL sync опционально (Standard).

## Tier B

### B1. Autocomplete

- Keyboard navigate highlights.
- Enter selects; Esc clears.
- Highlight match substring.

### B2. Infinite list

- IntersectionObserver sentinel или scroll handler.
- Deduplicate pages; stop when exhausted.

### B3. Mini kanban

- Columns + cards; drag **или** buttons move left/right.
- Persist to `localStorage`.

### B4. Form wizard

- 3 steps; validation per step; summary; back keeps draft.

## Tier C (stretch)

### C1. Virtualized list (windowing)

- Fixed row height; render only visible + overscan.
- Объясни почему без библиотеки тяжело на variable height.

### C2. Tiny router

- `pushState` + popstate; nested routes optional.
- Guard example (fake auth).

## DoD на задачу

- [ ] Happy path работает
- [ ] Empty + error есть
- [ ] Нет мутации state
- [ ] Могу рассказать структуру за 90 секунд
