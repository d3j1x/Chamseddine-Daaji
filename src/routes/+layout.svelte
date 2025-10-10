<script lang="ts">
	import Mynavbar from '$lib/components/layout/Mynavbar.svelte';
	import MySecondarynavbar from '$lib/components/layout/MySecondarynavbar.svelte';
	import '../app.css';

	let { children } = $props();
</script>

<Mynavbar />

<MySecondarynavbar />

{@render children()}

