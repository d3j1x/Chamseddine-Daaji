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
    
    const section = document.querySelector('#services');
    if (section) observer.observe(section);
    
    return () => observer.disconnect();
  });
  
  const services = [
    {
      icon: '🚀',
      title: 'تطوير المنتجات',
      description: 'من الفكرة إلى الإطلاق، أساعدك على تحويل رؤيتك للمنتج إلى واقع باستخدام أحدث التقنيات وأفضل الممارسات.'
    },
    {
      icon: '💡',
      title: 'استراتيجية الأعمال',
      description: 'تخطيط استراتيجي وتحليل السوق لمساعدة عملك على النمو وتحقيق النجاح المستدام.'
    },
    {
      icon: '🎨',
      title: 'تصميم واجهة وتجربة المستخدم (UI/UX)',
      description: 'ابتكار واجهات جميلة وسهلة الاستخدام يحبها المستخدمون وتزيد التفاعل والتحويلات.'
    },
    {
      icon: '📊',
      title: 'التسويق الرقمي',
      description: 'استراتيجيات تسويقية مبنية على البيانات لتعزيز حضورك على الإنترنت والوصول إلى جمهورك المستهدف بفعالية.'
    },
    {
      icon: '⚡',
      title: 'تطوير الويب',
      description: 'بناء تطبيقات ويب سريعة، متجاوبة، وقابلة للتوسع باستخدام أحدث التقنيات والأطر.'
    },
    {
      icon: '🔧',
      title: 'الاستشارات',
      description: 'تقديم النصائح والتوجيهات الخبيرة حول التكنولوجيا، عمليات الأعمال، واستراتيجيات النمو للشركات الناشئة.'
    }
  ];
</script>

<section id="services" class="py-20 md:py-32 px-4 sm:px-6 lg:px-8">
  <div class="mx-auto max-w-7xl">
    <!-- Section Header -->
    <div class="text-center mb-16 {visible ? 'animate-fade-in-up' : 'opacity-0'}">
      <p class="text-blue-900 font-medium text-sm md:text-base tracking-wide uppercase mb-2">
        الخدمات
      </p>
      <h2 class="text-3xl md:text-4xl lg:text-5xl font-bold text-foreground mb-4">
        ما أقدمه
      </h2>
      <p class="text-secondary text-lg max-w-2xl mx-auto">
        خدمات شاملة لمساعدتك على بناء، تنمية، وتوسيع أعمالك في عصر الرقمية.
      </p>
    </div>
    
    <!-- Services Grid -->
    <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-6 lg:gap-8">
      {#each services as service, index}
        <div 
          class="group bg-card rounded-2xl p-6 md:p-8 border border-border hover:border-blue-900 transition-all hover:shadow-xl hover:-translate-y-2 {visible ? 'animate-fade-in-up' : 'opacity-0'}"
          style="animation-delay: {index * 0.1}s;"
        >
          <div class="text-4xl md:text-5xl mb-4 transition-transform group-hover:scale-110">
            {service.icon}
          </div>
          <h3 class="text-xl md:text-2xl font-bold text-foreground mb-3 group-hover:text-blue-900 transition-colors">
            {service.title}
          </h3>
          <p class="text-secondary leading-relaxed">
            {service.description}
          </p>
        </div>
      {/each}
    </div>
  </div>
</section>
