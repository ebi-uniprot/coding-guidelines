# Javascript code style
Respecting code style means it's easier for other developers to read your code.

## Linting
We use [ESLint](https://eslint.org/) with the [Airbnb style guide](https://github.com/airbnb/javascript)

**TODO: note exceptions**


## Check your code
There should be a script in `package.json` to allow you to run linting:
```
yarn run jslint
```

## VSCode **(TODO: what about other text editors?)**
The "ESLint" plugin for VSCode allows you to quickly see any linting errors in your editor.

The Prettier (supports JSX, flow,...) plugin integrates with eslint (https://prettier.io/docs/en/eslint.html)
