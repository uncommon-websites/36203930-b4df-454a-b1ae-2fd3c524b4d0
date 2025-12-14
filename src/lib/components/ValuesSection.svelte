<script lang="ts">
  import { Users, ShieldCheck, FileCheck } from 'lucide-svelte';

  const benefits = [
    {
      title: "No Internal Headcount",
      desc: "Get a complete UK Amazon team without hiring, training, or managing employees. We handle everything from compliance to customer service.",
      icon: Users
    },
    {
      title: "Zero Upfront Risk",
      desc: "We buy your inventory and only make money when products sell. No retainers, no consulting fees—just aligned incentives and shared success.",
      icon: ShieldCheck
    },
    {
      title: "Regulatory Expertise",
      desc: "Navigate UK supplement regulations with confidence. We handle MHRA compliance, labeling, and all the complex paperwork so you stay compliant.",
      icon: FileCheck
    }
  ];
</script>

<section id="why-us" class="bg-gray-50 scroll-mt-24">
  <div class="max-w-[1600px] mx-auto px-6 md:px-12 py-32">
  <!-- Header -->
  <div class="flex flex-col lg:flex-row lg:items-end lg:justify-between gap-6 mb-20">
    <div class="max-w-2xl">
      <p class="text-xs uppercase tracking-wider text-gray-400 font-medium mb-4">Why partner with us</p>
      <h2 class="text-3xl md:text-4xl lg:text-5xl font-medium leading-[1.15] tracking-tight text-black">
        Focus on your brand, <span class="text-gray-400">not UK operations.</span>
      </h2>
    </div>
    <p class="text-gray-500 text-sm leading-relaxed max-w-sm lg:text-right">
      We become your dedicated UK partner, handling every aspect of the channel so you can focus on building great products.
    </p>
  </div>

  <!-- Benefits grid -->
  <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
    {#each benefits as benefit, i}
      <div class="group relative bg-white rounded p-8">
        <!-- Number indicator -->
        <span class="absolute top-8 right-8 text-5xl font-medium text-gray-100 select-none">0{i + 1}</span>

        <!-- Icon -->
        <div class="w-11 h-11 rounded bg-black mb-6 flex items-center justify-center">
          <benefit.icon class="w-5 h-5 text-white" strokeWidth={1.5} />
        </div>

        <!-- Content -->
        <h4 class="text-base font-medium text-gray-900 mb-2">{benefit.title}</h4>
        <p class="text-sm text-gray-500 leading-relaxed">{benefit.desc}</p>
      </div>
    {/each}
  </div>
  </div>
</section>
