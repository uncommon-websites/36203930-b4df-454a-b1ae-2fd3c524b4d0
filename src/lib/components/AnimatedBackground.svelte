<script lang="ts">
  import { onMount } from 'svelte';

  let vantaRef: HTMLDivElement;
  let vantaEffect: any = null;

  onMount(() => {
    // Load THREE.js first (required by Vanta core)
    const threeScript = document.createElement('script');
    threeScript.src = 'https://cdnjs.cloudflare.com/ajax/libs/three.js/r134/three.min.js';
    document.head.appendChild(threeScript);

    threeScript.onload = () => {
      // Load p5.js (required by TOPOLOGY effect)
      const p5Script = document.createElement('script');
      p5Script.src = 'https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.9.0/p5.min.js';
      document.head.appendChild(p5Script);

      p5Script.onload = () => {
        // Load Vanta TOPOLOGY after both dependencies
        const vantaScript = document.createElement('script');
        vantaScript.src = 'https://cdn.jsdelivr.net/npm/vanta@0.5.24/dist/vanta.topology.min.js';
        document.head.appendChild(vantaScript);

        vantaScript.onload = () => {
          // @ts-ignore
          if (window.VANTA) {
            // @ts-ignore
            vantaEffect = window.VANTA.TOPOLOGY({
              el: vantaRef,
              mouseControls: true,
              touchControls: true,
              gyroControls: false,
              minHeight: 200.0,
              minWidth: 200.0,
              scale: 1.0,
              scaleMobile: 1.0,
              color: 0x2dd4bf,
              backgroundColor: 0x000000,
              // Slow down the animation for a calmer feel
              speed: 0.5
            });
          }
        };
      };
    };

    return () => {
      if (vantaEffect) vantaEffect.destroy();
    };
  });
</script>

<div bind:this={vantaRef} class="absolute inset-0 z-0" style="width: 100%; height: 100%;"></div>
