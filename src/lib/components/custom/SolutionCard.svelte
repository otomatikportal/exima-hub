<script lang="ts">
	import { ArrowRightIcon } from 'lucide-svelte';
	import * as Card from '$lib/components/ui/card/index.js';
	import * as Item from '$lib/components/ui/item/index.js';

	interface Props {
		icon: any;
		title: string;
		shortDescription: string;
		description: string;
		difficulty: {
			label: string;
			icon: any;
			color: string;
		};
	}

	const { icon: Icon, title, shortDescription, description, difficulty } = $props();
	const { icon: DifficultyIcon, label: difficultyLabel, color: difficultyColor } = difficulty;
</script>

<Card.Root
	class="group flex cursor-pointer flex-col transition-all hover:scale-[1.03] hover:shadow-lg"
>
	<Card.Header class="flex min-h-[64px] items-center gap-3">
		<span class="flex-shrink-0"><Icon class="h-7 w-7 text-primary" /></span>
		<div class="flex flex-1 flex-col">
			<Card.Title class="text-lg font-semibold">{title}</Card.Title>
			<Card.Description class="text-sm text-muted-foreground">
				{shortDescription}
			</Card.Description>
		</div>
		<ArrowRightIcon
			class="h-7 w-7 flex-shrink-0 text-muted-foreground opacity-100 transition-opacity md:opacity-0 md:group-hover:opacity-100"
		/>
	</Card.Header>
	<Card.Content class="flex-1">
		<p>{@html description}</p>
	</Card.Content>
	<Card.Footer class="mt-auto">
		<Item.Root variant="outline" size="sm" class="w-full">
			<Item.Media>
				<DifficultyIcon class={`h-4 w-4 ${difficultyColor}`} />
			</Item.Media>
			<Item.Content>
				<Item.Title class="text-sm">Derinlik: {difficultyLabel}</Item.Title>
			</Item.Content>
		</Item.Root>
	</Card.Footer>
</Card.Root>
