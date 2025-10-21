<script lang="ts">
	import '../app.css';
	import favicon from '$lib/assets/favicon.ico';
	import EximaNavigationMenu from '$lib/components/custom/EximaNavigationMenu.svelte';
	import { ModeWatcher } from 'mode-watcher';
	import Button from '$lib/components/ui/button/button.svelte';
	import SunIcon from '@lucide/svelte/icons/sun';
	import MoonIcon from '@lucide/svelte/icons/moon';
	import { toggleMode } from 'mode-watcher';

	let { children } = $props();

	import { onMount } from 'svelte';

	let userLang;
	let prefersDark;

	onMount(() => {
		userLang = navigator.language;
		prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
	});
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<ModeWatcher />
<!-- Responsive Landing Page Layout Blueprint -->
<div class="relative flex min-h-screen flex-col">
	<!-- Header -->
	<header
		style="box-shadow: 0 1px 8px 0 rgba(0,0,0,0.4);"
		class="sticky top-0 z-50 flex items-center justify-between px-4 bg-background"
	>
		<EximaNavigationMenu />
		<Button
			onclick={toggleMode}
			variant="outline"
			size="icon"
			class="hidden cursor-pointer md:inline-flex"
		>
			<SunIcon
				class="h-[1.2rem] w-[1.2rem] scale-100 rotate-0 !transition-all dark:scale-0 dark:-rotate-90"
			/>
			<MoonIcon
				class="absolute h-[1.2rem] w-[1.2rem] scale-0 rotate-90 !transition-all dark:scale-100 dark:rotate-0"
			/>
			<span class="sr-only">Toggle theme</span>
		</Button>
	</header>
	<!-- Main content grows to fill remaining space -->
	<main class="flex flex-1 flex-col" style="box-shadow: 0 8px 8px -8px rgba(0,0,0,0.4);">
		{@render children?.()}
	</main>
	<footer class="w-full px-4 py-6 text-center text-sm">
		Made by Exima &copy; {new Date().getFullYear()}
	</footer>
</div>
