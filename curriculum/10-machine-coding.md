# 10 — Machine coding

## Модель

Machine coding = за ограниченное время собрать **работающий UI** с чистым разделением ответственности. Оценивают:

- читаемость и структура;
- корректность edge cases;
- UX базовый (loading/empty/error);
- умение говорить вслух trade-offs.

Не «идеальный Redux». Лучше простой working MVP + понятные next steps.

## Ритуал 45–60 мин

1. **2–3 мин** — уточни требования (scope, данные, constraints).
2. **5 мин** — компоненты + state ownership на бумаге/в комментарии.
3. **Основное** — vertical slice: сначала happy path end-to-end.
4. **Edge** — empty, error, debounce, keyboard.
5. **2 мин** — что бы сделал дальше (a11y, tests, perf).

## Частые задания

См. [practice/implement-from-scratch.md](../practice/implement-from-scratch.md):

- Autocomplete / typeahead
- Infinite scroll / virtual list (упрощённо)
- Tabs + accordion
- Modal / focus trap (упрощённо)
- Tic-tac-toe / memory game
- Kanban column
- Form wizard
- Debounced search + cancel in-flight

## Инварианты на собесе

- Controlled inputs с одним source of truth.
- Ключи списков стабильные.
- Не мутировать state in place.
- Вынести pure helpers из компонента.
- Не копипастить огромный CSS framework — достаточно простого layout.

## Мини-чеклист

- [ ] 3 задачи из practice сделаны без туториала под рукой
- [ ] Умею объяснить state ownership за 60 секунд
- [ ] Есть привычка: happy path → edges → polish

## Дальше

→ [../drills/question-bank.md](../drills/question-bank.md) · [../progress/CHECKLIST.md](../progress/CHECKLIST.md)
