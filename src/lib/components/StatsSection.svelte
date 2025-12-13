<script lang="ts">
  const stats = [
    {
      label: "100+ Brands Managed",
      desc: "Our leadership team has managed over 100 brands across agencies, aggregators, and their own FBA operations. We bring senior-level Amazon expertise without the need to build an in-house UK team.",
      img: "/generated/image-collection-of-diverse-supplement-and-wel-1765613754841-0.webp"
    },
    {
      label: "Supplement & Wellness Focus",
      desc: "We specialize exclusively in regulated health categories, starting with supplements and wellness brands. This focus allows us to build deep category expertise, navigate complex UK regulations, and create repeatable playbooks that drive results.",
      img: "/generated/image-supplement-bottles-and-wellness-products-1765613757131-1.webp"
    },
    {
      label: "UK Market Specialists",
      desc: "Based in the UK with deep local knowledge, we understand the nuances of Amazon UK, British consumer behavior, and the regulatory landscape. We're your local partner who speaks the language—literally and figuratively.",
      img: "/generated/image-uk-flag-subtly-integrated-with-amazon-ma-1765613759374-2.webp"
    },
    {
      label: "Performance-Based Model",
      desc: "We only make money when we successfully sell your products. By buying inventory upfront and taking on the operational risk, we create complete alignment around profitable, sustainable growth. Your success is our success.",
      img: "/generated/image-upward-trending-growth-chart-with-handsh-1765613761796-3.webp"
    }
  ];
</script>

<section class="py-24 px-6 md:px-12 bg-white border-t border-gray-100">
  <div class="mb-16">
    <p class="text-gray-500 max-w-xl">
      Why partner with eVolume? Here's what sets us apart in the crowded world of Amazon consultants and agencies.
    </p>
  </div>

  <div class="space-y-16">
    {#each stats as stat}
      <div class="flex flex-col md:flex-row md:items-start justify-between gap-8 border-b border-gray-100 pb-16 last:border-0">
        <h3 class="text-2xl md:text-4xl font-medium w-full md:w-1/3">{stat.label}</h3>
        <div class="w-full md:w-1/3">
           <p class="text-xs leading-relaxed text-gray-500">{stat.desc}</p>
        </div>
        <div class="w-full md:w-1/6 flex justify-end">
           <img src={stat.img} alt={stat.label} class="w-20 h-20 object-cover rounded bg-gray-100" />
        </div>
      </div>
    {/each}
  </div>
</section>
