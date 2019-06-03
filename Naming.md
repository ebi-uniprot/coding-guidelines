# Naming Style Guide

1. `PascalCase` for name<sup>1</sup>
2. `camelCase` for members<sup>1</sup>
3. Do not use an `I` prefix for interfaces.<sup>1</sup> Similarly, do not use a `Type` or `Interface` suffix to avoid conflicts with other entities (eg React components).
4. Name `ts|js|json` files with `camelCase`<sup>1</sup>. Name `tsx|jsx` files with `PascalCase.
5. If a file contains only types, interfaces or enums use `Type` as the suffix in the filename. Eg: `filenameType.ts`
6. Attempt to group types together into the same file as much as possible.
7. When a type's member is an array don't define the type of the array's elements inline - define this separately.

###### Bad

```
type Positions = {
  start: number;
  end: number;
}[]
```

###### Good

```
type Position = {
  start: number;
  end: number;
}
type Positions = Position[]
```

8. Do not use plural enum names. More generally, only use plural names for entities which are arrays.

###### Bad

```
enum Directions {
  Up,
  Down,
  Left,
  Right
}
```

###### Good

```
enum Direction {
  Up,
  Down,
  Left,
  Right
}
```

9. DO choose easily readable identifier names. For example, a property named HorizontalAlignment is more English-readable than AlignmentHorizontal. <sup>2</sup>

10. DO favor readability over brevity. The property name CanScrollHorizontally is better than ScrollableX (an obscure reference to the X-axis). <sup>2</sup>

11. DO NOT use underscores, hyphens, or any other nonalphanumeric characters. <sup>2</sup>

12. DO name classes and structs with nouns or noun phrases, using PascalCasing. This distinguishes type names from methods, which are named with verb phrases. <sup>3</sup>

# References

1. https://github.com/basarat/typescript-book/blob/master/docs/styleguide/styleguide.md
2. https://docs.microsoft.com/en-us/dotnet/standard/design-guidelines/general-naming-conventions
3. https://docs.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-classes-structs-and-interfaces
