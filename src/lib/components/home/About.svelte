<script lang="ts">
  import { onMount } from 'svelte';
  
  let visible = $state(false);
  
  onMount(() => {
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          visible = true;
        }
      });
    }, { threshold: 0.1 });
    
    const section = document.querySelector('#about');
    if (section) observer.observe(section);
    
    return () => observer.disconnect();
  });
  
  const achievements = [
    { number: '5+', label: 'مشروعات تم إطلاقها' },
    { number: '3+', label: 'سنوات من الخبرة' },
    { number: '10+', label: 'عملاء سعداء' }
  ];
  
  const skills = [
    'استراتيجية الأعمال', 
    'إدارة المنتجات', 
    'التسويق الرقمي', 
    'تطوير الويب', 
    'تصميم واجهات وتجربة المستخدم (UI/UX)', 
    'تحليل البيانات'
  ];
</script>

<section id="about" class="py-20 md:py-32 px-4 sm:px-6 lg:px-8">
  <div class="mx-auto max-w-7xl">
    <div class="grid md:grid-cols-2 gap-12 lg:gap-16 items-center">
      <!-- Profile Image -->
      <div class="order-2 md:order-1 {visible ? 'animate-fade-in-up' : 'opacity-0'}">
        <div class="relative">
          <div class="aspect-square rounded-2xl overflow-hidden bg-muted">
            <img 
              src="/images/chamseddine.png" 
              alt="Profile" 
              class="w-full h-full object-cover"
            />
          </div>
          <div class="absolute -bottom-6 -right-6 w-32 h-32 bg-accent/20 rounded-2xl -z-10"></div>
        </div>
      </div>
      
      <!-- About Content -->
      <div class="order-1 md:order-2 space-y-6 {visible ? 'animate-fade-in-up' : 'opacity-0'}" style="animation-delay: 0.2s;">
        <div>
          <p class="text-blue-900 font-medium text-base tracking-wide  mb-2">
            نبذة عني
          </p>
          <h2 class="text-3xl md:text-4xl lg:text-5xl font-bold text-foreground">
            تحويل الأفكار إلى واقع
          </h2>
        </div>
        
        <div class="space-y-4 text-secondary leading-relaxed">
          <p>
            أنا رائد أعمال مبتدئ شغوف بخلق حلول مبتكرة تحدث تأثيرًا حقيقيًا. علّمتني رحلتي في عالم الأعمال والتكنولوجيا أهمية الجمع بين الإبداع والتفكير الاستراتيجي لبناء منتجات يحبها الناس.
          </p>
          
          <p>
            أركّز حاليًا على تطوير المنتجات الرقمية واستكشاف الفرص في نظام الشركات الناشئة التقنية. أؤمن بقوة التكنولوجيا في حل المشكلات الواقعية وخلق قيمة للمستخدمين والشركات على حد سواء.
          </p>
        </div>
        
        <!-- Key Achievements -->
        <div class="grid grid-cols-3 gap-4 pt-6">
          {#each achievements as achievement}
            <div class="text-center">
              <div class="text-2xl md:text-3xl font-bold text-blue-900">{achievement.number}</div>
              <div class="text-sm text-secondary mt-1">{achievement.label}</div>
            </div>
          {/each}
        </div>
        
        <!-- Skills -->
        <div class="pt-4">
          <h3 class="text-foreground font-semibold mb-4">المهارات والخبرات</h3>
          <div class="flex flex-wrap gap-3">
            {#each skills as skill}
              <span class="px-4 py-2 bg-muted text-foreground text-sm rounded-lg border border-border hover:border-blue-900 transition-colors">
                {skill}
              </span>
            {/each}
          </div>
        </div>
      </div>
    </div>
  </div>
</section>
