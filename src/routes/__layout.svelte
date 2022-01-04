<script context="module">
  // Module script runs before page load

  export const load = async ({ fetch }) => {
    const res = await fetch('/pages.json')

    if (res.ok) {
      const { pages } = await res.json()

      return {
        props: {
          pages
        }
      }
    }
  }

</script>

<script>
	import '../app.css';
  import Nav from '$lib/nav.svelte'

  // props
  export let pages
</script>

<!-- global layout -->

<Nav {pages} />

<main class="container max-w-xl mx-auto px-4">
  <!-- content slots in -->
  <slot />
</main>
