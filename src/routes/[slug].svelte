<script context="module">

  export const load = async ({ fetch, params }) => {

    const {slug} = params

    const res = await fetch(`/pages/${slug}.json`)

    if (res.ok) {
      const { page } = await res.json()

      return {
        props: {
          page
        }
      }
    }
  }
</script>


<script>
  export let page

  const { title, content: { html } } = page
</script>

<svelte:head>
  <title>{title}</title>
</svelte:head>

<!-- <pre>{JSON.stringify(page, null, 2)}</pre> -->

<!-- <h1 class="text-3xl font-semibold mb-5">{title}</h1> -->

<article div class="prose">
  <!-- Tailwind typography Prose styles the content  -->
  {@html html}
</article>
