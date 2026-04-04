<script lang="ts">
	import favicon from '$lib/assets/favicon.ico'
	import Header from '$lib/components/feature/header/Header.svelte'
	import './layout.css'

	let { children } = $props()
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<Header />
{@render children()}
