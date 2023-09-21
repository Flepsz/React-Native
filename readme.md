# Commands To Setup TypeScript in Expo

## Create an Expo App with TypeScript Template
To create a new Expo app using the TypeScript template, run the following command:
```bash
yarn create expo-app --template
```

## Add TypeScript Dependencies
Install the necessary TypeScript dependencies:
```bash
yarn add --dev @tsconfig/react-native @types/jest @types/react @types/react-test-renderer typescript
yarn add expo react-native-web react-dom @expo/webpack-config
```

## Run the Project
Start your Expo project using the tunnel option:
```bash
yarn expo start --tunnel
```

# Navigation Setup
To set up navigation in your app, follow these steps:

## Install React Navigation
```bash
yarn add @react-navigation/native
```

## Add Navigation Stack Dependencies
```bash
yarn add react-native-screens react-native-safe-area-context @react-navigation/native-stack @react-navigation/stack
```

## Add Bottom Tabs Navigation (Optional)
If you want to use bottom tabs navigation, install the following package:
```bash
yarn add @react-navigation/bottom-tabs
```

# Eslint and Prettier Configuration
Set up ESLint and Prettier for your project:

```bash
yarn add -D expo eslint eslint-config-prettier eslint-config-universe eslint-plugin-react-hooks @typescript-eslint/eslint-plugin @typescript-eslint/parser
```

In your `package.json`, update the `eslintConfig` section to extend the desired ESLint configuration:

```json
{
  "eslintConfig": {
    "extends": "universe/native"
  }
}
```

Create an `.eslintrc.json` file and extend the ESLint configurations:

```json
{
  "extends": ["universe", "plugin:react-hooks/recommended"]
}
```

Install Prettier:

```bash
yarn add expo prettier
```

# CSS Configuration

## Use Viewport Units (vw, vh, vmin, vmax)
To enable viewport units in your styles, install the `react-native-viewport-units` package:

```bash
yarn add react-native-viewport-units --save
```

Import the units in your code:

```javascript
var { vw, vh, vmin, vmax } = require('react-native-viewport-units');
```

# Tailwind CSS Setup

**Choose between Nativewind or Tailwind-RN based on your preference and project requirements.**

## Nativewind

### Install Dependencies
```bash
yarn add nativewind postcss autoprefixer
yarn add --dev tailwindcss@3.3.2
```

### Initialize Tailwind CSS
Run the following command to initialize Tailwind CSS and create the `tailwind.config.js` file:
```bash
npx tailwindcss init
```

### Configure `tailwind.config.js`
Edit your `tailwind.config.js` file to include paths to your component files:
```javascript
module.exports = {
  content: ["./App.{js,jsx,ts,tsx}", "./src/**/*.{js,jsx,ts,tsx}", "./<custom directory>/**/*.{js,jsx,ts,tsx}"],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

### Update `babel.config.js`
Modify your `babel.config.js` to include the Nativewind Babel plugin:
```javascript
module.exports = function (api) {
  api.cache(true);
  return {
    presets: ["babel-preset-expo"],
    plugins: ["nativewind/babel"],
  };
};
```

### Create `postcss.config.js`
Create a `postcss.config.js` file and add the following configuration:
```javascript
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  }
}
```

### Configure `metro.config.js`
Create a `metro.config.js` file and add the following code to enable CSS support in Metro:
```javascript
const { getDefaultConfig } = require('expo/metro-config');

const config = getDefaultConfig(__dirname, {
  isCSSEnabled: true,
});

module.exports = config;
```

### Use Tailwind CSS in Your Project
Create a `globals.css` file and add the following Tailwind CSS imports:
```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

Import the `globals.css` file in your project where needed.

### TypeScript Support
If you are using TypeScript, create a `globals.d.ts` file and add the following reference:
```typescript
/// <reference types="nativewind/types" />
```

## Tailwind-RN
```bash
yarn add tailwind-rn
```

```bash
npx setup-tailwind-rn
```

Follow the configuration steps as described in the terminal, and run:
```bash
yarn dev:tailwind
```

**Note: Keep the dev server running at all times.**

In your `input.css` file, include the following Tailwind CSS imports:
```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

In your `tailwind.config.js` file, specify the content paths for your project.

This completes the setup for Tailwind CSS in your React Native project.