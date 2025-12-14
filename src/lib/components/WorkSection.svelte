<script lang="ts">
  import { Package, Shield, Sparkles, BarChart3, Megaphone, Store, Users } from 'lucide-svelte';

  const services = [
    {
      service: "Inventory Management",
      desc: "We buy your inventory upfront, removing cash flow concerns and aligning our success with yours.",
      icon: Package
    },
    {
      service: "Compliance & Regulations",
      desc: "Navigate UK supplement regulations with confidence. We handle MHRA compliance, labeling requirements, and all regulatory paperwork.",
      icon: Shield
    },
    {
      service: "Catalog Clean-Up",
      desc: "Eliminate rogue sellers and messy listings. We restore control of your brand presence on Amazon UK.",
      icon: Sparkles
    },
    {
      service: "Listing Optimization",
      desc: "Data-driven product listings that convert. From keyword research to A+ content, we make your products stand out.",
      icon: BarChart3
    },
    {
      service: "Amazon Advertising",
      desc: "Performance marketing that drives profitable growth. We optimize campaigns daily using advanced analytics and category expertise.",
      icon: Megaphone
    },
    {
      service: "Brand Store Design",
      desc: "Create a premium brand experience on Amazon with custom storefronts that tell your story and drive conversions.",
      icon: Store
    },
    {
      service: "Ongoing Management",
      desc: "Your dedicated UK team. We handle inventory, customer service, reviews, and continuous optimization—so you don't have to.",
      icon: Users
    }
  ];
</script>

<section id="services" class="bg-white scroll-mt-24">
  <div class="max-w-[1600px] mx-auto px-6 md:px-12 py-32">
  <!-- Header -->
  <div class="max-w-3xl mb-20">
    <p class="text-xs uppercase tracking-wider text-gray-400 font-medium mb-4">What we do</p>
    <h2 class="text-3xl md:text-4xl lg:text-5xl font-medium leading-[1.15] tracking-tight">
      We handle everything from <span class="text-primary-500">compliance to conversion</span>, <span class="text-gray-400">so you can unlock the UK market without the complexity.</span>
    </h2>
  </div>

  <!-- Services list -->
  <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-x-8 gap-y-12">
    {#each services as service, i}
      <div class="group">
        <!-- Icon + Number row -->
        <div class="flex items-center gap-3 mb-4">
          <div class="w-10 h-10 rounded-lg bg-gray-100 flex items-center justify-center group-hover:bg-black transition-colors duration-300">
            <service.icon class="w-5 h-5 text-gray-600 group-hover:text-white transition-colors duration-300" strokeWidth={1.5} />
          </div>
          <span class="text-xs text-gray-300 font-medium">0{i + 1}</span>
        </div>

        <!-- Content -->
        <h3 class="text-base font-medium text-gray-900 mb-2">{service.service}</h3>
        <p class="text-sm text-gray-500 leading-relaxed">{service.desc}</p>
      </div>
    {/each}
  </div>
  </div>
</section>
