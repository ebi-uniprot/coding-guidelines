# Javascript code style
Respecting code style means it's easier for other developers to read your code.

## Import order
Try to respect a sensible order in the imports, and group and separate them as much as it makes sense.
This needs to help in grasping easily what is used within a file, or find a specific import quickly.
A possible order might be:
 - external imports
 - components
 - hooks
 - utils (split by further groups if a lot)
 - types
 - non-standard imports (`.scss` or others)

It might be impossible to separate more if 2 different kind of things are exported from the same file, this is fine.

Another possible way of ordering might be alphabetically, especially for similar imports from a same file
(e.g. if importing lots of icons at once from the samee file).

## Linting
We use [ESLint](https://eslint.org/) with the [Airbnb style guide](https://github.com/airbnb/javascript)
We override some of these rules in the eslint configuration file,
and added some custom rules that specifically apply to our codebase.

**TODO: note exceptions**


## Check your code
There should be a script in `package.json` to allow you to run linting:
```
yarn run test:lint
```

## VSCode **(TODO: what about other text editors?)**
The "ESLint" plugin for VSCode allows you to quickly see any linting errors in your editor.

The Prettier (supports JSX, flow,...) plugin integrates with eslint (https://prettier.io/docs/en/eslint.html)

VSCode also provides built in support for the TypeScript checks within the editor
