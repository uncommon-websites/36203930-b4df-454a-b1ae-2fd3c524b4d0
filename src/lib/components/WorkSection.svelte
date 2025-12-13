<script lang="ts">
  const services = [
    {
      service: "Inventory Management",
      desc: "We buy your inventory upfront, removing cash flow concerns and aligning our success with yours.",
      bg: "bg-gray-950",
      img: "/generated/image-warehouse-shelves-stocked-with-supplemen-1765613406909-1.webp", 
      dark: true
    },
    {
      service: "Compliance & Regulations",
      desc: "Navigate UK supplement regulations with confidence. We handle MHRA compliance, labeling requirements, and all regulatory paperwork.",
      bg: "bg-gray-100",
      img: "/generated/image-close-up-of-hands-reviewing-uk-supplemen-1765613409181-2.webp",
      dark: false
    },
    {
      service: "Catalog Clean-Up",
      desc: "Eliminate rogue sellers and messy listings. We restore control of your brand presence on Amazon UK.",
      bg: "bg-gray-100",
      img: "/generated/image-amazon-uk-marketplace-storefront-on-comp-1765613555989-0.webp",
      dark: false
    },
    {
      service: "Listing Optimization",
      desc: "Data-driven product listings that convert. From keyword research to A+ content, we make your products stand out.",
      bg: "bg-gray-950",
      img: "/generated/image-person-working-on-laptop-optimizing-amaz-1765613411659-3.webp",
      dark: true
    },
    {
      service: "Amazon Advertising",
      desc: "Performance marketing that drives profitable growth. We optimize campaigns daily using advanced analytics and category expertise.",
      bg: "bg-gray-100",
      img: "/generated/image-analytics-dashboard-showing-amazon-adver-1765613413820-4.webp",
      dark: false,
      full: true
    },
    {
      service: "Brand Store Design",
      desc: "Create a premium brand experience on Amazon with custom storefronts that tell your story and drive conversions.",
      bg: "bg-gray-100",
      img: "/generated/image-designer-creating-amazon-brand-store-lay-1765613558250-1.webp",
      dark: false
    },
    {
      service: "Ongoing Management",
      desc: "Your dedicated UK team. We handle inventory, customer service, reviews, and continuous optimization—so you don't have to.",
      bg: "bg-gray-100",
      img: "/generated/image-customer-service-team-member-managing-am-1765613560548-2.webp",
      dark: false
    }
  ];
</script>

<section id="services" class="px-6 md:px-12 py-24 bg-white scroll-mt-24">
  <div class="max-w-3xl mb-16">
    <h2 class="text-2xl md:text-3xl font-medium leading-tight">
      <span class="font-bold">We handle everything from <span class="text-primary-600">compliance to conversion</span>,</span> so you can unlock the UK market without adding headcount or navigating complex regulations on your own.
    </h2>
  </div>

  <div class="grid grid-cols-1 md:grid-cols-2 gap-x-6 gap-y-12">
    {#each services as service}
      <div class="group cursor-pointer {service.full ? 'md:col-span-2' : ''}">
        <div class={`aspect-[4/3] w-full rounded-lg overflow-hidden relative ${service.bg} mb-4 ${service.full ? 'md:aspect-[2.5/1]' : ''}`}>
          {#if service.img}
             <img src={service.img} alt={service.service} class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-105" />
          {:else}
             <div class="w-full h-full flex items-center justify-center p-8">
               <span class={`text-xl md:text-2xl font-bold text-center ${service.dark ? 'text-white' : 'text-black'}`}>{service.service}</span>
             </div>
          {/if}
        </div>
        <h3 class="text-sm font-bold mb-1">{service.service}</h3>
        <p class="text-sm text-gray-600">{service.desc}</p>
      </div>
    {/each}
  </div>
</section>
