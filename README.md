# nextjs-with-prettier

This is **my custom** [Next.js](https://nextjs.org/) project **starting point** bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/basic-features/font-optimization) to automatically optimize and load Inter, a custom Google Font.

## Manually adding prettier and additional utilities

Assuming you have a [Next.js](https://nextjs.org/) project with **eslint** and **tailwindcss** configured.

1. Add `prettier`.

    ```bash
    yarn add -D prettier eslint-config-prettier prettier-plugin-tailwindcss
    ```

2. Update `.eslintrc.json` file.

    Example:

    ```diff
    {
    - "extends": "next/core-web-vitals"
    + "extends": ["next/core-web-vitals", "prettier"]
    }
    ```

    Copypasta:

    ```json
    {
      "extends": ["next/core-web-vitals", "prettier"]
    }
    ```

3. Create a `.prettierrc.json` file.

    ```json
    {
      "singleQuote": true,
      "plugins": ["prettier-plugin-tailwindcss"]
    }
    ```

4. Configure scripts.

    Example:

    ```diff
      "scripts": {
        ...
    +   "format": "prettier --check --ignore-path .gitignore .",
    +   "format:fix": "prettier --write --ignore-path .gitignore ."
      }
    ```

    Copypasta:

    ```json
        "format": "prettier --check --ignore-path .gitignore .",  
        "format:fix": "prettier --write --ignore-path .gitignore ."
    ```

5. Add Twailwind CSS, PostCSS, Autoprefixer and utilities.

    ```bash
    yarn add -D tailwindcss postcss autoprefixer class-variance-authority clsx tailwind-merge
    ```

6. In the `tailwind.config.ts` file, find the `content` property and make sure it is aligned with you project paths to all your template files. For example:

    ```ts
    import type { Config } from 'tailwindcss';

    const config: Config = {
      content: [
        "./pages/**/*.{js,ts,jsx,tsx}",  
        "./components/**/*.{js,ts,jsx,tsx}",
        "./app/**/*.{js,ts,jsx,tsx}",  

        // Or if using `src` directory:
        './src/pages/**/*.{js,ts,jsx,tsx,mdx}',
        './src/components/**/*.{js,ts,jsx,tsx,mdx}',
        './src/app/**/*.{js,ts,jsx,tsx,mdx}',
      ],
      theme: {
        extend: {
          backgroundImage: {
            'gradient-radial': 'radial-gradient(var(--tw-gradient-stops))',
            'gradient-conic':
              'conic-gradient(from 180deg at 50% 50%, var(--tw-gradient-stops))',
          },
        },
      },
      plugins: [],
    };
    export default config;
    ```
