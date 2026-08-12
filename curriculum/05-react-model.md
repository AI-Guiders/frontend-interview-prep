# 05 — React model

## Модель

React — UI = **f(state)**. Ты описываешь результат; библиотека считает diff и обновляет host tree (DOM).

Ключевые идеи:

1. **Render** — вызов функции компонента → описание UI (elements).
2. **Reconciliation** — сравнение с предыдущим деревом; `key` помогает сопоставлять siblings.
3. **Commit** — применение к DOM.
4. **Hooks** — состояние/эффекты, привязанные к порядку вызовов в компоненте (Rules of Hooks).

Fiber / concurrent: обновления могут прерываться; UI остаётся отзывчивым. Для собеса: знать *зачем* `useTransition` / `useDeferredValue`, не устройство fiber pointer.

## Когда ререндер

Компонент ререндерится когда:

- изменился его state;
- изменились props (обычно — родитель ререндернулся и передал новые ссылки);
- контекст, на который он подписан, изменился;
- родитель ререндерится **и** нет memoization boundary.

`React.memo` / `useMemo` / `useCallback` — **escape hatches**, не дефолт. С React Compiler (где включён) ручная мемоизация реже нужна — умей сказать это спокойно.

## Hooks — must

| Hook | Суть | Ловушка |
|------|------|---------|
| `useState` | local state | batching updates; functional updater |
| `useReducer` | сложные переходы | когда state machine лучше |
| `useEffect` | sync с внешним миром | deps, cleanup, strict mode double-invoke |
| `useLayoutEffect` | до paint | jank если тяжелый |
| `useRef` | box mutable / DOM node | не триггерит render |
| `useContext` | broadcast | всё дерево подписчиков |
| `useMemo` / `useCallback` | стабильность ссылок | преждевременная оптимизация |
| `useId` | SSR-safe ids | a11y |

Rules of Hooks: только top-level, только из React functions. Почему — порядок hooks = адрес state.

## Ownership

- State живёт у **ближайшего общего владельца**, которому он нужен.
- Lift state up vs colocate — trade-off пропдрила vs лишних ререндеров.
- Derived state: лучше вычислять при render, чем дублировать в `useEffect`.

## Keys

`key={index}` ломает identity при insert/reorder → баги focus/state. Стабильный id.

## Ловушки

- Stale closure в effect / handler — deps или functional update.
- Effect как «на каждое изменение props синхронизирую state» — чаще anti-pattern.
- Создавать объект/массив/функцию в props без нужды → лишние ререндеры детей.
- Conditional hooks.

## React 19 / modern (знать обзорно)

- `use` для чтения promise/context (где поддерживается).
- Server Components vs Client Components — граница `"use client"`, data на сервере, bundle на клиенте.
- Actions / form helpers — по стеку вакансии (Next.js чаще).

Не врать «я на RSC в проде», если не было — честно: модель + отличия.

## Мини-чеклист

- [ ] Объясню render → reconcile → commit
- [ ] Назову 4 причины ререндера
- [ ] Починю stale closure на примере
- [ ] Выберу где state жить на простом UI (фильтр списка)

## Дальше

→ [06-react-state-data.md](06-react-state-data.md) · [10-machine-coding.md](10-machine-coding.md)
