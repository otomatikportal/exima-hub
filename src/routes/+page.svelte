<script lang="ts">
	import {
		ChevronDownIcon,
		BuildingIcon,
		FileTextIcon,
		MessageSquareIcon,
		ShoppingCartIcon,
		CircleIcon,
		CircleDotIcon,
		ZapIcon,
		FlameIcon
	} from 'lucide-svelte';
	import fullLogoLight from '$lib/assets/full-logo-light.png';
	import fullLogoDark from '$lib/assets/full-logo-dark.png';
	import * as Select from '$lib/components/ui/select/index.js';
	import { Input } from '$lib/components/ui/input/index.js';
	import SolutionCard from '$lib/components/custom/SolutionCard.svelte';

	const roles = [
		{ value: 'salesperson', label: 'Satış yetkilisiyim' },
		{ value: 'purchasing', label: 'Satın alma yetkilisiyim' },
		{ value: 'worker', label: 'İşçiyim' },
		{ value: 'executive', label: 'Yöneticiyim' },
		{ value: 'owner', label: 'Sahibiyim' },
		{ value: 'chief_of_staff', label: 'Personel Şefiyim' },
		{ value: 'technician', label: 'Teknisyenim' },
		{ value: 'hr', label: 'İK Yetkilisiyim' }
	];

	const solutions = [
    {
        icon: BuildingIcon,
        title: 'Temel Tanıtım',
        shortDescription: 'Firmanıza dijital kimlik kazandıralım',
        description: 'Kurumsal kimliğinizi ve temel bilgilerinizi <span class="font-semibold text-primary">öne çıkaran bir web sitesi</span> oluşturalım. Bu süreçte ihtiyacınız olan dijital varlıkları <span class="font-semibold text-primary">iş birliği ile</span> oluşturup size teslim edelim',
        difficulty: {
            label: 'Başlangıç',
            icon: CircleIcon,
            color: 'text-green-500'
        }
    },
    {
        icon: FileTextIcon,
        title: 'Ürün ve Hizmet Tanıtımı',
        shortDescription: 'Dijital bir kataloğa geçiş yapın',
        description: 'Bu süreçte sizinle <span class="font-semibold text-primary">iş birliği içerisinde</span> ürün kategorizasyonunuzu ve isimlendirmenizi gerçekleştirelim',
        difficulty: {
            label: 'Orta',
            icon: CircleDotIcon,
            color: 'text-yellow-500'
        }
    },
    {
        icon: MessageSquareIcon,
        title: 'İletişim Dönüşümü',
        shortDescription: 'Ziyaretçilerinizi müşteriye dönüştürün',
        description: 'Ziyaretçiler, ilgilendikleri ürün veya hizmet için <span class="font-semibold text-primary">kolayca iletişime geçsin</span> ve sizden bilgi/fiyat alacakları bir yolculuk yapsınlar',
        difficulty: {
            label: 'İleri',
            icon: ZapIcon,
            color: 'text-orange-500'
        }
    },
    {
        icon: ShoppingCartIcon,
        title: 'E-ticaret',
        shortDescription: 'Satış dönüşümü',
        description: 'Web siteniz üzerinden <span class="font-semibold text-primary">doğrudan ürün veya hizmet satışı</span> yapın.',
        difficulty: {
            label: 'Uzman',
            icon: FlameIcon,
            color: 'text-red-500'
        }
    }
];

	let roleValue = $state('');

	const triggerContent = $derived(roles.find((r) => r.value === roleValue)?.label);

	function scrollToNextSection() {
		const nextSection = document.getElementById('next-section');
		if (nextSection) {
			nextSection.scrollIntoView({ behavior: 'smooth' });
		}
	}
</script>

<section class="flex min-h-[100svh] flex-col items-center justify-center px-4 py-20 text-center">
	<!-- Logo that changes based on theme -->
	<img src={fullLogoDark} alt="Exima Logo" class="mb-8 h-24 md:h-32 dark:hidden" />
	<img src={fullLogoLight} alt="Exima Logo" class="mb-8 hidden h-24 md:h-32 dark:block" />

	<h1
		class="mb-6 text-4xl font-bold tracking-tight md:text-6xl"
		style="letter-spacing: var(--tracking-tight);"
	>
		Gerçek sorunlara <span class="text-primary">gerçek çözümler</span>.
	</h1>
	<p class="mb-8 max-w-2xl text-lg md:text-xl" style="color: var(--muted-foreground);">
		İşinizin farkında ve özelleştirilmiş ve <span class="font-bold text-primary">işlevsel</span> web
		siteleri oluşturuyoruz.
	</p>
	<p>Nasıl mı?</p>
	<button
		class="mt-12 animate-bounce cursor-pointer rounded-full bg-primary p-3 text-primary-foreground shadow transition hover:bg-primary/90"
		aria-label="Sonraki bölüme geç"
		onclick={scrollToNextSection}
	>
		<ChevronDownIcon class="h-8 w-8" />
	</button>
</section>

<section id="next-section" class="flex min-h-screen flex-col items-center px-5 py-20 md:px-50">
	<!-- Next section content goes here -->
	<h2 class="mb-4 text-2xl font-semibold md:text-4xl">Öncelikle, seni tanımak istiyoruz</h2>
	<div class="mb-4 text-2xl md:text-4xl w-full md:w-full md:px-100">
		<div class="flex flex-col gap-2 text-base md:flex-row md:items-center md:gap-5 md:text-2xl">
			<Input class="w-full" placeholder="Firma ismi" />

			{roleValue === 'owner' ? ' firmasının ' : ' firmasında '}

			<Select.Root type="single" name="role" bind:value={roleValue}>
				<Select.Trigger class="w-full">
					{triggerContent}
				</Select.Trigger>
				<Select.Content>
					<Select.Group>
						<Select.Label>Roller</Select.Label>
						{#each roles as role (role.value)}
							<Select.Item value={role.value} label={role.label}>
								{role.label}
							</Select.Item>
						{/each}
					</Select.Group>
				</Select.Content>
			</Select.Root>
		</div>
	</div>
	<h2 class="mt-5 mb-4 text-2xl font-semibold md:mt-20 md:text-4xl">
		Aradığınız çözümün kapsamı nedir?
	</h2>

	<div class="grid w-full max-w-3xl gap-4 md:grid-cols-2">
		{#each solutions as solution (solution.title)}
			<SolutionCard {...solution} />
		{/each}
	</div>
</section>
