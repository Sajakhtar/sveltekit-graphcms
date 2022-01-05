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

Use [svelte-add]() utlity to install Tailwind CSS

```bash
npx svelte-add@latest tailwindcss
```

### GraphCMS

Signup/ login to [graphcms](https://graphcms.com/)

Select the blog starter template and create a new project.

Keep `include template content` checked.

Select a suitable CDN node location and create project.

Select the free Community plan.

#### API Endpoint

Navigate to `Settings` then `API Access` and copy the `Content API` endpoint into `.env`

```
GRAPHQL_ENDPOINT=https://#########.graphcms.com/v2/############
```

#### Pages

Graphcms has a `Pages` model for us to create content for standalone static pages.

Navigate to `Content` and then `Pages`. There is an existing page for `About`, but pages can be creted for static content such as FAQ or Products/ Services.

#### API Playground

Navigate to the `API Playground`

##### Create a query to fetch all posts:

```graphql
query Posts {
  posts {
    title
    slug
    date
    excerpt
    tags
    coverImage {
      url
    }
  }
}
```

Place query in a `get` request endpoint for `posts` and see the result in: http://localhost:3333/posts.json


##### Create a query to fetch a specific post:

```graphql
query Post($slug: String!) {
  post(where: {slug: $slug}) {
    title
    date
    tags
    author {
      name
      authorTitle: title
      picture {
        url(transformation:{image:{resize:{fit:clip, height:50, width:50}}})
      }
    }
    content {
      html
      markdown
      raw
      text
    }
    coverImage {
      url
    }
  }
}
```
Add `{"slug": "technical-seo-with-graphcms"}` in the Query Variables field before running the query.

GraphQL has ability to transform images on the URl itself.

Place query in a `get` request endpoint for a `post` (based on slug) and see the result in URI with a slug: http://localhost:3000/posts/technical-seo-with-graphcms.json

##### Create a query to fetch all pages under the Pages model

The `Pages` model contains static pages such as About, FAQ, Services.

```graphql
query Pages {
  pages {
    title
    slug
    content {
      html
    }
  }
}
```
Place query in a `get` request endpoint for `pages` and see the result in: http://localhost:3000/pages.json

##### Create a query to fetch a specifc page


```graphql
query Pages {
  pages {
    title
    slug
    content {
      html
    }
  }
}
```
Add `{"slug": "faq"}` in the Query Variables field before running the query.

Place query in a `get` request endpoint for a `page` (based on slug) and see the result in URI with a slug: http://localhost:3000/pages/faq.json

### Dependancies

Install the following dev dependancies:

```bash
npm i -D graphql-request graphql env-cmd daisyui @tailwindcss/typography theme-change

# or

npm install graphql-request --save-dev
npm install graphql --save-dev
npm install env-cmd --save-dev
npm install daisyui --save-dev
npm install @tailwindcss/typography --save-dev
npm install theme-change --save-dev
```


## Developing

Once you've created a project and installed dependencies with `npm install` (or `pnpm install` or `yarn`), start a development server:

```bash
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open

# Specify port
npm run dev -- --open --port 3333
```

Update the dev script in `package.json` to access the environment variables:

```json
"dev": "env-cmd svelte-kit dev"
```

## Building

Before creating a production version of your app, install an [adapter](https://kit.svelte.dev/docs#adapters) for your target environment. Then:

```bash
npm run build
```

> You can preview the built app with `npm run preview`, regardless of whether you installed an adapter. This should _not_ be used to serve your app in production.
