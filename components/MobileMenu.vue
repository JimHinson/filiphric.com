<template>
  <transition
    name="mobile-menu"
    mode="out-in"
  >
    <div
      v-if="showMenu"
      class="z-50 relative"
    >
      <div
        id="overlay"
        class="fixed w-screen h-screen top-0 left-0 bottom-0 right-0 z-20 cursor-pointer bg-black opacity-90"
        @click="hideMenu()"
      >
        <MenuItems class="text-4xl font-mono font-semibold text-white h-full grid auto-rows-min place-content-center place-items-center gap-6" />
      </div>
    </div>
  </transition>
</template>

<script>
 export default {
  computed: {
    showMenu() {
        return this.$store.getters['mobileMenu/toggleMenu']
    }
  },
  methods: {
    hideMenu() {
        this.$store.dispatch('mobileMenu/toggleMenu')
    }
  }
}

</script>

<style lang="postcss" scoped>
.mobile-menu-enter-active,
.mobile-menu-leave-active {
  @apply z-50;
  transition: opacity .2s;
}

.mobile-menu-enter,
.mobile-menu-leave-active
 {
   @apply z-50;
  opacity: 0
}
</style>
