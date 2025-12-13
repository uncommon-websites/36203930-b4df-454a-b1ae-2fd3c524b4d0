<script lang="ts">
  // State management
  let isModalOpen = $state(false);
  let isSubmitting = $state(false);
  let isSubmitted = $state(false);
  
  // Form fields
  let name = $state('');
  let email = $state('');
  let message = $state('');
  
  // Functions
  function openModal() {
    isModalOpen = true;
    document.body.style.overflow = 'hidden';
  }
  
  function closeModal() {
    isModalOpen = false;
    document.body.style.overflow = '';
    
    // Reset form after closing animation
    setTimeout(() => {
      if (!isModalOpen) {
        name = '';
        email = '';
        message = '';
        isSubmitted = false;
      }
    }, 300);
  }
  
  function handleBackdropClick(e: MouseEvent) {
    if (e.target === e.currentTarget) {
      closeModal();
    }
  }
  
  function handleBackdropKeydown(e: KeyboardEvent) {
    if (e.key === 'Enter' && e.target === e.currentTarget) {
      closeModal();
    }
  }
  
  function handleKeydown(e: KeyboardEvent) {
    if (e.key === 'Escape' && isModalOpen) {
      closeModal();
    }
  }
  
  async function handleSubmit(e: Event) {
    e.preventDefault();
    
    isSubmitting = true;
    
    // Simulate form submission
    await new Promise(resolve => setTimeout(resolve, 1000));
    
    console.log('Form submitted:', { name, email, message });
    
    isSubmitting = false;
    isSubmitted = true;
    
    // Close modal after success message
    setTimeout(() => {
      closeModal();
    }, 2000);
  }
</script>

<svelte:window onkeydown={handleKeydown} />

<section id="contact" class="px-6 md:px-12 pb-24 bg-white scroll-mt-24">
  <div class="rounded-2xl overflow-hidden relative bg-gradient-to-br from-black to-gray-700 text-white p-8 md:p-16 min-h-[500px] flex flex-col justify-between">
    <!-- Background overlay/image could go here -->
    
    <div>
      <h2 class="text-2xl md:text-3xl font-bold mb-2">Ready to unlock the <span class="text-primary-400">UK market</span>?</h2>
      <h2 class="text-2xl md:text-3xl font-bold">Let's discuss your Amazon UK opportunity.</h2>
    </div>

    <div class="bg-white text-black rounded-xl p-6 md:p-8 max-w-md self-end w-full flex items-center gap-6">
      <div class="flex-1">
        <h3 class="font-bold text-lg">Craig</h3>
        <p class="text-xs text-gray-500 mb-6">Company Director</p>
        <button 
          onclick={openModal}
          class="bg-primary-600 text-white px-6 py-2 rounded-full text-xs font-bold uppercase tracking-wide hover:bg-primary-700 transition-colors"
        >
          Get in touch
        </button>
      </div>
      <div class="w-24 h-24 rounded-lg overflow-hidden bg-gray-200 shrink-0">
        <img src="/uploaded/1765616340685-h8ibxgq.jpg" alt="Craig" class="w-full h-full object-cover" />
      </div>
    </div>
  </div>
</section>

<!-- Contact Form Modal -->
{#if isModalOpen}
  <div 
    class={[
      'fixed inset-0 z-50 flex items-center justify-center p-4 bg-black/50 backdrop-blur-sm',
      isModalOpen ? 'animate-in fade-in duration-200' : ''
    ]}
    onclick={handleBackdropClick}
    onkeydown={handleBackdropKeydown}
    role="dialog"
    aria-modal="true"
    aria-labelledby="modal-title"
    tabindex="-1"
  >
    <div class="bg-white rounded-2xl w-full max-w-lg p-6 md:p-8 relative animate-in zoom-in-95 duration-200">
      <!-- Close button -->
      <button
        onclick={closeModal}
        class="absolute top-4 right-4 p-2 rounded-full hover:bg-gray-100 transition-colors"
        aria-label="Close modal"
      >
        <svg class="w-5 h-5 text-gray-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
        </svg>
      </button>
      
      {#if !isSubmitted}
        <!-- Form -->
        <div class="mb-6">
          <h2 id="modal-title" class="text-2xl font-bold text-black mb-2">Get in touch</h2>
          <p class="text-gray-600 text-sm">Tell us about your Amazon UK opportunity and we'll get back to you soon.</p>
        </div>
        
        <form onsubmit={handleSubmit} class="space-y-4">
          <!-- Name field -->
          <div>
            <label for="name" class="block text-sm font-medium text-gray-700 mb-1">
              Name
            </label>
            <input
              id="name"
              type="text"
              bind:value={name}
              required
              class="w-full px-4 py-3 rounded-lg border border-gray-300 focus:outline-none focus:ring-2 focus:ring-primary-500 focus:border-transparent transition-all"
              placeholder="Your name"
            />
          </div>
          
          <!-- Email field -->
          <div>
            <label for="email" class="block text-sm font-medium text-gray-700 mb-1">
              Email
            </label>
            <input
              id="email"
              type="email"
              bind:value={email}
              required
              class="w-full px-4 py-3 rounded-lg border border-gray-300 focus:outline-none focus:ring-2 focus:ring-primary-500 focus:border-transparent transition-all"
              placeholder="your@email.com"
            />
          </div>
          
          <!-- Message field -->
          <div>
            <label for="message" class="block text-sm font-medium text-gray-700 mb-1">
              Tell us more about you
            </label>
            <textarea
              id="message"
              bind:value={message}
              required
              rows="4"
              class="w-full px-4 py-3 rounded-lg border border-gray-300 focus:outline-none focus:ring-2 focus:ring-primary-500 focus:border-transparent transition-all resize-none"
              placeholder="Tell us about your brand and what you're looking to achieve in the UK market..."
            ></textarea>
          </div>
          
          <!-- Submit button -->
          <button
            type="submit"
            disabled={isSubmitting}
            class={[
              'w-full py-3 px-6 rounded-lg font-bold text-white transition-all',
              isSubmitting 
                ? 'bg-gray-400 cursor-not-allowed' 
                : 'bg-primary-600 hover:bg-primary-700'
            ]}
          >
            {isSubmitting ? 'Sending...' : 'Send message'}
          </button>
        </form>
      {:else}
        <!-- Success message -->
        <div class="text-center py-8">
          <div class="w-16 h-16 bg-green-100 rounded-full flex items-center justify-center mx-auto mb-4">
            <svg class="w-8 h-8 text-green-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path>
            </svg>
          </div>
          <h3 class="text-xl font-bold text-black mb-2">Message sent!</h3>
          <p class="text-gray-600">We'll get back to you soon.</p>
        </div>
      {/if}
    </div>
  </div>
{/if}
