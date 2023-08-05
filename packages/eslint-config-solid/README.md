# eslint-config-solid

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

## License

MIT License