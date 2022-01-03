<script context="module">
  // Module script runs before page load

  export const load = async ({ fetch }) => {
    const res = await fetch('/posts.json')

    if (res.ok) {
      const {posts} = await res.json()

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
</script>

<h1>SvelteKit DaisyUI graphcms blog</h1>

<pre>{JSON.stringify(posts, null, 2)}</pre>
