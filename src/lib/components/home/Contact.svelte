<script lang="ts">
  import { onMount } from 'svelte';
  
  let visible = $state(false);
  let formData = $state({
    name: '',
    email: '',
    message: ''
  });
  
  let isSubmitting = $state(false);
  let submitStatus = $state<'idle' | 'success' | 'error'>('idle');
  
  onMount(() => {
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          visible = true;
        }
      });
    }, { threshold: 0.1 });
    
    const section = document.querySelector('#contact');
    if (section) observer.observe(section);
    
    return () => observer.disconnect();
  });
  
  async function handleSubmit(e: Event) {
    e.preventDefault();
    isSubmitting = true;
    
    // Simulate form submission
    await new Promise(resolve => setTimeout(resolve, 1000));
    
    console.log('[v0] Form submitted:', formData);
    submitStatus = 'success';
    isSubmitting = false;
    
    // Reset form
    formData = { name: '', email: '', message: '' };
    
    // Reset status after 3 seconds
    setTimeout(() => {
      submitStatus = 'idle';
    }, 3000);
  }
  
  const socialLinks = [
    { name: 'GitHub', icon: 'github', url: 'https://github.com/d3j1x' },
    { name: 'LinkedIn', icon: 'linkedin', url: 'https://linkedin.com/in/chamseddinedaaji' },
    { name: 'X', icon: 'twitter', url: 'https://x.com/chamseddinedaji' },
    { name: 'Email', icon: 'email', url: 'mailto:d3j1x@yahoo.com' }
  ];
</script>

<section id="contact" class="py-20 md:py-32 px-4 sm:px-6 lg:px-8 bg-muted/30">
  <div class="mx-auto max-w-7xl">
    <!-- Section Header -->
    <div class="text-center mb-16 {visible ? 'animate-fade-in-up' : 'opacity-0'}">
      <p class="text-blue-900 font-medium text-sm md:text-base tracking-wide uppercase mb-2">
        تواصل معي
      </p>
      <h2 class="text-3xl md:text-4xl lg:text-5xl font-bold text-foreground mb-4">
        لنعمل معًا
      </h2>
      <p class="text-secondary text-lg max-w-2xl mx-auto">
        أنا دائمًا متاح لمناقشة مشاريع جديدة، أفكار مبتكرة، أو فرص لأكون جزءًا من رؤيتك.
      </p>
    </div>
    
    <div class="grid lg:grid-cols-2 gap-12 lg:gap-16 max-w-6xl mx-auto">
      <!-- Contact Form -->
      <div class="{visible ? 'animate-fade-in-up' : 'opacity-0'}" style="animation-delay: 0.2s;">
        <form onsubmit={handleSubmit} class="space-y-6">
          <div>
            <label for="name" class="block text-sm font-medium text-foreground mb-2">
              الاسم
            </label>
            <input
              type="text"
              id="name"
              bind:value={formData.name}
              required
              class="w-full px-4 py-3 bg-card border border-border rounded-lg text-foreground placeholder:text-muted-foreground focus:outline-none focus:ring-2 focus:ring-blue-900 focus:border-transparent transition-all"
              placeholder="اسمك"
            />
          </div>
          
          <div>
            <label for="email" class="block text-sm font-medium text-foreground mb-2">
              البريد الإلكتروني
            </label>
            <input
              type="email"
              id="email"
              bind:value={formData.email}
              required
              class="w-full px-4 py-3 bg-card border border-border rounded-lg text-foreground placeholder:text-muted-foreground focus:outline-none focus:ring-2 focus:ring-blue-900 focus:border-transparent transition-all"
              placeholder="your.email@example.com"
            />
          </div>
          
          <div>
            <label for="message" class="block text-sm font-medium text-foreground mb-2">
              الرسالة
            </label>
            <textarea
              id="message"
              bind:value={formData.message}
              required
              rows="6"
              class="w-full px-4 py-3 bg-card border border-border rounded-lg text-foreground placeholder:text-muted-foreground focus:outline-none focus:ring-2 focus:ring-blue-900 focus:border-transparent transition-all resize-none"
              placeholder="أخبرني عن مشروعك..."
            ></textarea>
          </div>
          
          <button
            type="submit"
            disabled={isSubmitting}
            class="w-full px-8 py-4 bg-blue-900 text-accent-foreground font-medium rounded-lg hover:bg-blue-900/90 transition-all disabled:opacity-50 disabled:cursor-not-allowed hover:scale-105 shadow-lg"
          >
            {isSubmitting ? 'جارٍ الإرسال…' : 'إرسال الرسالة'}
          </button>
          
          {#if submitStatus === 'success'}
            <p class="text-blue-900 text-sm text-center">تم إرسال الرسالة بنجاح! سأرد عليك في أقرب وقت ممكن.</p>
          {/if}
        </form>
      </div>
      
      <!-- Contact Info -->
      <div class="space-y-8 {visible ? 'animate-fade-in-up' : 'opacity-0'}" style="animation-delay: 0.3s;">
        <div>
          <h3 class="text-2xl font-bold text-foreground mb-4">لنتواصل</h3>
          <p class="text-secondary leading-relaxed mb-6">
            سواء كان لديك سؤال، ترغب في بدء مشروع، أو ببساطة تريد التواصل، لا تتردد في الوصول إليّ. سأبذل قصارى جهدي للرد عليك في أقرب وقت ممكن.
          </p>
        </div>
        
        <!-- Social Links -->
        <div>
          <h4 class="text-lg font-semibold text-foreground mb-4">تابعني</h4>
          <div class="flex flex-wrap gap-4">
            {#each socialLinks as social}
              <a 
                href={social.url}
                target="_blank"
                rel="noopener noreferrer"
                class="flex items-center gap-2 px-4 py-2 bg-card border border-border rounded-lg hover:border-blue-900 transition-all hover:scale-105"
                aria-label={social.name}
              >
                {#if social.icon === 'github'}
                  <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                    <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
                  </svg>
                {:else if social.icon === 'linkedin'}
                  <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                    <path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/>
                  </svg>
                {:else if social.icon === 'twitter'}
                  <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                    <path d="M23 3a10.9 10.9 0 01-3.14 1.53 4.48 4.48 0 00-7.86 3v1A10.66 10.66 0 013 4s-4 9 5 13a11.64 11.64 0 01-7 2c9 5 20 0 20-11.5a4.5 4.5 0 00-.08-.83A7.72 7.72 0 0023 3z"/>
                  </svg>
                {:else if social.icon === 'email'}
                  <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/>
                  </svg>
                {/if}
                <span class="text-sm font-medium">{social.name}</span>
              </a>
            {/each}
          </div>
        </div>
        
        <!-- Additional Info -->
        <div class="bg-card border border-border rounded-2xl p-6 space-y-4">
          <div class="flex items-start gap-3">
            <svg class="w-6 h-6 text-blue-900 flex-shrink-0 mt-1" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/>
            </svg>
            <div>
              <div class="font-medium text-foreground">البريد الإلكتروني</div>
              <div class="text-secondary text-sm">d3j1x@yahoo.com</div>
            </div>
          </div>
          
          <div class="flex items-start gap-3">
            <svg class="w-6 h-6 text-blue-900 flex-shrink-0 mt-1" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"/>
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"/>
            </svg>
            <div>
              <div class="font-medium text-foreground">الموقع</div>
              <div class="text-secondary text-sm">متاح عالميًا</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>
