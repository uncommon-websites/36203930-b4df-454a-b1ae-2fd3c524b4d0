<script lang="ts">
  const stats = [
    {
      label: "100+ Brands Managed",
      desc: "Our leadership team has managed over 100 brands across agencies, aggregators, and their own FBA operations. We bring senior-level Amazon expertise without the need to build an in-house UK team."
    },
    {
      label: "Supplement & Wellness Focus",
      desc: "We specialize exclusively in regulated health categories, starting with supplements and wellness brands. This focus allows us to build deep category expertise, navigate complex UK regulations, and create repeatable playbooks that drive results."
    },
    {
      label: "UK Market Specialists",
      desc: "Based in the UK with deep local knowledge, we understand the nuances of Amazon UK, British consumer behavior, and the regulatory landscape. We're your local partner who speaks the language—literally and figuratively."
    },
    {
      label: "Performance-Based Model",
      desc: "We only make money when we successfully sell your products. By buying inventory upfront and taking on the operational risk, we create complete alignment around profitable, sustainable growth. Your success is our success."
    }
  ];
</script>

<section class="bg-white">
  <div class="max-w-[1600px] mx-auto px-6 md:px-12 py-32">
    <div class="mb-20">
      <p class="text-lg md:text-xl text-gray-500 max-w-2xl leading-relaxed">
        Why partner with eVolume? Here's what sets us apart in the crowded world of Amazon consultants and agencies.
      </p>
    </div>

    <div>
      {#each stats as stat}
        <div class="group flex flex-col md:flex-row md:items-start gap-6 md:gap-24 py-12 px-6 -mx-6 border-t border-gray-100 cursor-default hover:bg-gray-50 transition-all duration-300">
          <h3 class="text-2xl md:text-4xl font-medium text-gray-900 w-full md:w-2/5 shrink-0 group-hover:text-primary-600 transition-colors duration-300">{stat.label}</h3>
          <p class="text-base leading-relaxed text-gray-500">{stat.desc}</p>
        </div>
      {/each}
    </div>
  </div>
</section>
