<script lang="ts">
	import '../app.css';
	import favicon from '$lib/assets/favicon.ico';
	import EximaNavigationMenu from '$lib/components/custom/EximaNavigationMenu.svelte';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<!-- Responsive Landing Page Layout Blueprint -->
<div class="flex min-h-screen flex-col">
	<!-- Header -->
	<header class="shadow-lg bg-dark">
		<EximaNavigationMenu></EximaNavigationMenu>
	</header>
	{@render children?.()}
</div>
