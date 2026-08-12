# 07 — Performance

## Модель

Perf = ощущение пользователя + бюджеты. Метрики (упрощённо):

- **LCP** — largest contentful paint
- **INP** — interaction to next paint (вместо FID в современных разговорах)
- **CLS** — cumulative layout shift

Инструменты: DevTools Performance, React Profiler, Lighthouse, bundle analyzer.

## Frontend рычаги

1. **Bundle** — code split (`React.lazy`, route-based), tree shaking, не тащить moment.js «на всякий».
2. **Render** — меньше работы на interaction: memo boundaries, виртуализация списков, defer non-urgent updates (`useTransition`).
3. **Network** — меньше waterfall, HTTP cache, image sizes/`srcset`, prefetch.
4. **Main thread** — не блокировать долгим sync JS; chunking.
5. **Layout** — избегать thrashing; скелетоны против CLS.

## React-specific

- Profiler: что ререндерится и почему.
- Список 10k строк → virtualization (react-window / tanstack virtual), не «просто memo».
- Context split (частота обновлений).
- Hydration cost (SSR/RSC stacks).

## Ловушки

- Оптимизировать до измерения.
- `useMemo` на дешёвых вычислениях.
- Гигантский Context value object каждый render.
- Картинки без размеров → CLS.

## Мини-чеклист

- [ ] Назову LCP/INP/CLS своими словами
- [ ] Предложу план оптимизации медленного списка
- [ ] Найду лишний ререндер в Profiler (мысленно)
- [ ] Скажу 3 способа резать bundle

## Дальше

→ [08-testing.md](08-testing.md) · [09-frontend-system-design.md](09-frontend-system-design.md)
