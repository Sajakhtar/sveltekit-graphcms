<script context="module">
  // Module script runs before page load

  export const load = async ({ fetch }) => {
    const res = await fetch('/posts.json')

    if (res.ok) {
      const { posts } = await res.json()

      return {
        props: {
          posts
        }
      }
    }
  }

</script>

<script>
  // receive props from module script
  export let posts
  // console.log(posts)
</script>

<svelte:head>
  <title>SvelteKit DaisyUI graphcms blog</title>
</svelte:head>

<h1 class="text-center text-3xl mb-10 font-extrabold">SvelteKit DaisyUI graphcms blog</h1>

<!-- <pre>{JSON.stringify(posts, null, 2)}</pre> -->

{#each posts as { title, slug, excerpt, coverImage, tags, date} }
  <div class="card text-center shadow-2xl mb-20">
    <figure class="px-10 pt-10">
      <img src={coverImage.url} alt={`Cover image for ${title}`}>
    </figure>

    <div class="card-body">
      <h2 class="card-title">{title}</h2>
      <p>{excerpt}</p>
      <div class="flex justify-center mt-5 space-x-2">
        {#each tags as tag}
          <span class="badge badge-primary">{tag}</span>
        {/each}
      </div>

      <div class="card-actions justify-center">
        <a href={`/posts/${slug}`} class="btn btn-outline btn-primary btn-sm">Read &rArr;</a>
      </div>
    </div>
  </div>
{/each}
