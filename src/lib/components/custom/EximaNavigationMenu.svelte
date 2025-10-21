<script lang="ts">
	import * as NavigationMenu from '$lib/components/ui/navigation-menu/index.js';
	import { navigationMenuTriggerStyle } from '$lib/components/ui/navigation-menu/navigation-menu-trigger.svelte';
	import Button from '../ui/button/button.svelte';
	import { toggleMode } from 'mode-watcher';

	import { SunIcon, MoonIcon, FileTextIcon, InfoIcon, MailIcon, BookOpenIcon, HandshakeIcon } from 'lucide-svelte';

	let isSidebarOpen = $state(false);

	function toggleSidebar() {
		isSidebarOpen = !isSidebarOpen;
	}

	function closeSidebar() {
		isSidebarOpen = false;
	}

	const mobileLinkClasses = 'w-full justify-start';

	const navItems = [
		{ href: '/solutions', label: 'Çözümler', icon: FileTextIcon },
		{ href: '/about', label: 'Hakkında', icon: InfoIcon },
		{ href: '/contact', label: 'İletişim', icon: MailIcon },
		{ href: '/blog', label: 'Blog', icon: BookOpenIcon }
	];
</script>

<!-- Hamburger Menu Button (Mobile Only) -->
<button
	class="fixed top-4 right-4 z-50 rounded-md border bg-background p-2 shadow-sm hover:bg-accent md:hidden"
	onclick={toggleSidebar}
	aria-label="Toggle navigation menu"
>
	<svg class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" aria-hidden="true">
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
	class="fixed inset-0 z-40 bg-black transition-opacity duration-300 ease-in-out md:hidden {isSidebarOpen
		? 'pointer-events-auto opacity-50'
		: 'pointer-events-none opacity-0'}"
	onclick={closeSidebar}
	aria-label="Close navigation menu"
></button>

<!-- Navigation Sidebar/Menu -->
<NavigationMenu.Root
	class="
        fixed top-0
        right-0 z-40
        h-full w-64
        border-l bg-background
        p-4 transition-transform
        duration-300 ease-in-out
        md:relative md:h-auto
        md:w-auto md:border-l-0 md:bg-transparent
        md:p-2
        {isSidebarOpen ? 'translate-x-0' : 'translate-x-full md:translate-x-0'}
    "
	viewport={false}
>
	<div class="flex w-full flex-col gap-4 md:flex-row md:items-center md:justify-between">
		<!-- Navigation Links List -->
		<NavigationMenu.List class="flex-col items-start gap-2 md:flex-row md:items-center md:gap-1">
			{#each navItems as item}
				<NavigationMenu.Item>
					<NavigationMenu.Link>
						{#snippet child()}
							<a
								href={item.href}
								class="{navigationMenuTriggerStyle()} {mobileLinkClasses} flex items-center gap-2"
								onclick={closeSidebar}
							>
								<item.icon class="h-4 w-4" />
								{item.label}
							</a>
						{/snippet}
					</NavigationMenu.Link>
				</NavigationMenu.Item>
			{/each}
		</NavigationMenu.List>

		<!-- Actions Section -->
		<div class="flex flex-col items-stretch gap-2 md:flex-row md:items-center">
			<!-- Call-to-Action Button -->
			<Button class="flex w-full items-center gap-2 md:w-auto" href="/quotation-request">
				<HandshakeIcon class="h-4 w-4" />
				Beraber çözelim
			</Button>

			<!-- Theme Toggle Button (Mobile Only) -->
			<Button onclick={toggleMode} variant="outline" size="icon" class="md:hidden">
				<SunIcon
					class="h-[1.2rem] w-[1.2rem] scale-100 rotate-0 !transition-all dark:scale-0 dark:-rotate-90"
				/>
				<MoonIcon
					class="absolute h-[1.2rem] w-[1.2rem] scale-0 rotate-90 !transition-all dark:scale-100 dark:rotate-0"
				/>
				<span class="sr-only">Toggle theme</span>
			</Button>
		</div>
	</div></NavigationMenu.Root
>
