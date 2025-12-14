<script lang="ts">
  import { onMount } from 'svelte';

  const cards = [
    {
      title: "We Don't Just Advise...",
      subtitle: "We Execute End-to-End.",
      image: "/generated/warehouse.png"
    },
    {
      title: "We Don't Take Retainers...",
      subtitle: "We Only Win When You Win.",
      image: "/generated/people-laptop.png"
    },
    {
      title: "We Don't Spread Thin...",
      subtitle: "We Build Deep Category Expertise.",
      image: "/generated/supplements.png"
    }
  ];

  let cardRefs: HTMLElement[] = [];
  let visibleCards = $state<boolean[]>([false, false, false]);

  onMount(() => {
    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          const index = cardRefs.indexOf(entry.target as HTMLElement);
          if (index !== -1 && entry.isIntersecting) {
            visibleCards[index] = true;
          }
        });
      },
      { threshold: 0.3 }
    );

    cardRefs.forEach((ref) => {
      if (ref) observer.observe(ref);
    });

    return () => observer.disconnect();
  });
</script>

<section class="bg-white">
  <div class="max-w-[1600px] mx-auto px-6 md:px-12 py-32">
  <div class="max-w-3xl mb-20">
    <p class="text-2xl md:text-3xl lg:text-4xl font-medium leading-[1.3] tracking-tight text-gray-900">
      We're not a traditional agency or marketplace consultant. <span class="text-gray-400">We buy your inventory, run your entire UK channel, and only make money when we successfully sell your products. Full alignment, zero risk.</span>
    </p>
  </div>

  <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
    {#each cards as card, i}
      <div class="group" bind:this={cardRefs[i]}>
        <div class="aspect-[4/3] overflow-hidden rounded mb-6 bg-gray-100">
          <img
            src={card.image}
            alt={card.title}
            class="w-full h-full object-cover transition-all duration-500 {visibleCards[i] ? 'grayscale-0' : 'grayscale'} md:grayscale md:group-hover:grayscale-0"
          />
        </div>
        <p class="text-base text-gray-400 mb-1">{card.title}</p>
        <h3 class="text-lg md:text-xl font-medium text-gray-900">{card.subtitle}</h3>

        <div class="flex justify-between mt-6 text-sm text-gray-300">
           <span>{String(i + 1).padStart(2, '0')}</span>
           <span>→</span>
        </div>
      </div>
    {/each}
  </div>
  </div>
</section>
