<script lang="ts">
  import { onMount } from 'svelte';

  let isVisible = $state(false);
  let activeSection = $state('');

  const sections = [
    { id: 'services', label: 'Services' },
    { id: 'approach', label: 'Approach' },
    { id: 'why-us', label: 'Why Us' },
    { id: 'contact', label: 'Contact' }
  ];

  function scrollToSection(sectionId: string) {
    return (e: Event) => {
      e.preventDefault();
      const element = document.getElementById(sectionId);
      if (element) {
        element.scrollIntoView({ behavior: 'smooth', block: 'start' });
      }
    };
  }

  function updateActiveSection() {
    const scrollPosition = window.scrollY + window.innerHeight / 3;
    const firstSection = document.getElementById(sections[0].id);

    // Don't show active state if we're still in the hero
    if (firstSection && scrollPosition < firstSection.offsetTop) {
      activeSection = '';
      return;
    }

    for (let i = sections.length - 1; i >= 0; i--) {
      const element = document.getElementById(sections[i].id);
      if (element && element.offsetTop <= scrollPosition) {
        activeSection = sections[i].id;
        break;
      }
    }
  }

  function checkVisibility() {
    const footer = document.getElementById('site-footer');
    const firstSection = document.getElementById(sections[0].id);

    // Hide in hero (before first section)
    if (firstSection && window.scrollY < firstSection.offsetTop - window.innerHeight / 2) {
      isVisible = false;
      return;
    }

    // Hide near footer
    if (footer) {
      const footerRect = footer.getBoundingClientRect();
      isVisible = footerRect.top > window.innerHeight - 100;
      return;
    }

    isVisible = true;
  }

  onMount(() => {
    const handleScroll = () => {
      updateActiveSection();
      checkVisibility();
    };

    window.addEventListener('scroll', handleScroll, { passive: true });
    handleScroll();

    return () => {
      window.removeEventListener('scroll', handleScroll);
    };
  });
</script>

<div
  class="fixed bottom-8 left-1/2 -translate-x-1/2 z-50 bg-white/90 backdrop-blur-md border border-gray-200 rounded-full px-6 py-3 shadow-lg flex gap-6 text-xs font-medium text-gray-500 transition-all duration-300"
  class:opacity-0={!isVisible}
  class:pointer-events-none={!isVisible}
  class:translate-y-4={!isVisible}
>
  {#each sections as section}
    <a
      href="#{section.id}"
      onclick={scrollToSection(section.id)}
      class="hover:text-black transition-colors flex items-center gap-1.5"
      class:text-black={activeSection === section.id}
    >
      {#if activeSection === section.id}
        <span class="w-1.5 h-1.5 bg-primary-500 rounded-full"></span>
      {/if}
      {section.label}
    </a>
  {/each}
</div>
