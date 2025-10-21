<script lang="ts">
    import { goto } from '$app/navigation';
    import EximaNavigationMenu from '$lib/components/custom/EximaNavigationMenu.svelte';
    import ChevronDownIcon from '@lucide/svelte/icons/chevron-down';
    import fullLogoLight from '$lib/assets/full-logo-light.png';
    import fullLogoDark from '$lib/assets/full-logo-dark.png';
    
    function scrollToNextSection() {
        const nextSection = document.getElementById('next-section');
        if (nextSection) {
            nextSection.scrollIntoView({ behavior: 'smooth' });
        }
    }
</script>

<section
    class="flex flex-col items-center justify-center text-center py-20 px-4 min-h-[100svh]"
>
    <!-- Logo that changes based on theme -->
    <img 
        src={fullLogoDark} 
        alt="Exima Logo" 
        class="mb-8 h-24 md:h-32 dark:hidden"
    />
    <img 
        src={fullLogoLight} 
        alt="Exima Logo" 
        class="mb-8 h-24 md:h-32 hidden dark:block"
    />
    
    <h1 class="text-4xl md:text-6xl font-bold mb-6 tracking-tight" style="letter-spacing: var(--tracking-tight);">
        Gerçek sorunlara <span class="text-primary">gerçek çözümler</span>.
    </h1>
    <p class="text-lg md:text-xl max-w-2xl mb-8" style="color: var(--muted-foreground);">
        İşinizin farkında ve özelleştirilmiş web tabanlı yazılım çözümleri sunuyoruz.
    </p>
    <p>
        Nasıl mı?
    </p>
    <button
        class="mt-12 animate-bounce cursor-pointer rounded-full bg-primary text-primary-foreground p-3 shadow hover:bg-primary/90 transition"
        aria-label="Sonraki bölüme geç"
        on:click={scrollToNextSection}
    >
        <ChevronDownIcon class="w-8 h-8" />
    </button>
</section>

<section id="next-section" class="py-20 px-4">
    <!-- Next section content goes here -->
    <h2 class="text-2xl font-semibold mb-4">Bir sonraki bölüm</h2>
    <p>
        Burada hizmetlerimiz veya detaylar hakkında bilgi vereceğim
    </p>
</section>