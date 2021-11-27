<template>
  <div class="min-w-screen-md">
    <ul
      v-if="posts.length"
      class="mt-8"
    >
      <li
        v-for="post of posts"
        :key="post.slug"
        data-cy="post"
        class="grid grid-cols-12 my-8"
      >
        <p class="hidden sm:block text-sm font-normal col-span-2 self-start justify-self-center p-2 mr-2 text-gray-400">
          {{ dateToYMD(new Date(post.date)) }}
        </p>
        <div
          class="col-span-12 sm:col-span-10 self-center relative"
        >
          <nuxt-link
            :to="`/${post.slug}`"
            :class="`font-mono text-2xl font-semibold pt-1 pb-1 relative w-full`"
          >
            {{ post.title }}
          </nuxt-link>
          <p class="font-sans font-thin text-base block pt-2">
            {{ post.description }}
          </p>
          <div class="my-2 ">
            <div
              v-for="tag in post.tags"
              :key="tag"
              :class="`text-xs font-normal pr-3 inline-block text-green-dark text-center`"
            >
              #{{ tag }}
            </div>
          </div>
        </div>
      </li>
    </ul>
    <ul
      v-else
      class="mt-8"
    >
      <li
        class="grid grid-cols-12 my-8"
      >
        <p class="font-sans font-thin text-base block pt-2 col-span-12">
          No posts were found.
        </p>
      </li>
    </ul>
  </div>
</template>

<script>

export default {
  props: {
    posts: {
      type: Array,
      required: true
    },
  },
  methods: {
    dateToYMD(date) {
      var strArray=['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];
      var d = date.getDate();
      var m = strArray[date.getMonth()];
      var y = date.getFullYear();
      return '' + (d <= 9 ? '0' + d : d) + ' ' + m + '\n' + y;
    },
  }
}
</script>

<style>

</style>
