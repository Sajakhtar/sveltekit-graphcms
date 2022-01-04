<script>
	import '../app.css';
  import Nav from '$lib/nav.svelte'
</script>

<!-- global layout -->

<Nav />

<main class="container max-w-xl mx-auto px-4">
  <!-- content slots in -->
  <slot />
</main>
