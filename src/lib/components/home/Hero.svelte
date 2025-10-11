<script lang="ts">
  import { onMount } from 'svelte';
  
  let visible = $state(false);
  
  onMount(() => {
    setTimeout(() => visible = true, 100);
  });
</script>

<section id="home" class="min-h-[80vh]  flex items-center justify-center px-4 sm:px-6 lg:px-8 pt-20">
  <div class="mx-auto max-w-7xl w-full">
    <div class="text-center space-y-8">
      <!-- Animated headline -->
      <div class="space-y-4 {visible ? 'animate-fade-in-up' : 'opacity-0'}">
        <p class="text-accent font-medium text-sm md:text-base tracking-wide uppercase">
          مرحبًا بكم في ملفّي الشخصي
        </p>
        <h1 class="text-4xl sm:text-5xl md:text-6xl lg:text-7xl font-bold text-foreground leading-tight">
          بناء المستقبل،<br />
          <span class="text-accent">مشروعًا تلو الآخر</span>
        </h1>
        <p class="text-secondary text-lg md:text-xl leading-relaxed max-w-2xl mx-auto">
          رائد أعمال مبتدئ شغوف بابتكار حلول إبداعية تُحدث فرقًا. أحوّل الأفكار إلى واقع من خلال التكنولوجيا والإبداع.
        </p>
      </div>
      
      <!-- CTA Buttons -->
      <div class="flex flex-col sm:flex-row items-center justify-center gap-4 {visible ? 'animate-fade-in' : 'opacity-0'}" style="animation-delay: 0.2s;">
        <a 
          href="#projects" 
          class="px-8 py-3 bg-accent text-accent-foreground rounded-lg font-medium hover:bg-accent/90 transition-all hover:scale-105 shadow-lg"
          aria-label="View My Work"
        >
          عرض أعمالي
        </a>
        <a 
          href="#contact" 
          class="px-8 py-3 border-2 border-border text-foreground rounded-lg font-medium hover:bg-muted transition-all hover:scale-105"
          aria-label="Get In Touch"
        >
          تواصل معي
        </a>
      </div>
      
      <!-- Scroll indicator -->
      <div class="pt-12 {visible ? 'animate-fade-in' : 'opacity-0'}" style="animation-delay: 0.4s;">
        <a href="#about" class="inline-block animate-bounce" aria-label="Scroll to About">
          <svg class="w-6 h-6 text-secondary" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3" />
          </svg>
        </a>
      </div>
    </div>
  </div>
</section>
