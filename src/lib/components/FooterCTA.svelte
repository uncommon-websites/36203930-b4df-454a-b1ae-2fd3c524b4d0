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

    try {
      const response = await fetch('https://api.web3forms.com/submit', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({
          access_key: 'f3143083-6997-49df-b8b3-da514a59b75d',
          to: 'k@krish.sh',
          name,
          email,
          message
        })
      });

      isSubmitted = response.ok;
    } catch {
      isSubmitted = false;
    }

    isSubmitting = false;

    if (isSubmitted) {
      setTimeout(() => {
        closeModal();
      }, 2000);
    }
  }
</script>

<svelte:window onkeydown={handleKeydown} />

<section id="contact" class="bg-black scroll-mt-24">
  <div class="max-w-[1600px] mx-auto px-6 md:px-12 py-32">
  <div class="max-w-3xl mx-auto text-center">
    <!-- Eyebrow -->
    <div class="inline-flex items-center gap-2 mb-6">
      <span class="w-1.5 h-1.5 bg-primary-500 rounded-full animate-pulse"></span>
      <span class="text-xs uppercase tracking-wider text-gray-500 font-medium">Available for new partners</span>
    </div>

    <!-- Main headline -->
    <h2 class="text-4xl md:text-5xl lg:text-6xl font-medium leading-[1.1] tracking-tight text-white mb-8">
      Ready to unlock the<br /><span class="text-primary-400">UK market</span>?
    </h2>

    <!-- CTA row -->
    <div class="inline-flex flex-col sm:flex-row items-center gap-6">
      <button
        onclick={openModal}
        class="bg-white text-black px-8 py-4 rounded-full text-sm font-medium hover:bg-gray-100 transition-colors"
      >
        Get in touch
      </button>
      <div class="flex items-center gap-3">
        <div class="w-10 h-10 rounded-full overflow-hidden bg-gray-800 shrink-0">
          <img src="/uploaded/1765616340685-h8ibxgq.jpg" alt="Craig" class="w-full h-full object-cover" />
        </div>
        <div class="text-left">
          <p class="text-white text-sm font-medium">Talk to Craig</p>
          <p class="text-gray-500 text-xs">Company Director</p>
        </div>
      </div>
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
