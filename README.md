# CRA Stroybook Setup Example

This is an example of how to setup Storybook with Create React App.

You can read this README or commit logs to see how to setup Storybook with Create React App.

## Library Versions

- [Create React App@5.0.1](https://create-react-app.dev/)
  - setup with typescript.
- [Jest@29.3.1](https://jestjs.io/)
  - setup with ts-jest and react-testing-library.
- [Storybook@6.5.15](https://storybook.js.org/)
  - setup with @storybook/addon-storyshots.

## Why make this example?

I tried to setup Storybook with Create React App, but it was not easy way. Dependencies are not compatible with each other. Creating boilerplate cli is not satisfied. So I made this example to help you.

# Setup logs

### 1. Create React App

```bash
npx create-react-app --template typescript
````

### 2. Jest

```bash
npm install -D jest@latest @types/jest@latest ts-jest 
```

```bash
npm install -D typescript @types/node@latest @types/react@latest @types/react-dom@latest
```

create `jest.config.js`.

```ts
// jest.config.js
module.exports = {
  roots: ["<rootDir>/src"],
  testMatch: [
    "**/__tests__/**/*.+(ts|tsx|js)",
    "**/?(*.)+(spec|test).+(ts|tsx|js)",
  ],
  transform: {
    "^.+\\.(ts|tsx)$": "ts-jest",
  },
  setupFilesAfterEnv: ["<rootDir>/src/setupTests.ts"],
};
```

```bash
# test run to command.
npm test
```

### 3. Storybook

```bash
npx init storybook
```

```bash
npm install -D @storybook/preset-create-react-app@latest
```

```bash
# test to start storybook
npm run storybook
```

### 4. Storybook addon storyshots

```bash
npm install --save @storybook/addon-storyshots
```

```bash
touch src/snapshot.test.ts
```

```ts
// snapshot.test.ts
import initStoryshots from "@storybook/addon-storyshots";
import { render } from "@testing-library/react";

initStoryshots({
  renderer: render,
});
```