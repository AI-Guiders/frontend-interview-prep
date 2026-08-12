# Question bank (drills)

Используй как карточки: закрой ответ, ответь вслух 60–90 сек, потом сверь.

## JavaScript

1. Разница `==` и `===`; когда `==` всё ещё встречается.
2. Как работает прототипная цепочка; `Object.create`.
3. Closures: пример утечки / stale state.
4. `this` в ordinary function vs arrow; call/apply/bind.
5. Event loop: sync → microtasks → macrotasks; `queueMicrotask` vs `setTimeout(0)`.
6. `Promise.all` / `allSettled` / `race` / `any` — когда какой.
7. Deep vs shallow copy; structuredClone; immutable update pattern.
8. Debounce vs throttle — реализация и use-case.
9. Generators / async iterators — обзорно.
10. Module systems: ESM vs CJS pitfalls.

## TypeScript

1. `interface` vs `type` — практические отличия.
2. Narrowing: typeof, in, discriminated unions.
3. Generics: constraints `extends`, default type params.
4. `unknown` vs `any`; type guards.
5. Utility types: Partial, Pick, Omit, Record, ReturnType.
6. Variance intuitions (ковариантность массивов) — senior-ish.
7. Declaration merging — когда бывает.

## Browser / CSS / a11y

1. Reflow vs repaint; что провоцирует.
2. Event capturing / bubbling / `stopPropagation`.
3. Critical rendering path (упрощённо).
4. Flex vs Grid — когда что.
5. `position` + stacking context.
6. Focus, tab order, `aria-*` минимум для modal/tabs.
7. CORS — почему браузер блокирует; preflight.

## React

1. Почему keys важны; почему index — плохой default.
2. Controlled vs uncontrolled inputs.
3. Rules of Hooks — почему порядок.
4. `useEffect` deps и cleanup; Strict Mode double invoke.
5. Когда lift state / когда colocate.
6. Context pitfalls (high-frequency).
7. memo / useMemo / useCallback — когда да/нет.
8. Error boundaries: что ловят / не ловят.
9. CSR vs SSR vs RSC — одной схемой.
10. Как бы отладил лишний ререндер.

## Data / perf / testing

1. Race condition в fetch — как чинить.
2. Cache invalidation после мутации.
3. Virtualization — зачем.
4. LCP / INP / CLS своими словами.
5. Testing Library queries priority.
6. Flaky E2E — топ причин.

## System design prompts

1. Design a news feed frontend.
2. Design an admin table with saved filters + shareable URL.
3. Design notifications (in-app + optional push).
4. Design a multi-step checkout.

Для SD: всегда constraints → IA → data → rendering → risks.
