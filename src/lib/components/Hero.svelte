<script lang="ts">
  // Trusted by leading supplement and wellness brands
  const categories = [
    "Supplements",
    "Wellness",
    "Vitamins",
    "Sports Nutrition",
    "Natural Health"
  ];
</script>

<section class="relative min-h-screen flex flex-col justify-end pb-20 px-6 md:px-12 bg-gradient-to-b from-black via-gray-900 to-white text-[#1a1a1a]">
  <!-- Gradient overlay/background handling -->
  <div class="absolute inset-0 z-[-1] bg-[linear-gradient(180deg,#000_0%,#1a1a1a_30%,#404040_60%,#fff_100%)]"></div>

  <div class="max-w-4xl mb-32 pt-40">
    <h1 class="text-3xl md:text-5xl font-medium leading-[1.15] tracking-tight text-white">
      We run your entire <span class="text-primary-400">Amazon UK channel</span> end-to-end. <span class="text-gray-400">From compliance and catalog clean-up to listings, advertising and ongoing management—so you can focus on building your brand.</span>
    </h1>
  </div>

  <div class="border-t border-gray-400 pt-8 flex flex-wrap gap-8 md:gap-16 items-center opacity-50">
    <div class="text-xs text-gray-500 font-medium uppercase tracking-wider">Specializing in</div>
    {#each categories as category}
      <div class="h-8 flex items-center justify-center font-medium text-sm text-gray-600">{category}</div>
    {/each}
  </div>
</section>
