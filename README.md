# Tanstack start Sitemap Plugin

A Tanstack start plugin that generates a `sitemap.xml` file during the build process by reading a route tree file and extracting the routes. This plugin makes it easy to maintain your website’s sitemap based on your application's routing configuration.

## Features

- **Automatic Sitemap Generation:** Automatically creates a `sitemap.xml` during the build process.
- **Customizable Options:** Configure per-route settings such as `changefreq`, `priority`, and `lastmod`.

## Installation

### Using pnpm 

```bash
pnpm add -D tanstack-start-sitemap
```

## Usage

Add the plugin to your tanstack start configuration `app.config.ts`:

```ts
// app.config.ts
import { defineConfig } from 'vite';
import { sitemapPlugin } from './plugins/vite-sitemap-plugin';

export default defineConfig({
    vite: {
    plugins: [
      tsConfigPaths({
        projects: ["./tsconfig.json"],
      }),
       sitemapPlugin({
        hostname: 'https://example.com'
    }),
    ],
  },

});
```

## Plugin Options

| Option               | Type                                                            | Default                    | Description                                                                                     |
| -------------------- | --------------------------------------------------------------- | -------------------------- | ----------------------------------------------------------------------------------------------- |
| `hostname`           | `string`                                                        | **Required**               | The base URL of your site (e.g., `https://example.com`).                                        |
| `routeTreePath`      | `string`                                                        | `'app/routeTree.gen.ts'`   | The path to your route tree file. The plugin will search several possible paths to locate it.   |
| `routes`             | `{ [key: string]: { changefreq?: string; priority?: number; lastmod?: string } }` | `{}`                       | Per-route configuration that allows overriding default settings for specific routes.           |
| `defaultChangefreq`  | `'always' | 'hourly' | 'daily' | 'weekly' | 'monthly' | 'yearly' | 'never'` | `'weekly'`                | The default change frequency applied to routes that don't have an override.                     |
| `defaultPriority`    | `number`                                                        | `0.5`                      | The default priority applied to routes that don't have an override.                            |

## Troubleshooting

- **Route Tree File Not Found:**  
  Ensure that the path provided in `routeTreePath` is correct or that your file exists in one of the expected locations.
  
## License

This project is licensed under the [MIT License](LICENSE).
