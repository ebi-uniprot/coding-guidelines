# Styling

<img src="https://i.imgur.com/9qzBYbH.jpg" width="300">

## Guidelines
- use `rem` instead of `px`

## CSS naming
We use the [BEM methodology](https://en.bem.info/methodology/).

### Block
Standalone entity that is meaningful on its own.

### Element
A part of a block that has no standalone meaning and is semantically tied to its block.

### Modifier
A flag on a block or element. Use them to change appearance or behavior.

### Naming rules
`block-name__elem-name_mod-name_mod-val`

- Names are written in lowercase Latin letters.
- Words are separated by a hyphen (-).
- The block name defines the namespace for its elements and modifiers.
- The element name is separated from the block name by a double underscore (__).
- The modifier name is separated from the block or element name by a single underscore (_).
- The modifier value is separated from the modifier name by a single underscore (_).
- For boolean modifiers, the value is not included in the name.
