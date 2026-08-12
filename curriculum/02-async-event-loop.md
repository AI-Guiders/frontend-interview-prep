# 02 — Async & event loop

## Модель

Один JS-thread. Долгая работа либо режется на куски (async), либо блокирует UI.

**Event loop (упрощённо для собеса):**

1. Выполнить синхронный код (call stack).
2. Когда стек пуст — сначала **microtasks** (`Promise.then`, `queueMicrotask`, `MutationObserver`).
3. Потом следующий **macrotask** (`setTimeout`, `setInterval`, I/O, UI events в браузере — с нюансами).
4. Между макрозадачами браузер может render (не гарантировано «после каждого timeout»).

`async/await` = Promise + microtasks. `await x` → если `x` thenable, продолжение после microtask.

## Инварианты

1. `Promise.resolve().then(fn)` почти всегда раньше `setTimeout(fn, 0)`.
2. Цепочка `.then` ставит *новые* microtasks; долгий цикл microtasks откладывает render → jank.
3. `async` функция всегда возвращает Promise.
4. Unhandled rejection — отдельный fail mode (знать, что бывает в Node/browser).
5. Cancellation — в браузере чаще `AbortController`, не «убить промис».

## Ловушки

| Паттерн | Проблема |
|---------|----------|
| `await` в цикле по независимым запросам | водопад вместо `Promise.all` |
| `Promise.all` без обработки частичных ошибок | один fail валит всё → `allSettled` |
| Забыли `return`/`await` в `async` | «проглотили» ошибку / порядок сюрприз |
| Полагаться на точный timing `setTimeout(0)` | порядок vs microtasks |
| Гонки fetch: ответ A пришёл после B | нужен ignore/abort/seq id |

## Classic output puzzle

Умей предсказать порядок логов:

```js
console.log("a");
setTimeout(() => console.log("b"), 0);
Promise.resolve().then(() => console.log("c"));
console.log("d");
// a, d, c, b
```

Усложнения: nested `then`, `async` function, `queueMicrotask`, два timeout.

## Что писать руками

См. [practice/implement-from-scratch.md](../practice/implement-from-scratch.md):

- `Promise.all` / `race` / `any` / `allSettled`
- `delay(ms)`
- retry с backoff
- debounce / throttle

## Мини-чеклист

- [ ] Micro vs macro — своими словами + пример
- [ ] Почему `await` в for — медленно для независимых I/O
- [ ] Гонка запросов: как чинить
- [ ] AbortController: связать с fetch

## Дальше

→ [03-typescript.md](03-typescript.md)
