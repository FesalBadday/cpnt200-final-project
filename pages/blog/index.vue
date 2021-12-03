<template>
<<main>
  <Navigation />
  <Header :pageInfo="siteInfo" />
  <article>
  <ul>
    <li v-for="post in posts" :key="post.slug"
      <NuxtLink :to="'blog/${post.slug}'">{{ post.title }}</NuxtLink>
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
      const post = await $content(`blog`).fetch();
      return {
        post,
      };
    } catch (error) {
      error("No article found");
    }
  },
};
</script>
