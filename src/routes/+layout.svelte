<script>
	import { fly } from 'svelte/transition';
	import { page } from '$app/stores';
    import Header from "../lib/components/Header.svelte";

	const { children } = $props();

	const startTransition = () => {
		document.body.classList.add('page-transitioning');
	};

	const endTransition = () => {
		document.body.classList.remove('page-transitioning');
	};
</script>
<svelte:head>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap" rel="stylesheet">
</svelte:head>

<Header />

{#key $page.url}
	<main
		in:fly={{ x: -200, duration: 300, delay: 300 }}
		out:fly={{ x: 200, duration: 300 }}
		onintrostart={startTransition}
		onintroend={endTransition}
		onoutrostart={startTransition}
		onoutroend={endTransition}
	>
		{@render children()}
	</main>
{/key}

<style>
	:global(body) {
		width: 100%;
		min-height: 100vh;
		margin: 0;
		padding: 0;
		overflow: visible;
		font-family: Arial, sans-serif;
	}

	main {
		min-height: 100vh;
		width: 100%; 
		margin: auto;
		box-sizing: border-box;
	}
</style>