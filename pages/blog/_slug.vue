<template>
  <main>
    <Navigation />
    <Header :pageInfo="siteInfo" />
    <article class="flex flex-col text-center">
      <NuxtLink to="/blog">Previous Page</NuxtLink>
      <h2 class="text-4xl m-5">{{ post.title }}</h2>
      <nuxt-content class="text-justify ml-10 mr-10 mb-10 p-5" :document="post" />
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
      const post = await $content(`blog/${params.slug}`).fetch();
      return {
        post,
      };
    } catch (error) {
      error("No article found");
    }
  },
};
</script>
