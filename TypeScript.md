# TypeScript Name Style Guide

1. `PascalCase` for name<sup>1</sup>
2. `camelCase` for members<sup>1</sup>
3. Do not use an `I` prefix for interfaces.<sup>1</sup> Similarly, do not use a `Type` or `Interface` suffix to avoid conflicts with other entities (eg React components).
4. Name files with camelCase<sup>1</sup>
5. If a file contains only types, interfaces or enums use `Type` as the suffix in the filename. Eg: `filenameType.ts`
6. When a type's member is an array don't define the type of the array's elements inline - define this separately.

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

7. Do not use plural enum names. More generally, only use plural names for entities which are arrays.

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

# References

1. https://github.com/basarat/typescript-book/blob/master/docs/styleguide/styleguide.md
