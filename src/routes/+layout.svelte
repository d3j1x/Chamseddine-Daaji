<script lang="ts">
	import Footer from '$lib/components/layout/Footer.svelte';
	import Mynavbar from '$lib/components/layout/Mynavbar.svelte';
	import MySecondarynavbar from '$lib/components/layout/MySecondarynavbar.svelte';
	import '../app.css';
	import { page } from '$app/stores';

	let { children } = $props();
</script>

<svelte:head>
	<!-- Charset & Viewport -->
	<meta charset="utf-8" />
	<meta name="viewport" content="width=device-width, initial-scale=1.0" />
	<meta name="theme-color" content="#0f172a" />

	<!-- Favicon & Icons -->
	<link rel="icon" href="/favicon.ico" />
	<link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png" />
	<link rel="manifest" href="/site.webmanifest" />

	<!-- Open Graph Defaults -->
	<meta property="og:site_name" content="شمس الدين دعجي" />
	<meta property="og:type" content="website" />
	<meta property="og:locale" content="ar_AR" />
	<meta property="og:image" content="https://chamseddinedaaji.tn/og-image.png" />

	<!-- Twitter / X Card Defaults -->
	<meta name="twitter:card" content="summary_large_image" />
	<meta name="twitter:title" content="شمس الدين دعجي | رائد أعمال ومصمم مشاريع رقمية" />
	<meta name="twitter:description" content="أكتشف أعمال ومشاريع شمس الدين دعجي في مجال التصميم والتطوير الرقمي." />
	<meta name="twitter:image" content="https://chamseddinedaaji.tn/og-image.png" />
	<meta name="twitter:site" content="@chamseddinedaji" />
	<meta name="twitter:creator" content="@chamseddinedaji" />


	<!-- Canonical (dynamic per page) -->
	<link rel="canonical" href={`https://chamseddinedaaji.tn${$page.url.pathname}`} />

	<!-- JSON-LD Structured Data -->
	<script type="application/ld+json">
		{
			"@context": "https://schema.org",
			"@type": "Person",
			"name": "شمس الدين دعجي",
			"url": "https://chamseddinedaaji.tn/",
			"image": "https://chamseddinedaaji.tn/profile.png",
			"jobTitle": "رائد أعمال ومصمم مشاريع رقمية",
			"sameAs": [
				"https://linkedin.com/in/chamseddinedaaji",
				"https://x.com/chamseddinedaji",
				"https://github.com/d3j1x"
			]
		}
	</script>
</svelte:head>


<Mynavbar />

<MySecondarynavbar />

{@render children()}

<Footer />

