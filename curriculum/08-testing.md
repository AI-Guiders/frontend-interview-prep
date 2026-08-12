# 08 — Testing

## Модель

Пирамида для FE:

1. **Unit** — чистые функции, reducers, hooks с изоляцией.
2. **Component / integration** — Testing Library: поведение с точки зрения пользователя.
3. **E2E** — Playwright/Cypress: критические пути.

На собесе чаще: «как протестируешь этот компонент?» → role/name queries, не implementation details.

## Инварианты

- Тестируй **что видит пользователь** (`getByRole`, `getByLabelText`), не className/internal state.
- Async: `findBy*`, `waitFor`.
- Моки сети: MSW предпочтительнее ручного mock fetch в больших приложениях.
- Snapshot — осторожно; не как единственный тест.

## Что уметь сказать

- Разница unit vs integration.
- Почему не тестировать каждый `useEffect` по отдельности.
- Flaky E2E: причины и стабилизация.
- Visual regression — когда имеет смысл (design system).

## Мини-чеклист

- [ ] Напишу тест на форму: ошибка валидации видна
- [ ] Объясню почему `getByTestId` — last resort
- [ ] Опишу smoke E2E для login → home

## Дальше

→ [09-frontend-system-design.md](09-frontend-system-design.md)
