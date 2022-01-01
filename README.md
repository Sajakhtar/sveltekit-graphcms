# create-svelte

Everything you need to build a Svelte project, powered by [`create-svelte`](https://github.com/sveltejs/kit/tree/master/packages/create-svelte);

This project is based on the following tutorial:

[SvelteKit Crash Course w/ Tailwind CSS and DaisyUI, GraphQL and dynamic routes](https://www.youtube.com/watch?v=zH2qG9YwN3s&list=PLGi_uHe_v04AuMoPAtBN3ULy7zhFILKRQ&index=3)

## Creating a project

If you're seeing this, you've probably already done this step. Congrats!

```bash
# create a new project in the current directory
npm init svelte@next

# create a new project in my-app
npm init svelte@next my-app
```

> Note: the `@next` is temporary

### Tailwind CSS


### GraphCMS

Signup/ login to [graphcms](https://graphcms.com/)

Select the blog starter template and create a new project.

Keep `include template content` checked.

Select a suitable CDN node location and create project.

Select the free Community plan.


## Developing

Once you've created a project and installed dependencies with `npm install` (or `pnpm install` or `yarn`), start a development server:

```bash
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

## Building

Before creating a production version of your app, install an [adapter](https://kit.svelte.dev/docs#adapters) for your target environment. Then:

```bash
npm run build
```

> You can preview the built app with `npm run preview`, regardless of whether you installed an adapter. This should _not_ be used to serve your app in production.
