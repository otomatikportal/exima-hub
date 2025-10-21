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
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<ModeWatcher />
<!-- Responsive Landing Page Layout Blueprint -->
<div class="flex flex-col min-h-screen relative">
    <!-- Paper texture overlay -->
    <div 
        class="fixed inset-0 pointer-events-none opacity-[0.15] dark:opacity-[0.08] z-50"
        style="background-image: url('data:image/svg+xml,%3Csvg xmlns=%22http://www.w3.org/2000/svg%22 width=%22600%22 height=%22600%22%3E%3Cfilter id=%22noise%22%3E%3CfeTurbulence type=%22fractalNoise%22 baseFrequency=%220.65%22 numOctaves=%224%22 /%3E%3C/filter%3E%3Crect width=%22100%25%22 height=%22100%25%22 filter=%22url(%23noise)%22 /%3E%3C/svg%3E'); background-size: 600px 600px;"
    ></div>
    
    <!-- Header -->
    <header
        style="box-shadow: 0 1px 8px 0 rgba(0,0,0,0.4);"
        class="flex items-center justify-between px-4"
    >
        <EximaNavigationMenu />
        <Button onclick={toggleMode} variant="outline" size="icon" class="hidden md:inline-flex cursor-pointer">
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
<main
    class="flex-1 flex flex-col"
    style="box-shadow: 0 8px 8px -8px rgba(0,0,0,0.4);"
>
    {@render children?.()}
</main>
    <footer
        class="w-full py-6 px-4 text-center text-sm"
    >
        Made by Exima &copy; {new Date().getFullYear()}
    </footer>
</div>
