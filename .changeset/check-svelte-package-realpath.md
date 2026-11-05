---
"@rsvelte/svelte-check": patch
---

fix(svelte-check): under pnpm, `class` values are type-checked again. The overlay listed the installed svelte's `svelte-html.d.ts` by its `node_modules` symlink path, which loaded a second `svelte/elements.d.ts` whose `import('clsx')` couldn't resolve; package-ID dedupe let that copy win, so `ClassValue` was `any` and `<span class={5}>` passed. The svelte package is now resolved to its realpath, as `require.resolve` does.
