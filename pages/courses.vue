<template>
  <!-- <div class="container grid ms:mx-16 md:grid-cols-2 md:gap-8 md:w-max-screen-md"> -->
  <div class="max-w-screen-md mx-auto">
    <h1 class="text-4xl font-mono font-bold mt-8 text-black">
      Courses
    </h1>
    <div
      v-for="course in courses"
      :key="course.title"
      class="mt-8"
    >
      <div class="gradient pb-1 pr-1 shadow-lg mx-8 lg:mx-0">
        <div class="bg-black relative overflow-hidden text-white">
          <div
            v-if="course.commingSoon"
            :class="`ribbon uppercase ${course.commingSoon ? 'bg-green' : '' }`"
          >
            comming soon
          </div>
          <div
            v-if="course.onSale"
            :class="`ribbon uppercase ${course.onSale ? 'bg-red' : '' }`"
          >
            on sale!
          </div>
          <div class="grid grid-cols-1 ms:grid-cols-12">
            <img
              :src="`${require(`~/assets/images/courses/${course.image}`)}`"
              :alt="course.alt"
              class="w-full col-span-4"
            >
            <div class="px-8 py-4 col-span-8 ms:px-4 ms:py-4">
              <span
                class="font-mono font-bold text-2xl relative pb-1 ms:text-xl ms:pb-0 md:text-3xl"
              >
                {{ course.title }}
              </span>
              <hr class="my-4 border-white w-2/5">
              <p class="mt-4 ms:mt-2 ms:text-sm md:text-base md:font-light">
                {{ course.description }} <a
                  v-if="course.href"
                  :href="course.href"
                  class="font-bold pb-1"
                >Visit course site</a>
              </p>
              <a
                v-if="course.href"
                :href="course.href"
                class="ms:hidden bg-red block w-1/2 text-white h-14 mt-8 mx-auto text-center p-4 font-mono font-bold hover:bg-red-dark transition ease-in-out focus:outline-none"
              >
                Get started
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ params, error, $content }) {
    try {
      const courses = await $content("/")
      .fetch();
      return { courses };
    } catch (err) {
      error({
        statusCode: 404,
        message: "Page could not be found",
      });
    }
  },
  head() {
    return {
      title: 'Courses',
      link: [
        {
          rel: "canonical",
          href: `https://filiphric.com/courses`,
        },
      ]
    }
  },
}
</script>

<style lang="postcss" scoped>
  .ribbon {
    @apply absolute top-0 right-0 w-48 h-8 -mr-10 mt-10 text-center p-1 transform rotate-45 text-white font-bold shadow-md ms:left-0 ms:right-auto ms:h-4 ms:-rotate-45 ms:text-xs ms:p-0 ms:-ml-10 ms:mr-0;
  }
</style>
