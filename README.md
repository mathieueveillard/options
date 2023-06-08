# options

```typescript
const defaultOptions =
  <Options extends {}>(defaultValues: Options) =>
  (values: Partial<Options>): Options => ({
    ...defaultValues,
    ...values,
  });
```

```typescript
type Options = {
  color: "red" | "green" | "blue";
  size: "small" | "medium" | "large";
};

const DEFAULT_OPTIONS: Options = {
  color: "red",
  size: "medium",
};

test(`It should provide default values for options that are not specified,
      while preserving options that are specified`, () => {
  // GIVEN
  const options: Partial<Options> = {
    color: "green",
  };

  // WHEN
  const actual = defaultOptions(DEFAULT_OPTIONS)(options);

  // THEN
  const expected: Options = {
    color: "green",
    size: "medium",
  };
  expect(actual).toEqual(expected);
});
```
