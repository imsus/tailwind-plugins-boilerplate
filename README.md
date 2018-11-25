<h1 align="center" style="border-bottom: 0">🛩 Tailwind Plugin Boilerplate</h1>
<p align="center">Boilerplate for creating TailwindCSS Plugins from scratch.<p>
<p align="center">
  <a href="https://github.com/imsus"><img src="https://flat.badgen.net/badge/author/@imsus/purple?icon=github" alt="author badge with @imsus written on it"></a>
</p>

## ⭐️ Features

- Using Parcel for bundling and dev-server.
- 2 Sample plugin provided for reference.
    - `sample-plugin-with-params`
    - `sample-plugin-without-params`

## ⚠️ Requirements

1. You must installed `parcel-bundler` globally. Run `npm i -g parcel-bundler` or `yarn global add parcel-bundler` if you have `yarn`.
2. Make sure you can run `parcel` in terminal. You should put `parcel` inside your `PATH` environment variable (`npm` and `yarn` takes care of this).

## ✅ Usage

1. Clone/Download this repo.
2. Install code dependencies. Run `npm install` or `yarn install` if you prefer `yarn` over `npm`.
3. Start the development. Run `npm run dev` or `yarn dev`. This will watch `index.html` file and other files referenced inside `index.js` file.
4. If you are finished the development and want to move into production then run `npm run prod` or `yarn prod`. This will bundle all of the code, minify, and remove all unused code inside from `tailwindcss` dependencies.
