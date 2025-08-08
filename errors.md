Run npm run build

> my-portfolio@0.0.1 build
> vite build

vite v7.1.1 building SSR bundle for production...
transforming...
✓ 177 modules transformed.
rendering chunks...
vite v7.1.1 building for production...
transforming...
✓ 147 modules transformed.
rendering chunks...
computing gzip size...
.svelte-kit/output/client/_app/version.json                        0.03 kB │ gzip:  0.05 kB
.svelte-kit/output/client/.vite/manifest.json                      3.30 kB │ gzip:  0.62 kB
.svelte-kit/output/client/_app/immutable/assets/0.CI87OW2L.css     0.40 kB │ gzip:  0.26 kB
.svelte-kit/output/client/_app/immutable/assets/3.COsfsIh2.css     0.44 kB │ gzip:  0.22 kB
.svelte-kit/output/client/_app/immutable/assets/2.C-ZL2b_i.css     1.09 kB │ gzip:  0.44 kB
.svelte-kit/output/client/_app/immutable/chunks/qL1LC61O.js        0.04 kB │ gzip:  0.06 kB
.svelte-kit/output/client/_app/immutable/chunks/DsnmJJEf.js        0.07 kB │ gzip:  0.08 kB
.svelte-kit/output/client/_app/immutable/entry/start.CUG0HSMI.js   0.08 kB │ gzip:  0.09 kB
.svelte-kit/output/client/_app/immutable/nodes/0.DzTMAikk.js       0.39 kB │ gzip:  0.29 kB
.svelte-kit/output/client/_app/immutable/nodes/3.Dmi7DH8e.js       0.45 kB │ gzip:  0.31 kB
.svelte-kit/output/client/_app/immutable/chunks/BDOMHziP.js        0.51 kB │ gzip:  0.33 kB
.svelte-kit/output/client/_app/immutable/nodes/1.DUig20hn.js       0.58 kB │ gzip:  0.36 kB
.svelte-kit/output/client/_app/immutable/nodes/2.UK5iO80n.js       0.99 kB │ gzip:  0.58 kB
.svelte-kit/output/client/_app/immutable/chunks/BS57mw6O.js        3.93 kB │ gzip:  2.08 kB
.svelte-kit/output/client/_app/immutable/entry/app.XvCoYqO3.js     7.49 kB │ gzip:  3.53 kB
.svelte-kit/output/client/_app/immutable/chunks/C79lt2y7.js       20.38 kB │ gzip:  8.13 kB
.svelte-kit/output/client/_app/immutable/chunks/BcCk3m3_.js       31.00 kB │ gzip: 12.23 kB
✓ built in 596ms
.svelte-kit/output/server/.vite/manifest.json                           3.06 kB
.svelte-kit/output/server/_app/immutable/assets/_layout.CI87OW2L.css    0.40 kB
.svelte-kit/output/server/_app/immutable/assets/_page.COsfsIh2.css      0.44 kB
.svelte-kit/output/server/_app/immutable/assets/_page.C-ZL2b_i.css      1.09 kB
.svelte-kit/output/server/chunks/false.js                               0.05 kB
.svelte-kit/output/server/entries/pages/_layout.svelte.js               0.27 kB
.svelte-kit/output/server/internal.js                                   0.36 kB
.svelte-kit/output/server/entries/pages/projects/_page.svelte.js        0.37 kB
.svelte-kit/output/server/chunks/escaping.js                            0.48 kB
.svelte-kit/output/server/chunks/environment.js                         0.58 kB
.svelte-kit/output/server/entries/pages/_page.svelte.js                 0.71 kB
.svelte-kit/output/server/chunks/equality.js                            1.23 kB
.svelte-kit/output/server/entries/fallbacks/error.svelte.js             1.33 kB
.svelte-kit/output/server/chunks/event-state.js                         2.87 kB
.svelte-kit/output/server/chunks/index.js                               5.24 kB
.svelte-kit/output/server/chunks/exports.js                             6.89 kB
.svelte-kit/output/server/remote-entry.js                              10.81 kB
.svelte-kit/output/server/chunks/internal.js                           59.56 kB
.svelte-kit/output/server/index.js                                    113.76 kB
✓ built in 2.38s

Run npm run preview to preview your production build locally.

> Using @sveltejs/adapter-static
  @sveltejs/adapter-static: all routes must be fully prerenderable, but found the following routes that are dynamic:
    - src/routes/
    - src/routes/projects
  
  You have the following options:
    - set the `fallback` option — see https://svelte.dev/docs/kit/single-page-apps#usage for more info.
    - add `export const prerender = true` to your root `+layout.js/.ts` or `+layout.server.js/.ts` file. This will try to prerender all pages.
    - add `export const prerender = true` to any `+server.js/ts` files that are not fetched by page `load` functions.
  
    - pass `strict: false` to `adapter-static` to ignore this error. Only do this if you are sure you don't need the routes in question in your final app, as they will be unavailable. See https://github.com/sveltejs/kit/tree/main/packages/adapter-static#strict for more info.
  
  If this doesn't help, you may need to use a different adapter. @sveltejs/adapter-static can only be used for sites that don't need a server for dynamic rendering, and can run on just a static file server.
  See https://svelte.dev/docs/kit/page-options#prerender for more details
error during build:
Error: Encountered dynamic routes
    at adapt (file:///home/runner/work/Beijing-corn87.github.io/Beijing-corn87.github.io/node_modules/@sveltejs/adapter-static/index.js:38:12)
    at adapt (file:///home/runner/work/Beijing-corn87.github.io/Beijing-corn87.github.io/node_modules/@sveltejs/kit/src/core/adapt/index.js:38:8)
    at finalise (file:///home/runner/work/Beijing-corn87.github.io/Beijing-corn87.github.io/node_modules/@sveltejs/kit/src/exports/vite/index.js:1159:13)
    at async Object.handler (file:///home/runner/work/Beijing-corn87.github.io/Beijing-corn87.github.io/node_modules/@sveltejs/kit/src/exports/vite/index.js:1189:5)
    at async PluginDriver.hookParallel (file:///home/runner/work/Beijing-corn87.github.io/Beijing-corn87.github.io/node_modules/rollup/dist/es/shared/node-entry.js:22255:17)
    at async Object.close (file:///home/runner/work/Beijing-corn87.github.io/Beijing-corn87.github.io/node_modules/rollup/dist/es/shared/node-entry.js:23271:13)
    at async buildEnvironment (file:///home/runner/work/Beijing-corn87.github.io/Beijing-corn87.github.io/node_modules/vite/dist/node/chunks/dep-eRCq8YxU.js:34367:15)
    at async Object.build (file:///home/runner/work/Beijing-corn87.github.io/Beijing-corn87.github.io/node_modules/vite/dist/node/chunks/dep-eRCq8YxU.js:34723:19)
    at async Object.buildApp (file:///home/runner/work/Beijing-corn87.github.io/Beijing-corn87.github.io/node_modules/vite/dist/node/chunks/dep-eRCq8YxU.js:34720:153)
    at async CAC.<anonymous> (file:///home/runner/work/Beijing-corn87.github.io/Beijing-corn87.github.io/node_modules/vite/dist/node/cli.js:642:3)
Error: Process completed with exit code 1.