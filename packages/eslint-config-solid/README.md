# eslint-config-solid
This package configures a set of ESLint rules to to assist in code style checking while working on [SolidJS](https://www.solidjs.com/) applications with TypeScript.

## Features
- Intended to support ESLint versions `>=8.0.0`.
- **Target Environment**: `browser`
- **Target ECMAScript Version**: ES2020 [(Wikipedia)](https://en.wikipedia.org/wiki/ECMAScript_version_history#ES2020)
- Accessibility rules through [`eslint-plugin-jsx-a11y`](https://www.npmjs.com/package/eslint-plugin-jsx-a11y)
- Import sorting through `eslint-plugin-simple-import-sort`. See this [section](#rules-you-may-want-to-override) for details on how imports are grouped by default when using this config.

## Installation
With `npm`:
```
npm i -D eslint @typescript-eslint/eslint-plugin @typescript-eslint/parser @pxeeio/eslint-config-solid
```

With `yarn`:
```
yarn add -D eslint @typescript-eslint/eslint-plugin @typescript-eslint/parser @pxeeio/eslint-config-solid
```

With `pnpm`:
```
pnpm add -D eslint @typescript-eslint/eslint-plugin @typescript-eslint/parser @pxeeio/eslint-config-solid
```

## Recommended Usage
If you use `.eslintrc.(cjs|js)` or `eslint.config.(cjs|js)`, I **HIGHLY** recommend that you also use [`eslint-define-config`](https://www.npmjs.com/package/eslint-define-config), which provides type-hints when defining your settings.

At the very least, add the following value to the `extends` property in your `.eslintrc.*` file:

```js
// @ts-check

const {defineConfig} = require('eslint-define-config');

module.exports = defineConfig({
    // or: extends: '@pxeeio/eslint-config-solid',
    extends: [
        // ^ ... configs that can be overwritten
        '@pxeeio/eslint-config-solid',
        // v ... configs that can override settings defined here
    ],
    // ... settings, rules, overrides, etc.
});
```

## Import Sort Order
Each group of imports must be separated with a newline character. Please see the [README](https://github.com/lydell/eslint-plugin-simple-import-sort#custom-grouping) for `eslint-plugin-simple-import-sort` if you wish to override the default setting.

**Note**: Groups 4-6 are meant to organize imports that make use of path aliases.
- `~` precedes `!` which precedes `@`.

```ts
// 1. Side effect imports
import './polyfills';

// 2. Node.js built-ins prefixed with `node:`
import {resolve} from 'node:path';

// 3. 3rd party packages.
import {MetaProvider} from '@solidjs/meta';
import {type Component, createSignal} from 'solid-js';

// 4. Imports that start with `~`.
import packageJSON from '~/package.json';

// 5. Imports that start with `!`.
import {testUtility} from '!/utilities/test-utility';

// 6. Imports that start with `@`.
import LandingPage from '@/pages/LandingPage';

// 7a. Absolute imports and other imports not matched in another group
// 7b. Relative imports. Anything that starts with a dot.
import SomeAbsoluteImport from '/path/to/import/__also__/this/goes/before/relative/imports';
import {someVariable} from '../../someModule'
import styles from './styles.module.css';

```

### Rules You May Want to Override
- `quotes`: Prefer single quotes, except to avoid escape characters.
- `indent`: Prefer an indent size of 4 spaces over 2 spaces.
- `max-len`: 100 characters max.
- `array-bracket-spacing` - Prefer `['foo', 'bar']` over `[ 'foo', 'bar' ]`.
- `object-curly-spacing` - Prefer `{foo: 'bar'}` over `{ foo: 'bar' }`.
- `comma-dangle` - Prefer trailing commas.
- `semi` - Prefer use of semi-colons.
- `@typescript-eslint/consistent-type-imports` - Prefer use of the `type` keyword when importing variables from other modules as types.

## License

[MIT](https://github.com/pxeeio/eslint-configs/blob/main/packages/eslint-config-solid/LICENSE) License
