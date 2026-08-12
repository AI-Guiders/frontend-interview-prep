# 09 — Frontend system design

## Модель

FE SD на собесе — не «нарисуй Kubernetes». Это:

1. **Продукт и constraints** — кто юзер, мобильный?, оффлайн?, realtime?
2. **Информационная архитектура** — экраны, навигация, deep links.
3. **Данные** — источники, freshness, ownership, offline cache.
4. **Клиентская архитектура** — routing, state boundaries, module boundaries.
5. **Нефункциональное** — perf budgets, a11y, i18n, feature flags, observability.
6. **Риски** — XSS, CSRF, PII в localStorage, third-party scripts.

## Каркас ответа (15–20 мин)

1. Уточни scope (MVP vs scale).
2. Нарисуй high-level: CDN → app shell → API / BFF → services.
3. Выбери rendering: CSR / SSR / SSG / hybrid — **почему**.
4. Разбей на features + shared (design system, auth, analytics).
5. Data flow для 1–2 критичных сценариев (feed, checkout, editor).
6. Perf & resilience (skeleton, retry, stale-while-revalidate).
7. Trade-offs — всегда называй цену решения.

## Типовые задачи

- News feed / social timeline
- Admin dashboard с фильтрами
- Collaborative editor (presence, OT/CRDT — обзорно)
- E-commerce product + cart
- Chat / notifications

Для каждой: pagination strategy, cache key, realtime transport (WS vs SSE vs poll), auth.

## Ловушки

- Сразу microfrontends «потому что масштабно».
- Игнор URL как state.
- Один global store на всё.
- Нет плана ошибок и пустых состояний.

## Мини-чеклист

- [ ] Прогоню вслух feed или dashboard по каркасу выше
- [ ] Обосную SSR vs CSR для своей задачи
- [ ] Назову 3 non-functional constraints до кодинга

## Дальше

→ [10-machine-coding.md](10-machine-coding.md) · [../practice/implement-from-scratch.md](../practice/implement-from-scratch.md)
