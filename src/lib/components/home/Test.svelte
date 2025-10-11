<script lang="ts">
  import { onMount } from 'svelte';
  
  let visible = $state(false);
  
  onMount(() => {
    setTimeout(() => visible = true, 100);
  });
</script>


<div class="w-full max-w-7xl px-4 mx-auto sm:px-8 md:mt-24 mt-12 {visible ? 'animate-fade-in-up' : 'opacity-0'}">
    <blockquote class="relative grid items-center bg-white shadow-xl md:grid-cols-3 rounded-xl">
        
        <img class="hidden object-cover w-full h-full rounded-l-xl md:block" style="clip-path: polygon(0 0%, 100% 0%, 75% 100%, 0% 100%);" 
        src="/images/chamseddine.png" alt="Profile picture of Chamseddine Daaji">

        <article class="relative p-6 md:p-8 md:col-span-2">
            <svg class="absolute top-0 right-0 hidden w-24 h-24 -mt-12 -mr-12 text-primary-600 md:block" width="256"
                height="256" viewBox="0 0 256 256" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path
                    d="M65.44 153.526V149.526H61.44H20.48C11.3675 149.526 4 142.163 4 133.105V51.4211C4 42.3628 11.3675 35 20.48 35H102.4C111.513 35 118.88 42.3628 118.88 51.4211V166.187C118.88 195.935 95.103 220.165 65.44 220.979V153.526ZM198.56 153.526V149.526H194.56H153.6C144.487 149.526 137.12 142.163 137.12 133.105V51.4211C137.12 42.3628 144.487 35 153.6 35H235.52C244.633 35 252 42.3628 252 51.4211V166.187C252 195.935 228.223 220.165 198.56 220.979V153.526Z"
                    stroke="currentColor" stroke-width="8"></path>
            </svg>

            <div class="space-y-8">
                <p class="text-base sm:leading-relaxed md:text-2xl ">
                    أنا شمس الدين دعجي، رائد أعمال ومطور برمجيات شغوف بابتكار الحلول الرقمية التي تُحدث فرقًا حقيقيًا. أؤمن بأن التقنية ليست مجرد أدوات، بل وسيلة لبناء مستقبل أكثر ذكاءً وحرية للمبدعين والأعمال الناشئة. أعمل حاليًا على تطوير مشاريع مفتوحة المصدر تهدف إلى تمكين الأفراد والشركات من بناء منصّاتهم الرقمية بسهولة وكفاءة. أحب التعلّم المستمر، خوض التحديات، وتحويل الأفكار إلى منتجات ملموسة تجمع بين البساطة والابتكار.
                </p>

                <footer class="flex items-center space-x-4 md:space-x-0">
                    <img class="w-12 h-12 rounded-full md:hidden" src="/images/chamseddine.png" alt="Profile picture of Chamseddine Daaji">
                    <span class="font-bold text-lg">شــمــس الــديــن دعــجــي</span>
                </footer>
            </div>
        </article>
    </blockquote>
</div>

