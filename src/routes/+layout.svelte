<script lang="ts">
	import Mynavbar from '$lib/components/layout/Mynavbar.svelte';
	import '../app.css';

	let { children } = $props();
</script>

<Mynavbar />

{@render children()}

