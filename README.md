# Svelte Todo App Assignment

This is a simple web application built with Svelte that allows you to keep track of your tasks and stay organized.

🔗 **Live Demo:** []()

## 🚀 Project Structure

```text
└── 📁src
    └── 📁components
        ├── filter-button.svelte
        ├── task-list.svelte
        ├── todo-form.svelte
    └── 📁lib
        └── 📁assets
            ├── favicon.svg
        ├── index.ts
    └── 📁routes
        ├── +layout.svelte
        ├── +page.svelte
    └── 📁utils
        ├── constants.ts
        ├── types.ts
    ├── app.d.ts
    ├── app.html
└── 📁static
    ├── robots.txt
```

## ⚡ Tools

- Svelte: A modern JavaScript framework for building user interfaces.

- TypeScript: A statically typed superset of JavaScript that compiles to plain JavaScript.

- Vite: A fast development server and build tool.

- SvelteKit: A framework for building full-stack Svelte applications.

## 🚀 Why Svelte is great for front-end development

- Compiles rapidly your components into highly efficient JavaScript code that runs in the browser.

- Declarative syntax with Svelte `runes` and `markup` helping development and debug more easier .

- Svelte's compiler generates code that is highly optimized and has a small bundle size.

- Easy learning curve with component-driven, props and side-effect management like React and Vue.

- Lightweight and does not require any additional dependencies, only SvelteKit is far enough.

- Great developer experience with features like `runes`, `markup`, hot reload, etc...

## 🧞 Commands

You could also use `yarn` or any other package managers:

| Command                   | Action                                           |
| :------------------------ | :----------------------------------------------- |
| `npm install`             | Installs dependencies                            |
| `npm run dev`             | Starts local dev server at `localhost:5173`      |
| `npm run build`           | Build your production site to `./svelte-kit/`          |
| `npm run preview`         | Preview your build locally at `localhost:4173`     |
