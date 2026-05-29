<script setup lang="ts">
const { t } = useI18n()
const { observe } = useScrollAnimation()

onMounted(() => {
  observe()
})
</script>

<template>
  <div>
    <AppSplash />
    <AppPageLoader />
    <NuxtRouteAnnouncer />
    <NuxtPage />
    <a
      href="tel:+380961462910"
      class="app-fab fixed bottom-6 right-6 z-40 flex items-center justify-center gap-2 rounded-full shadow-lift transition-all duration-300 hover:-translate-y-1 w-14 h-14 sm:w-auto sm:h-auto sm:px-4 sm:py-3"
      style="background: linear-gradient(135deg, var(--color-sapphire-700), var(--color-sapphire-800));"
      :aria-label="t('app.callAria')"
    >
      <svg class="h-6 w-6 flex-shrink-0 text-white sm:h-5 sm:w-5" fill="currentColor" viewBox="0 0 24 24">
        <path d="M6.62 10.79c1.44 2.83 3.76 5.14 6.59 6.59l2.2-2.2c.27-.27.67-.36 1.02-.24 1.12.37 2.33.57 3.57.57.55 0 1 .45 1 1V20c0 .55-.45 1-1 1-9.39 0-17-7.61-17-17 0-.55.45-1 1-1h3.5c.55 0 1 .45 1 1 0 1.25.2 2.45.57 3.57.11.35.03.74-.25 1.02l-2.2 2.2z" />
      </svg>
      <span class="hidden sm:inline font-body text-sm font-semibold text-white">+38 096 146 29 10</span>
    </a>
  </div>
</template>
