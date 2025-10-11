<script lang="ts">
	import Footer from '$lib/components/layout/Footer.svelte';
import Mynavbar from '$lib/components/layout/Mynavbar.svelte';
	import MySecondarynavbar from '$lib/components/layout/MySecondarynavbar.svelte';
	import '../app.css';

	let { children } = $props();
</script>

<Mynavbar />

<MySecondarynavbar />

{@render children()}

<Footer />

