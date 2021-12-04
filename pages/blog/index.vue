<template>
  <main>
    <Navigation />
    <Header :pageInfo="siteInfo" />
    <article>
      <ul class="flex flex-wrap text-center justify-evenly text-5xl p-10">
        <li class="p-5" v-for="post in posts" :key="post.slug">
          <TailwindSvg v-if="post.title === 'Tailwind CSS'" />
          <VueSvg v-if="post.title === 'Vue.js'" />
          <NuxtSvg v-if="post.title === 'Nuxt.js'" />
          <NuxtLink class="hover:text-pink-600" :to="`/blog/${post.slug}`">{{ post.title }}</NuxtLink>
        </li>
      </ul>
    </article>
    <Footer :pageInfo="siteInfo" />
  </main>
</template>

<script>
export default {
  data() {
    return {
      siteInfo: {
        pageName: "Blog",
        author: "FastVue",
      },
    };
  },
  // fetch the data from blog in the content folder
  async asyncData({ $content, params, error }) {
    try {
      const posts = await $content(`blog`).fetch();
      return {
        posts,
      };
    } catch (error) {
      error("No article found");
    }
  },
};
</script>