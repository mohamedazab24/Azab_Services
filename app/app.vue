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
