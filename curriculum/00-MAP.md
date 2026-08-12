# 00 — Карта территории

## Слои (снизу вверх)

```
Browser platform (DOM, CSSOM, layout/paint, network, a11y)
        ↑
JavaScript runtime (scope, this, prototypes, modules)
        ↑
Async model (event loop, promises, micro/macro)
        ↑
TypeScript (types as contracts for UI + API)
        ↑
React model (render, reconciliation, hooks, ownership)
        ↑
Data & state (fetch, cache, forms, global store)
        ↑
Quality (testing, perf, a11y) + machine coding + FE SD
```

Интервью почти всегда бьёт **на стыках слоёв**: stale closure = JS + React; waterfall = React + network; CLS = CSS + React.

## Порядок модулей

| # | Файл | Must для Sprint | Standard |
|---|------|-----------------|----------|
| 01 | `01-javascript-core.md` | ✓ | ✓ |
| 02 | `02-async-event-loop.md` | ✓ | ✓ |
| 03 | `03-typescript.md` | ✓ | ✓ |
| 04 | `04-browser-css-a11y.md` | skim | ✓ |
| 05 | `05-react-model.md` | ✓ | ✓ |
| 06 | `06-react-state-data.md` | ✓ | ✓ |
| 07 | `07-performance.md` | skim | ✓ |
| 08 | `08-testing.md` | skim | ✓ |
| 09 | `09-frontend-system-design.md` | stretch | ✓ Mid+ |
| 10 | `10-machine-coding.md` | ✓ | ✓ |

## Форматы раундов (что ждать)

1. **JS/TS screen** — closures, event loop, руками `debounce` / `Promise.all`, generics.
2. **React depth** — когда ререндер, hooks rules, state ownership, иногда RSC/Suspense.
3. **Machine coding** — autocomplete, infinite list, modal stack, tabs (45–90 мин).
4. **FE system design** — лента, чат, design system, collaborative UI (Middle+).
5. **Behavioral / project deep dive** — свои проекты: trade-offs, инциденты, метрики.

## Как читать модуль

В каждом файле блоки:

- **Модель** — картинка в голове
- **Инварианты** — то, что нельзя путать
- **Ловушки** — типичные fail на собесе
- **Мини-чеклист** — «могу объяснить без Гугла»
- **Дальше** — ссылка на practice / drills
