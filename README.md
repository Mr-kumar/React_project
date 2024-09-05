# React + TypeScript + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type aware lint rules:

- Configure the top-level `parserOptions` property like this:

```js
export default tseslint.config({
  languageOptions: {
    // other options...
    parserOptions: {
      project: ['./tsconfig.node.json', './tsconfig.app.json'],
      tsconfigRootDir: import.meta.dirname,
    },
  },
})
```

- Replace `tseslint.configs.recommended` to `tseslint.configs.recommendedTypeChecked` or `tseslint.configs.strictTypeChecked`
- Optionally add `...tseslint.configs.stylisticTypeChecked`
- Install [eslint-plugin-react](https://github.com/jsx-eslint/eslint-plugin-react) and update the config:

```js
// eslint.config.js
import react from 'eslint-plugin-react'

export default tseslint.config({
  // Set the react version
  settings: { react: { version: '18.3' } },
  plugins: {
    // Add the react plugin
    react,
  },
  rules: {
    // other rules...
    // Enable its recommended rules
    ...react.configs.recommended.rules,
    ...react.configs['jsx-runtime'].rules,
  },
})
```
The foder structure that i suggest you to use is 
src/
├── assets/                # Static assets like images, fonts, etc.
│   ├── images/
│   └── fonts/
├── components/            # Reusable UI components
│   ├── Button.tsx
│   └── Modal.tsx
├── features/              # Feature-specific modules or domains
│   ├── auth/
│   │   ├── components/    # Auth-specific components
│   │   ├── pages/         # Auth pages (e.g., login, signup)
│   │   ├── hooks/         # Auth-related hooks
│   │   └── services/      # Auth API services
│   ├── dashboard/
│   │   ├── components/    # Dashboard-specific components
│   │   ├── pages/         # Dashboard pages
│   │   ├── hooks/         # Dashboard-related hooks
│   │   └── services/      # Dashboard API services
│   └── profile/
│       ├── components/
│       ├── pages/
│       ├── hooks/
│       └── services/
├── hooks/                 # Custom hooks used across the app
│   └── useFetch.ts
├── layouts/               # Layout components that wrap pages
│   └── MainLayout.tsx
├── pages/                 # Top-level pages or views
│   ├── Home.tsx
│   └── About.tsx
├── services/              # API services or business logic
│   ├── api.ts
│   └── userService.ts
├── store/                 # State management (e.g., Redux, Zustand)
│   ├── store.ts
│   └── slices/
├── styles/                # Global and component-specific styles
│   ├── globals.css
│   └── tailwind.css
├── utils/                 # Utility functions
│   └── formatDate.ts
├── App.tsx                # Main App component
├── main.tsx               # Entry point for React application
└── index.css              # Import Tailwind CSS and global styles
