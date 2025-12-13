<script lang="ts">
  const cards = [
    {
      title: "We Don't Just Advise...",
      subtitle: "We Execute End-to-End.",
      image: "/generated/image-professional-business-meeting-with-suppl-1765613404044-0.webp"
    },
    {
      title: "We Don't Take Retainers...",
      subtitle: "We Only Win When You Win.",
      image: "/generated/image-analytics-dashboard-showing-amazon-adver-1765613413820-4.webp"
    },
    {
      title: "We Don't Spread Thin...",
      subtitle: "We Build Deep Category Expertise.",
      image: "/generated/image-warehouse-shelves-stocked-with-supplemen-1765613406909-1.webp"
    }
  ];
</script>

<section class="py-24 px-6 md:px-12 bg-white">
  <div class="max-w-2xl mb-16">
    <p class="text-xl md:text-2xl leading-relaxed text-gray-800">
      We're not a traditional agency or marketplace consultant. We buy your inventory, run your entire UK channel, and only make money when we successfully sell your products. Full alignment, zero risk.
    </p>
  </div>

  <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
    {#each cards as card, i}
      <div class="group">
        <div class="aspect-[4/3] overflow-hidden rounded-lg mb-4 bg-gray-100">
          <img src={card.image} alt={card.title} class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-500" />
        </div>
        <h3 class="text-sm text-gray-500 mb-1">{card.title}</h3>
        <p class="text-sm font-bold">{card.subtitle}</p>
        
        <div class="flex justify-between mt-4 text-xs text-gray-400">
           <span>{String(i + 1).padStart(2, '0')}</span>
           <span>→</span>
        </div>
      </div>
    {/each}
  </div>
</section>
