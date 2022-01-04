<script context="module">
  // const slug = req.params.slug
  export const load = async ({ fetch, params }) => {

    const {slug} = params

    const res = await fetch(`/pages/${slug}.json`)

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
  export let page

</script>

<svelte:head>
  <title>{title}</title>
</svelte:head>


<!-- <pre>{JSON.stringify(page, null, 2)}</pre> -->
