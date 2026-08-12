# 06 — React: data & state management

## Модель

Три разных «состояния»:

1. **Server/remote** — данные с API (кэш, stale, revalidate).
2. **URL/UI** — то, чем делятся вкладки/ссылки (фильтры, tab id).
3. **Ephemeral client** — модалка открыта, hover, draft в инпуте.

Путаница этих трёх = половина плохих архитектур.

## Data fetching

Классика:

- fetch в `useEffect` + loading/error — ок для скрина, в проде часто React Query / SWR / router loaders.
- **Waterfalls** — компонент ждёт A, потом монтирует B, тот ждёт C.
- **Race** — медленный ответ затирает новый (seq / abort).
- Cache keys — по URL+params; инвалидация после мутации.

Suspense + error boundaries — модель «UI как дерево fallback'ов».

## Forms

- Controlled vs uncontrolled — trade-offs.
- Validation: sync UX vs server errors.
- Optimistic UI — показать успех до ответа; откат при ошибке.
- Не хранить огромную форму целиком в global store без нужды.

## Global state

| Подход | Когда |
|--------|--------|
| Local state | почти всегда сначала |
| Context | редкие updates, theme/locale/auth session |
| Redux / Zustand / Jotai / … | сложный клиентский domain, много writers |
| Server cache library | remote data |

На собесе: «зачем Redux» — не «так принято», а конкретный pain (time-travel, много независимых подписчиков, сложные transitions).

## Auth session (FE)

- Где токен: memory vs httpOnly cookie.
- XSS vs CSRF trade-offs одной фразой.
- Protected routes = UI convenience, не security boundary.

## Мини-чеклист

- [ ] Разведу remote / URL / ephemeral на примере «таблица с фильтрами»
- [ ] Опишу invalidation после POST
- [ ] Скажу когда Context — плохая идея (high-frequency)
- [ ] Optimistic update + rollback сценарий

## Дальше

→ [07-performance.md](07-performance.md) · [08-testing.md](08-testing.md)
