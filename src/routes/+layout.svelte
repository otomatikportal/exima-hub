<script lang="ts">
	import '../app.css';
	import favicon from '$lib/assets/favicon.ico';
	import EximaNavigationMenu from '$lib/components/custom/EximaNavigationMenu.svelte';
	import { ModeWatcher } from 'mode-watcher';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<ModeWatcher/>
<!-- Responsive Landing Page Layout Blueprint -->
<div class="flex min-h-screen flex-col">
	<!-- Header -->
	<header style="box-shadow: 0 1px 8px 0 rgba(0,0,0,0.4);">
		<EximaNavigationMenu></EximaNavigationMenu>
	</header>
	{@render children?.()}
</div>
