<script lang="ts">
	import { goto } from '$app/navigation';
	import EximaNavigationMenu from '$lib/components/custom/EximaNavigationMenu.svelte';
</script>



<!-- Hero Section -->
<section class="flex flex-1 flex-col items-center justify-center bg-gray-50 px-4 py-16 text-center">
	<h1 class="mb-4 text-3xl font-extrabold md:text-5xl">Landing Page Headline</h1>
	<p class="mb-8 text-lg md:text-xl">Short description goes here.</p>
	<div class="flex flex-col justify-center gap-4 sm:flex-row">
		<a href="#" class="rounded bg-blue-600 px-6 py-3 text-white">Primary Action</a>
		<a href="#" class="rounded border border-blue-600 px-6 py-3 text-blue-600">Secondary Action</a>
	</div>
</section>

<!-- Features Section -->
<section class="bg-white px-4 py-16">
	<div class="mx-auto grid max-w-5xl grid-cols-1 gap-8 md:grid-cols-3">
		<div class="flex flex-col items-center text-center">
			<div class="mb-4 h-12 w-12 rounded-full bg-gray-200"></div>
			<h2 class="mb-2 font-semibold">Feature One</h2>
			<p class="text-gray-600">Description of feature one.</p>
		</div>
		<div class="flex flex-col items-center text-center">
			<div class="mb-4 h-12 w-12 rounded-full bg-gray-200"></div>
			<h2 class="mb-2 font-semibold">Feature Two</h2>
			<p class="text-gray-600">Description of feature two.</p>
		</div>
		<div class="flex flex-col items-center text-center">
			<div class="mb-4 h-12 w-12 rounded-full bg-gray-200"></div>
			<h2 class="mb-2 font-semibold">Feature Three</h2>
			<p class="text-gray-600">Description of feature three.</p>
		</div>
	</div>
</section>

<!-- Footer -->
<footer class="w-full bg-gray-100 px-4 py-6 text-center text-gray-500">
	&copy; 2025 Your Company. All rights reserved.
</footer>
