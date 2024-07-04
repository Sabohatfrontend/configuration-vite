1. Project Setup
   - Initialize the project using [Vite](https://vitejs.dev/guide/) with the [_react-ts_ template](https://vite.new/react-ts).
     __Install Vite:__
     ```
          npm create vite@latest
     ```
     Then run this:
     ```
     npm install
     npm run dev
     ```
2. Code Quality Tools
   1. __ESLint__
      - Set up ESLint:
        ```
        npm i eslint --save-dev
        ```
      - Set up [eslint-plugin-react-compiler](https://www.npmjs.com/package/eslint-plugin-react-compiler):
        ```
        npm install eslint-plugin-react-compiler --save-dev
        ```

      - Change eslintrc.cjs:
        ```
         module.exports = {
        root: true,
        env: { browser: true, es2020: true },
        extends: [
          'eslint:recommended',
          'plugin:@typescript-eslint/recommended',
          'plugin:react-hooks/recommended',
        ],
        ignorePatterns: ['dist', '.eslintrc.cjs'],
        parser: '@typescript-eslint/parser',
        plugins: ["react-compiler", "@typescript-eslint"],
        rules: {
         "@typescript-eslint/no-explicit-any": "error",
         "react-compiler/react-compiler": "error",
        },
      }
      ```
   2. __Prettier__
      - now just install all prettier dependencies:
        ```
        npm i -D prettier eslint-config-prettier eslint-plugin-prettier
        ```
      - Create .prettierrc.cjs file in root directory:
```
          module.exports = {
           trailingComma: "es5",
           tabWidth: 2,
           semi: true,
           singleQuote: true,
           };
```
   3. __Husky__
      - Add Husky and configure it to run linting on pre-commit:
        ```
        npm i -D husky
        ```
      - Run
        ``` npx husky init ``` in your terminal.
        
   4. package.json commands
      - Add the following npm scripts:
          "format:fix": "prettier --write ./src".

My ___package.json___:
```
{
  "name": "task1",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "tsc -b && vite build",
    "lint": "eslint . --ext ts,tsx --report-unused-disable-directives --max-warnings 0",
    "preview": "vite preview",
    "prepare": "husky",
     "format:fix": "prettier --write ./src"
  },
  "dependencies": {
    "react": "^18.3.1",
    "react-dom": "^18.3.1"
  },
  "devDependencies": {
    "@types/react": "^18.3.3",
    "@types/react-dom": "^18.3.0",
    "@typescript-eslint/eslint-plugin": "^7.13.1",
    "@typescript-eslint/parser": "^7.13.1",
    "@vitejs/plugin-react": "^4.3.1",
    "eslint": "^8.57.0",
    "eslint-config-prettier": "^9.1.0",
    "eslint-plugin-prettier": "^5.1.3",
    "eslint-plugin-react-compiler": "^0.0.0-experimental-0998c1e-20240625",
    "eslint-plugin-react-hooks": "^4.6.2",
    "eslint-plugin-react-refresh": "^0.4.7",
    "husky": "^9.0.11",
    "prettier": "^3.3.2",
    "typescript": "^5.2.2",
    "vite": "^5.3.1"
  }
}
```
