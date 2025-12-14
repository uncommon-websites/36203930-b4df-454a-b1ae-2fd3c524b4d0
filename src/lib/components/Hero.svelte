<script lang="ts">
  import AnimatedBackground from './AnimatedBackground.svelte';

  // Trusted by leading supplement and wellness brands
  const categories = [
    "Supplements",
    "Wellness",
    "Vitamins",
    "Sports Nutrition",
    "Natural Health"
  ];
</script>

<section class="relative min-h-screen flex flex-col justify-end overflow-hidden bg-black">
  <!-- Animated background -->
  <AnimatedBackground />

  <!-- Subtle overlay to improve text readability -->
  <div class="absolute inset-0 z-[1] bg-gradient-to-t from-black/80 via-black/40 to-transparent"></div>

  <div class="relative z-10 max-w-[1600px] mx-auto w-full px-6 md:px-12">
    <div class="max-w-4xl mb-12 pt-40">
      <h1 class="text-3xl md:text-5xl font-medium leading-[1.15] tracking-tight text-white">
        We run your entire <span class="text-primary-400">Amazon UK channel</span> end-to-end. <span class="text-gray-400">From compliance and catalog clean-up to listings, advertising and ongoing management—so you can focus on building your brand.</span>
      </h1>
    </div>

    <div class="pb-24 flex flex-wrap gap-8 md:gap-16 items-center">
      <div class="text-xs text-gray-500 font-medium uppercase tracking-wider">Specializing in</div>
      {#each categories as category}
        <div class="h-8 flex items-center justify-center font-medium text-sm text-gray-400">{category}</div>
      {/each}
    </div>
  </div>
</section>
