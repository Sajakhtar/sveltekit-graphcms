<script context="module">
  // const slug = req.params.slug
  export const load = async ({ fetch, params }) => {

    const {slug} = params

    const res = await fetch(`/posts/${slug}.json`)

    if (res.ok) {
      const { post } = await res.json()

      return {
        props: {
          post
        }
      }
    }
  }
</script>


<script>
  export let post
</script>

<svelte:head>
  <title>{post.title}</title>
</svelte:head>


<pre>{JSON.stringify(post, null, 2)}</pre>
