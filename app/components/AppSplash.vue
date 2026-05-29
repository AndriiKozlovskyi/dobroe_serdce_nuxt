<script setup lang="ts">
const visible = ref(true)
const started = ref(false)

onMounted(() => {
  // Tiny delay lets the enter transition finish before spin begins
  requestAnimationFrame(() => {
    requestAnimationFrame(() => { started.value = true })
  })
})

function onSpinDone() {
  visible.value = false
}
</script>

<template>
  <Transition name="splash">
    <div v-if="visible" class="splash" aria-hidden="true">
      <div class="splash__bg" />
      <div class="splash__overlay" />
      <div class="splash__body">
        <img
          src="/logo.webp"
          alt=""
          class="splash__logo"
          :class="{ 'splash__logo--spin': started }"
          @animationend="onSpinDone"
        />
      </div>
    </div>
  </Transition>
</template>

<style scoped>
.splash {
  position: fixed;
  inset: 0;
  z-index: 9999;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.splash__bg {
  position: absolute;
  inset: -5%;
  background: url('/about/care.webp') center / cover no-repeat;
  filter: blur(22px);
  transform: scale(1.08);
}

.splash__overlay {
  position: absolute;
  inset: 0;
  background: rgba(2, 12, 34, 0.58);
}

.splash__body {
  position: relative;
  z-index: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  animation: bodyIn 0.35s cubic-bezier(0.16, 1, 0.3, 1) both;
}
@keyframes bodyIn {
  from { opacity: 0; transform: scale(0.88); }
  to   { opacity: 1; transform: scale(1); }
}

.splash__logo {
  width: 110px;
  height: 110px;
  transform: rotate(180deg);
  opacity: 0;
  object-fit: contain;
  filter: drop-shadow(0 6px 28px rgba(0, 0, 0, 0.45));
  transform-origin: center center;
}

.splash__logo--spin {
  animation: halfSpin 0.55s cubic-bezier(0.22, 1, 0.36, 1) forwards;
}

@keyframes halfSpin {
  from  { transform: rotate(180deg); opacity: 0; }
  35%   { opacity: 1; }
  to    { transform: rotate(0deg); opacity: 1; }
}

.splash-enter-active { transition: opacity 0.3s ease; }
.splash-leave-active { transition: opacity 0.5s ease; }
.splash-enter-from, .splash-leave-to { opacity: 0; }
</style>
