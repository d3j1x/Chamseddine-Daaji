<script lang="ts">
  const currentYear = new Date().getFullYear();
  
  const footerLinks = [
    { name: 'الرئيسية', href: '/' },
    { name: 'من أنا', href: '#about' },
    { name: 'المشاريع', href: '#projects' },
    { name: 'الخدمات', href: '#services' },
    { name: 'تواصل', href: '#contact' }
  ];
  
  const socialLinks = [
    { name: 'GitHub', url: 'https://github.com/d3j1x' },
    { name: 'LinkedIn', url: 'https://linkedin.com/in/chamseddinedaaji' },
    { name: 'X', url: 'https://x.com/chamseddinedaji' }
  ];
</script>

<footer class="border-t border-border bg-card/50">
  <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8 py-12">
    <div class="grid md:grid-cols-3 gap-8 mb-8">
      <!-- Brand -->
      <div>
        <h3 class="text-xl font-bold text-foreground mb-4">شــمــس الــديــن دعــجــي</h3>
        <p class="text-secondary text-sm leading-relaxed">
          بناء حلول مبتكرة وخلق تجارب رقمية ذات معنى للمستقبل.
        </p>
      </div>
      
      <!-- Quick Links -->
      <div>
        <h4 class="font-semibold text-foreground mb-4">روابط سريعة</h4>
        <ul class="space-y-2">
          {#each footerLinks as link}
            <li>
              <a 
                href={link.href} 
                class="text-secondary text-sm hover:text-accent transition-colors"
              >
                {link.name}
              </a>
            </li>
          {/each}
        </ul>
      </div>
      
      <!-- Social -->
      <div>
        <h4 class="font-semibold text-foreground mb-4">Connect</h4>
        <div class="flex gap-4">
          {#each socialLinks as social}
            <a 
              href={social.url}
              target="_blank"
              rel="noopener noreferrer"
              class="text-secondary hover:text-accent transition-colors"
              aria-label={social.name}
            >
              <span class="text-sm">{social.name}</span>
            </a>
          {/each}
        </div>
      </div>
    </div>
    
    <!-- Bottom Bar -->
    <div class="pt-8 border-t border-border flex flex-col sm:flex-row items-center justify-between gap-4">
      <p class="text-secondary text-sm text-center sm:text-left">
        © {currentYear} شــمــس الــديــن دعــجــي. جميع الحقوق محفوظة.
      </p>
      <div class="flex gap-6 text-sm">
        <a href="/privacy-policy" class="text-secondary hover:text-accent transition-colors">سياسة الخصوصية</a>
        <a href="/terms-of-service" class="text-secondary hover:text-accent transition-colors">شروط الخدمة</a>
      </div>
    </div>
  </div>
</footer>
