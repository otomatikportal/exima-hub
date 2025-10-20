<script lang="ts">
	import * as NavigationMenu from '$lib/components/ui/navigation-menu/index.js';
	import { navigationMenuTriggerStyle } from '$lib/components/ui/navigation-menu/navigation-menu-trigger.svelte';
	import Button from '../ui/button/button.svelte';
	import SunIcon from '@lucide/svelte/icons/sun';
	import MoonIcon from '@lucide/svelte/icons/moon';
	import { toggleMode } from 'mode-watcher';

	// State for mobile sidebar visibility
	let isSidebarOpen = $state(false);

	// Toggle sidebar open/closed
	function toggleSidebar() {
		isSidebarOpen = !isSidebarOpen;
	}

	// Close sidebar (used when clicking overlay or links)
	function closeSidebar() {
		isSidebarOpen = false;
	}

	// Shared link style classes
	const mobileLinkClasses = 'w-full justify-start';

	// Navigation items configuration
	const navItems = [
		{ href: '/docs', label: 'Docs' },
		{ href: '/about', label: 'About' },
		{ href: '/contact', label: 'Contact' }
	];
</script>

<!-- Hamburger Menu Button (Mobile Only) -->
<button
	class="md:hidden fixed top-4 right-4 z-50 p-2 bg-background border rounded-md shadow-sm hover:bg-accent"
	onclick={toggleSidebar}
	aria-label="Toggle navigation menu"
>
	<svg
		class="w-6 h-6"
		fill="none"
		stroke="currentColor"
		viewBox="0 0 24 24"
		aria-hidden="true"
	>
		{#if isSidebarOpen}
			<!-- Close icon (X) -->
			<path
				stroke-linecap="round"
				stroke-linejoin="round"
				stroke-width="2"
				d="M6 18L18 6M6 6l12 12"
			/>
		{:else}
			<!-- Menu icon (hamburger) -->
			<path
				stroke-linecap="round"
				stroke-linejoin="round"
				stroke-width="2"
				d="M4 6h16M4 12h16M4 18h16"
			/>
		{/if}
	</svg>
</button>

<!-- Backdrop Overlay (Mobile Only) -->
<button
	class="md:hidden fixed inset-0 bg-black z-40 transition-opacity duration-300 ease-in-out {isSidebarOpen ? 'opacity-50 pointer-events-auto' : 'opacity-0 pointer-events-none'}"
	onclick={closeSidebar}
	aria-label="Close navigation menu"
></button>

<!-- Navigation Sidebar/Menu -->
<NavigationMenu.Root
	class="
		fixed md:relative
		top-0 right-0
		h-full md:h-auto
		w-64 md:w-auto
		bg-background md:bg-transparent
		border-l md:border-l-0
		p-4 md:p-2
		transition-transform duration-300 ease-in-out
		z-40
		{isSidebarOpen ? 'translate-x-0' : 'translate-x-full md:translate-x-0'}
	"
	viewport={false}
>
	<div class="flex flex-col md:flex-row md:items-center md:justify-between w-full gap-4">
		<!-- Navigation Links List -->
		<NavigationMenu.List class="flex-col md:flex-row items-start md:items-center gap-2 md:gap-1">
			{#each navItems as item}
				<NavigationMenu.Item>
					<NavigationMenu.Link>
						{#snippet child()}
							<a
								href={item.href}
								class="{navigationMenuTriggerStyle()} {mobileLinkClasses}"
								onclick={closeSidebar}
							>
								{item.label}
							</a>
						{/snippet}
					</NavigationMenu.Link>
				</NavigationMenu.Item>
			{/each}
		</NavigationMenu.List>

		<!-- Actions Section -->
		<div class="flex flex-col md:flex-row items-stretch md:items-center gap-2">
			<!-- Call-to-Action Button -->
			<Button class="w-full md:w-auto">Beraber çözelim</Button>

			<!-- Theme Toggle Button -->
			<Button onclick={toggleMode} variant="outline" size="icon">
				<SunIcon
					class="h-[1.2rem] w-[1.2rem] rotate-0 scale-100 !transition-all dark:-rotate-90 dark:scale-0"
				/>
				<MoonIcon
					class="absolute h-[1.2rem] w-[1.2rem] rotate-90 scale-0 !transition-all dark:rotate-0 dark:scale-100"
				/>
				<span class="sr-only">Toggle theme</span>
			</Button>
		</div>
	</div>
</NavigationMenu.Root>
