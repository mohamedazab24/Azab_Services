
فيو
<script setup lang="ts">
useHead({
  bodyAttrs: {
    class: 'bg-white dark:bg-zinc-900 overscroll-none',
  },
})
useSeoMeta({
  title: 'Chat with PDF',
  ogTitle: 'Chat with PDF',
  ogDescription: 'Chat with PDF is a full-stack AI-powered application that lets you to ask questions to PDF documents. Built using NuxtHub, and powered by Cloudflare Workers AI and Vectorize.',
  description: 'Chat with PDF is a full-stack AI-powered application that lets you to ask questions to PDF documents. Built using NuxtHub, and powered by Cloudflare Workers AI and Vectorize.',
  ogImage: 'https://chat-with-pdf.nuxt.dev/image.png',
  twitterCard: 'summary_large_image',
  twitterSite: '@your_site_handle',
  twitterCreator: '@your_creator_handle',
  ogUrl: 'https://your-site-url.com',
  ogType: 'website',
})
</script>

<template>
  <NuxtRouteAnnouncer />
  <NuxtLoadingIndicator />
  <UApp>
    <NuxtPage />
  </UApp>
</template>

<style>
@import "tailwindcss";
@import "@nuxt/ui";

@plugin "@tailwindcss/typography";
</style>
تأكد من تعديل القيم الخاصة بالروابط (مثل و و ) لتتناسب مع موقعك الجديد.twitterSitetwitterCreatorogUrl

 اسم آخر رسالة التزام تاريخ الالتزام الأخير
..
dashboard.vue
إضافة ملفات عبر التحميل
منذ 7 دقائق
فهرس.ڤو
الالتزام الأولي
منذ 18 دقيقة
تسجيل الدخول
إضافة ملفات عبر التحميل
منذ 7 دقائق
maintenance-request.vue
إضافة ملفات عبر التحميل
منذ 7 دقائق
الصيانة status.vue
إضافة ملفات عبر التحميل
منذ 7 دقائق
متفائل-todos.vue
إضافة ملفات عبر التحميل
منذ 7 دقائق
privacy.vue
إضافة ملفات عبر التحميل
منذ 7 دقائق
profile.vue
إضافة ملفات عبر التحميل
منذ 7 دقائق
register.vue
إضافة ملفات عبر التحميل
منذ 7 دقائق
terms.vue
إضافة ملفات عبر التحميل
منذ 7 دقائق
todos.vue
1 الرقم المرجعي
لقد وجدت ملف في المستودع. إليك محتويات الملف الحالية:app.vue

فيو
<script setup lang="ts">
useHead({
  bodyAttrs: {
    class: 'bg-white dark:bg-zinc-900 overscroll-none',
  },
})
useSeoMeta({
  title: 'Chat with PDF',
  ogTitle: 'Chat with PDF',
  ogDescription: 'Chat with PDF is a full-stack AI-powered application that lets you to ask questions to PDF documents. Built using NuxtHub, and powered by Cloudflare Workers AI and Vectorize.',
  description: 'Chat with PDF is a full-stack AI-powered application that lets you to ask questions to PDF documents. Built using NuxtHub, and powered by Cloudflare Workers AI and Vectorize.',
  ogImage: 'https://chat-with-pdf.nuxt.dev/image.png',
  twitterCard: 'summary_large_image',
})
</script>

<template>
  <NuxtRouteAnnouncer />
  <NuxtLoadingIndicator />
  <UApp>
    <NuxtPage />
  </UApp>
</template>

<style>
@import "tailwindcss";
@import "@nuxt/ui";

@plugin "@tailwindcss/typography";
</style>
الخطوة التالية هي تعديل هذا الملف لإضافة روابط الصفحات الجديدة. سأقوم بذلك الآن.
لإضافة روابط الصفحات الجديدة، يمكننا تعديل قسم في ملف ليشمل الروابط الجديدة. افترض أن لدينا صفحات جديدة مثل و وغيرها. سأضيف هذه الروابط كمثال:<template>app.vuedashboard.vueprofile.vue

فيو
<script setup lang="ts">
useHead({
  bodyAttrs: {
    class: 'bg-white dark:bg-zinc-900 overscroll-none',
  },
})
useSeoMeta({
  title: 'Chat with PDF',
  ogTitle: 'Chat with PDF',
  ogDescription: 'Chat with PDF is a full-stack AI-powered application that lets you to ask questions to PDF documents. Built using NuxtHub, and powered by Cloudflare Workers AI and Vectorize.',
  description: 'Chat with PDF is a full-stack AI-powered application that lets you to ask questions to PDF documents. Built using NuxtHub, and powered by Cloudflare Workers AI and Vectorize.',
  ogImage: 'https://chat-with-pdf.nuxt.dev/image.png',
  twitterCard: 'summary_large_image',
})
</script>

<template>
  <NuxtRouteAnnouncer />
  <NuxtLoadingIndicator />
  <UApp>
    <nav>
      <ul>
        <li><NuxtLink to="/dashboard">Dashboard</NuxtLink></li>
        <li><NuxtLink to="/profile">Profile</NuxtLink></li>
        <li><NuxtLink to="/maintenance-request">Maintenance Request</NuxtLink></li>
        <li><NuxtLink to="/privacy">Privacy</NuxtLink></li>
        <li><NuxtLink to="/terms">Terms</NuxtLink></li>
        <li><NuxtLink to="/todos">Todos</NuxtLink></li>
      </ul>
    </nav>
    <NuxtPage />
  </UApp>
</template>

<style>
@import "tailwindcss";
@import "@nuxt/ui";

@plugin "@tailwindcss/typography";
</style>
