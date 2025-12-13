<script lang="ts">
  const benefits = [
    {
      title: "No Internal Headcount",
      desc: "Get a complete UK Amazon team without hiring, training, or managing employees. We handle everything from compliance to customer service."
    },
    {
      title: "Zero Upfront Risk",
      desc: "We buy your inventory and only make money when products sell. No retainers, no consulting fees—just aligned incentives and shared success."
    },
    {
      title: "Regulatory Expertise",
      desc: "Navigate UK supplement regulations with confidence. We handle MHRA compliance, labeling, and all the complex paperwork so you stay compliant."
    }
  ];
</script>

<section class="py-24 px-6 md:px-12 bg-white">
  <div class="max-w-xl mb-16">
    <h3 class="text-lg font-bold mb-2">Focus on your brand, not UK operations.</h3>
    <p class="text-gray-500 text-sm leading-relaxed">
      Expanding to Amazon UK shouldn't mean building a local team or navigating unfamiliar regulations. We become your dedicated UK partner, handling every aspect of the channel so you can focus on what you do best—building great products.
    </p>
  </div>

  <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
    {#each benefits as benefit}
      <div>
        <div class="w-16 h-16 rounded-lg bg-gray-50 mb-4"></div>
        <h4 class="text-xs font-bold mb-1">{benefit.title}</h4>
        <p class="text-[10px] text-gray-500 leading-relaxed">{benefit.desc}</p>
      </div>
    {/each}
  </div>
</section>
