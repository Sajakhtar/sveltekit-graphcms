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

</script>

<svelte:head>
  <title>{page.title}</title>
</svelte:head>

<!-- <pre>{JSON.stringify(page, null, 2)}</pre> -->

<!-- <h1 class="text-3xl font-semibold mb-5">{title}</h1> -->

<article div class="prose">
  <!-- Tailwind typography Prose styles the content  -->
  {@html page.content.html}
</article>
