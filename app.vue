<template>
  <div>
    <NuxtRouteAnnouncer />
    <NuxtWelcome />
    <NuxtWelcome />
    <NuxtWelcome />
    <NuxtWelcome />
    <NuxtWelcome />
    <NuxtWelcome />
    <Transition name="slide-fade">
      <aside v-show="isShowNavbar" class="navBar">
        <div class="navBar__inner">Demo Navigation Bar ipad pro 11</div>
      </aside>
    </Transition>
    
  </div>
</template>

<script setup>
import { useScroll } from '@vueuse/core'
const isShowNavbar = ref(true)

const { directions } = useScroll(window)

watch(directions, (newDirections) => {
  if (newDirections.top) {
    isShowNavbar.value = false
  }

  if (newDirections.bottom) {
    isShowNavbar.value = true
  }
})
</script>

<style lang="css">
.navBar {
  position: fixed;
  z-index: 13;
  right: 0;
  left: 0;
  bottom: 0;

  will-change: transform;
}

.navBar__inner {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 85px;
  background-color: black;
  color: white;
}

.slide-fade-enter-active {
  transition: all 0.3s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.5s ease;
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateY(100px);
}
</style>
