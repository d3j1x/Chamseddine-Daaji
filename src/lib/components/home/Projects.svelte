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
    
    const section = document.querySelector('#projects');
    if (section) observer.observe(section);
    
    return () => observer.disconnect();
  });
  
  const projects = [
    {
      title: 'عالم اتش.تي.إم.إل | HTMLverse',
      description: 'استكشف عالم اتش.تي.إم.إل  HTMLverse (لغة ترميز النص الفائق) مع أمثلة، أفضل الممارسات، نصائح (تحسين محركات البحث)، وإرشادات الوصول.',
      technologies: ['HTML', 'CSS', 'GitHub'],
      link: 'https://d3j1x.github.io/HTMLverse/',
      image: '/images/HTMLverseLogo.png?height=400&width=600'
    },
    {
      title: 'Testx',
      description: 'تطبيق مفتوح المصدر لتعليم واختبار مهارات اختبار البرمجيات (Software Testing). يوفّر تجربة تفاعلية لتعلّم المفاهيم العملية والنظرية مع واجهة أنيقة وسهلة الاستخدام.',
      technologies: ['SvelteKit', 'Vercel', 'Node.js', 'Tailwind CSS'],
      link: 'https://github.com/SmrtMrktX/Testx',
      image: '/images/testx.png?height=400&width=600'
    },
    {
      title: 'Sveltx',
      description: 'قالب حديث وغني بالمميزات لبناء تطبيقات ويب قابلة للتوسع وعالية الأداء',
      technologies: ['Sveltekit', 'TypeScript CSS', 'DaisyUI', 'Tailwind CSS'],
      link: 'https://github.com/SmrtMrktX/Sveltx',
      image: '/images/sveltx.png?height=400&width=600'
    },
    {
      title: 'Experdesk',
      description: 'تطبيق سطح مكتب احترافي لاختبارات الاختيار من متعدد (QCM)، صُمم لتقديم تجربة تعليمية وتقييمية سلسة وسريعة. يدعم أنظمة التشغيل ويندوز وماك ولينكس، ويتميز بواجهة مستخدم حديثة وأداء مستقر على جميع المنصات.',
      technologies: ['Electron', 'Svelte', 'Gsap', 'Tailwind CSS'],
      link: 'https://github.com/d3j1x/Experdesk',
      image: '/images/experdesk.png?height=400&width=600'
    }
  ];
</script>

<section id="projects" class="py-20 md:py-32 px-4 sm:px-6 lg:px-8 bg-muted/30">
  <div class="mx-auto max-w-7xl">
    <!-- Section Header -->
    <div class="text-center mb-16 {visible ? 'animate-fade-in-up' : 'opacity-0'}">
      <p class="text-accent font-medium text-sm md:text-base tracking-wide uppercase mb-2">
        معرض أعمالي
      </p>
      <h2 class="text-3xl md:text-4xl lg:text-5xl font-bold text-foreground mb-4">
        مشاريع مميزة
      </h2>
      <p class="text-secondary text-lg max-w-2xl mx-auto">
        عرضٌ لأحدث مشاريعي التي تُظهر مهاراتي وشغفي بالابتكار.
      </p>
    </div>
    
    <!-- Projects Grid -->
    <div class="grid md:grid-cols-2 gap-8 lg:gap-12">
      {#each projects as project, index}
        <article 
          class="group bg-card rounded-2xl overflow-hidden border border-border hover:border-accent transition-all hover:shadow-2xl {visible ? 'animate-fade-in-up' : 'opacity-0'}"
          style="animation-delay: {index * 0.1}s;"
        >
          <a href={project.link} target="_blank" class="block">
            <!-- Project Image -->
            <div class="relative overflow-hidden aspect-video bg-muted">
              <img
                src={project.image || "/placeholder.svg"}
                alt={project.title}
                class="w-full h-full object-center transition-transform duration-500 group-hover:scale-110"
              />
              <div class="absolute inset-0 bg-gradient-to-t from-card/90 to-transparent opacity-0 group-hover:opacity-100 transition-opacity"></div>
            </div>
            
            <!-- Project Content -->
            <div class="p-6 space-y-4">
              <h3 class="text-xl md:text-2xl font-bold text-foreground group-hover:text-accent transition-colors flex items-center gap-2">
                {project.title}
                <svg class="w-5 h-5 transition-transform group-hover:translate-x-1 group-hover:-translate-y-1" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"/>
                </svg>
              </h3>
              
              <p class="text-secondary leading-relaxed">
                {project.description}
              </p>
              
              <div class="flex flex-wrap gap-2 pt-2">
                {#each project.technologies as tech}
                  <span class="text-xs font-medium text-accent bg-accent/10 px-3 py-1 rounded-full">
                    {tech}
                  </span>
                {/each}
              </div>
            </div>
          </a>
        </article>
      {/each}
    </div>
  </div>
</section>
