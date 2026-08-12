# 03 — TypeScript

## Модель

TS — **статические контракты** поверх JS. На собесе ценят не «знаю 40 utility types», а:

- смоделировать props / API state без `any`;
- объяснить generics;
- отличить type vs interface на практике;
- сузить типы (narrowing) так, чтобы UI был безопасным.

## Инварианты

1. **Structural typing** — важна форма, не имя («уткой»).
2. **`interface` vs `type`** — для собеса: interfaces mergeable / extendable; type aliases мощнее для unions/mapped. Команда обычно фиксирует одно правило линтером.
3. **Narrowing** — `typeof`, `in`, discriminated unions (`kind: 'loading' | 'ok' | 'err'`).
4. **Generics** — параметризация контракта: `function identity<T>(x: T): T`, `ApiResult<T>`.
5. **`unknown` > `any`** — unknown заставляет сузить; any отключает проверку.
6. **Readonly / const assertions** — иммутабельность на уровне типов (не runtime magic).

## Паттерны для UI/API

```ts
type LoadState<T> =
  | { status: "idle" }
  | { status: "loading" }
  | { status: "success"; data: T }
  | { status: "error"; error: string };
```

Discriminated union → exhaustive `switch` → меньше «забыли ветку» в UI.

Props:

```ts
type ButtonProps = {
  variant: "primary" | "ghost";
  onClick: () => void;
  children: React.ReactNode;
  disabled?: boolean;
};
```

## Ловушки

| Ловушка | Суть |
|---------|------|
| `as` везде | врёшь компилятору |
| Optional `data?` вместо union | `data` «есть», но runtime undefined |
| Generics «для галочки» | не связывают вход/выход |
| Enums | часто предпочитают union string literals |
| `React.FC` споры | знать, что дети/generics исторически болели; многие команды пишут явный тип props |

## Минимум advanced (Middle)

- `Partial` / `Pick` / `Omit` / `Record` — когда полезны
- Conditional types — узнать в коде (`T extends U ? X : Y`)
- `satisfies` — проверка без расширения типа
- Generics constraints: `T extends { id: string }`

## Мини-чеклист

- [ ] Смоделирую LoadState без optional-каши
- [ ] Напишу generic `unwrap` / `apiGet<T>`
- [ ] Объясню structural typing на примере «два разных interface с одним полем»
- [ ] Не использую `any` без оправдания

## Дальше

→ [04-browser-css-a11y.md](04-browser-css-a11y.md) · [05-react-model.md](05-react-model.md)
