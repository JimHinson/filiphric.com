<template>
  <div class="grid place-items-center">
    <button
      id="articleLink"
      class="bg-blue hover:bg-blue-dark text-white w-[fit-content] px-4 py-2 font-mono font-bold sm:mx-auto md:mx-0 transition ease-in-out focus:outline-none"
      @click="copyLink"
    >
      Click to copy article link 🔗
    </button>
  </div>
</template>

<script>
export default {
methods: {
    copyLink() {
      const clipBoardValue = window.location.href;
      const clipboard = window.navigator.clipboard;
      const linkToCopy = document.getElementById('articleLink');
      linkToCopy.innerText = 'Copied to clipboard! 🎉'
      setTimeout(function () {
        linkToCopy.innerText = 'Click to copy article link 🔗'
			}, 5000);
      return clipboard.writeText(clipBoardValue);
    },
  }
}
</script>

<style>

</style>
