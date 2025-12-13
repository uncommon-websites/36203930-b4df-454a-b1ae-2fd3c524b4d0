<script lang="ts">
  function scrollToSection(e: MouseEvent, sectionId: string) {
    e.preventDefault();
    const element = document.getElementById(sectionId);
    if (element) {
      element.scrollIntoView({ behavior: 'smooth', block: 'start' });
    }
  }
</script>

<div class="fixed bottom-8 left-1/2 -translate-x-1/2 z-50 bg-white/80 backdrop-blur-md border border-gray-200 rounded-full px-6 py-3 shadow-lg flex gap-6 text-xs font-medium text-gray-600">
  <a href="#services" onclick={(e) => scrollToSection(e, 'services')} class="hover:text-black transition-colors">Services</a>
  <a href="#approach" onclick={(e) => scrollToSection(e, 'approach')} class="hover:text-black transition-colors">Approach</a>
  <a href="#why-us" onclick={(e) => scrollToSection(e, 'why-us')} class="hover:text-black transition-colors">Why Us</a>
  <a href="#contact" onclick={(e) => scrollToSection(e, 'contact')} class="hover:text-black transition-colors flex items-center gap-1">
    <span class="w-2 h-2 bg-green-500 rounded-full"></span>
    Contact
  </a>
</div>
