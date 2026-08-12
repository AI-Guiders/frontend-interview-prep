# 01 — JavaScript core

## Модель

JS — язык с **lexical scope**, **first-class functions**, **prototype chain**, и **единым потоком** + event loop снаружи.

Значение ≠ переменная: переменная — binding в environment record; значение может быть shared (объекты по ссылке).

## Инварианты

1. **`let`/`const`** — temporal dead zone до инициализации; **`var`** — function-scoped + hoist (в современных интервью почти всегда «не используй var, но объясни»).
2. **Closure** — функция помнит lexical environment, где создана. Не «магия», а ссылка на env.
3. **`this`** — не lexical (кроме arrow). Решается *call site*: `obj.m()`, `fn()`, `fn.call`, `new`, class fields/arrows.
4. **Prototype** — `obj → proto → … → null`. `class` — сахар над prototypes + constructor.
5. **Equality** — `===` vs `Object.is`; для объектов сравнение по ссылке, deep equality — отдельно.
6. **Modules** — ESM: static import graph, live bindings; CJS — `require`, copy of exports (знать отличие на уровне «почему circular deps ведут себя иначе»).

## Ловушки

| Симптом | Почему |
|---------|--------|
| `for (var i…; setTimeout(() => console.log(i)))` → все `N` | один binding `i` |
| `obj.method` передали в `setTimeout` — потеряли `this` | call site без receiver |
| `const a = []; a.push(1)` ок | const запрещает *rebind*, не mutation |
| `[] + {}` / `{} + []` | coercion; на собесе лучше сказать «не делаю так в проде» + объяснить ToPrimitive |
| mutate props / shared state | ссылочная семантика объектов |

## Что уметь объяснить вслух (2–3 мин каждое)

- Closures: зачем (encapsulation, partial application), чем опасны (утечки через подписки).
- Prototypal inheritance vs class inheritance mentally.
- Value vs reference; shallow vs deep copy.
- `call` / `apply` / `bind` и когда arrow лучше метода класса.
- Spread vs rest; destructuring pitfalls (defaults, nested).
- Iterable / iterator / generator — хотя бы «зачем `for…of` и spread работают».

## Мини-чеклист

- [ ] Нарисую scope chain для вложенных функций
- [ ] Объясню `this` на 4 call-site без шпаргалки
- [ ] Реализую `deepClone` с оговорками про циклы / Date / Map
- [ ] Отличу `==` / `===` / `Object.is`

## Дальше

→ [02-async-event-loop.md](02-async-event-loop.md) · practice: clone / flatten / EventEmitter
