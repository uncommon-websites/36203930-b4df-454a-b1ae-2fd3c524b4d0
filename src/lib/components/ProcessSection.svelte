<script lang="ts">
  import { onMount } from 'svelte';

  const steps = [
    {
      id: "assess",
      title: "Assess Your UK Opportunity",
      text: "We start by analyzing your current Amazon US performance, product portfolio, and UK market potential. Our team evaluates regulatory requirements, competitive landscape, and identifies the fastest path to compliant, profitable growth in the UK market.",
      tags: ["Market Analysis", "Regulatory Assessment", "Competitor Research", "Product Viability", "Pricing Strategy", "Growth Forecasting"],
      graphic: "lines"
    },
    {
      id: "prepare",
      title: "Prepare for Market Entry",
      text: "We handle all the complexity of UK market entry. From MHRA compliance and product registration to catalog clean-up and removing rogue sellers, we ensure your brand is retail-ready and fully compliant before launch.",
      tags: ["MHRA Compliance", "Product Registration", "Labeling Requirements", "Catalog Clean-Up", "Brand Protection", "Account Setup"],
      graphic: "curve"
    },
    {
      id: "launch",
      title: "Launch with Optimized Listings",
      text: "We create data-driven product listings, A+ content, and brand stores that convert UK customers. Our team handles keyword research, competitive positioning, and all content creation to maximize visibility and sales from day one.",
      tags: ["Listing Optimization", "Keyword Research", "A+ Content", "Brand Store Design", "Product Photography", "SEO Strategy"],
      graphic: "circle-top"
    },
    {
      id: "grow",
      title: "Grow Through Performance Marketing",
      text: "We drive profitable growth through continuous optimization. Our team manages advertising campaigns, inventory planning, customer reviews, and performance analytics—constantly refining the approach to maximize your ROI and market share.",
      tags: ["Amazon Advertising", "Campaign Management", "Performance Analytics", "Inventory Planning", "Review Management", "Continuous Optimization"],
      graphic: "circle-waves"
    }
  ];

  let activeStep = 0;
  let sectionRef: HTMLElement;

  onMount(() => {
    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            const index = steps.findIndex(step => step.id === entry.target.id);
            if (index !== -1) {
              activeStep = index;
            }
          }
        });
      },
      {
        root: null,
        rootMargin: "-20% 0px -20% 0px", // Trigger when element is in the middle 60% of viewport
        threshold: 0.5
      }
    );

    steps.forEach((step) => {
      const el = document.getElementById(step.id);
      if (el) observer.observe(el);
    });

    return () => observer.disconnect();
  });
</script>

<section id="approach" class="bg-black text-white py-24 px-6 md:px-12 relative scroll-mt-24" bind:this={sectionRef}>
  <div class="max-w-screen-2xl mx-auto flex flex-col md:flex-row gap-12">
    
    <!-- Sticky Navigation -->
    <div class="md:w-1/2 md:h-[calc(100vh-6rem)] md:sticky md:top-24 flex flex-col justify-center">
      <div class="space-y-8">
        {#each steps as step, i}
          <div class="transition-opacity duration-500 {i === activeStep ? 'opacity-100' : 'opacity-30'}">
            <p class="text-xl md:text-2xl font-light mb-1">We help you</p>
            <h2 class="text-2xl md:text-3xl font-bold">{step.title}</h2>
          </div>
        {/each}
      </div>
    </div>

    <!-- Scrollable Cards -->
    <div class="md:w-1/2 space-y-24 pt-12 md:pt-0">
      {#each steps as step, i}
        <div class="bg-white text-black rounded-lg p-8 md:p-12 min-h-[600px] flex flex-col justify-between scroll-mt-32" id={step.id}>
          <!-- Graphic Placeholder -->
          <div class="flex-1 flex items-center justify-center mb-8 border border-gray-100 rounded bg-gray-50 min-h-[200px]">
             {#if step.graphic === 'lines'}
                <svg width="200" height="100" viewBox="0 0 200 100" class="opacity-50">
                    <line x1="20" y1="20" x2="20" y2="80" stroke="black" stroke-width="1"/>
                    <line x1="40" y1="20" x2="40" y2="80" stroke="black" stroke-width="1"/>
                    <line x1="60" y1="20" x2="60" y2="80" stroke="black" stroke-width="1"/>
                    <line x1="80" y1="20" x2="80" y2="80" stroke="black" stroke-width="1"/>
                    <line x1="100" y1="20" x2="100" y2="80" stroke="black" stroke-width="1"/>
                </svg>
             {:else if step.graphic === 'curve'}
                <svg width="200" height="100" viewBox="0 0 200 100" class="opacity-50">
                    <path d="M20 80 Q 100 0 180 80" fill="none" stroke="black" stroke-width="1"/>
                </svg>
             {:else if step.graphic === 'circle-top'}
                <svg width="200" height="100" viewBox="0 0 200 100" class="opacity-50">
                    <circle cx="100" cy="100" r="60" fill="none" stroke="black" stroke-width="1"/>
                    <circle cx="100" cy="100" r="40" fill="none" stroke="black" stroke-width="1"/>
                </svg>
             {:else}
                <svg width="200" height="100" viewBox="0 0 200 100" class="opacity-50">
                    <ellipse cx="100" cy="50" rx="80" ry="20" fill="none" stroke="black" stroke-width="1"/>
                    <ellipse cx="100" cy="50" rx="60" ry="15" fill="none" stroke="black" stroke-width="1"/>
                    <ellipse cx="100" cy="50" rx="40" ry="10" fill="none" stroke="black" stroke-width="1"/>
                </svg>
             {/if}
          </div>

          <div>
             <p class="text-lg leading-relaxed mb-8">{step.text}</p>

             <div class="grid grid-cols-2 gap-4 text-xs font-medium text-gray-600">
               {#each step.tags as tag}
                 <div class="flex items-center gap-2">
                   <span class="w-1.5 h-1.5 bg-black rounded-full shrink-0"></span>
                   {tag}
                 </div>
               {/each}
             </div>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>
