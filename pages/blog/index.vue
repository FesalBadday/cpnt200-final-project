<template>
  <main>
    <Navigation />
    <Header :pageInfo="siteInfo" />
    <div class="flex flex-wrap text-center justify-evenly mt-5">
    <!--Vue Svg -->
    <svg class="w-64"viewBox="0 0 32 32" xmlns="http://www.w3.org/2000/svg">
  <path style="font-variation-settings:normal;stroke-width:.0737982;-inkscape-stroke:none" d="m7.256 3.619 8.91 15.437 8.826-15.355-5.46-.041-3.326 5.912-3.49-5.953Z" fill="gray"/>
  <path style="font-variation-settings:normal;stroke-width:.0737982;-inkscape-stroke:none" d="m1.344 3.578 5.953.082 8.868 15.396L24.951 3.66l5.83.041-14.698 25.373Z"/>
</svg>
<!--Tailwind Svg -->
<svg class="w-64" viewBox="0 0 32 32" xmlns="http://www.w3.org/2000/svg">
  <path d="M9.608 13.009c.88-3.52 3.08-5.28 6.6-5.28 5.28 0 5.939 3.958 8.578 4.619 1.76.44 3.3-.22 4.62-1.98-.88 3.52-3.08 5.28-6.599 5.28-5.28 0-5.94-3.958-8.579-4.62-1.76-.44-3.3.22-4.62 1.98zm-6.6 7.92c.88-3.52 3.08-5.28 6.6-5.28 5.28 0 5.94 3.958 8.579 4.619 1.76.44 3.3-.22 4.62-1.98-.88 3.521-3.08 5.281-6.6 5.281-5.281 0-5.94-3.958-8.58-4.62-1.76-.44-3.3.22-4.619 1.98z" fill="url(#a)" style="fill:#000;stroke-width:.755453"/>
</svg>
<!--Nuxt Svg -->
<svg class="w-64" viewBox="0 0 32 32" version="1.1" id="svg3072" xmlns="http://www.w3.org/2000/svg">
  <defs id="defs3076"/>
  <g id="g862" transform="translate(-74.441 -16.504) scale(1.29259)">
    <path style="fill:#000;fill-opacity:1;stroke-width:.458262" id="path12" d="M65.71 32.161a.859.859 0 0 1-.046-.094 1.204 1.204 0 0 1-.081-.679h-5.466l8.123-14.294 2.666 4.688.773-1.368-2.324-4.095a1.42 1.42 0 0 0-1.135-.75 1.263 1.263 0 0 0-1.1.76l-8.23 14.467a1.455 1.455 0 0 0-.071 1.365 1.266 1.266 0 0 0 1.204.58h6.892a1.263 1.263 0 0 1-1.205-.58z"/>
    <path style="fill:#000;fill-opacity:1;stroke-width:.458262" id="path14" d="m81.555 30.796-6.761-11.912a1.424 1.424 0 0 0-1.14-.759 1.26 1.26 0 0 0-1.1.757l-.875 1.532.778 1.368 1.205-2.132 6.689 11.738h-2.544a1.14 1.14 0 0 1-.053.578.733.733 0 0 1-.053.118l-.021.044a1.456 1.456 0 0 1-1.226.614h3.979a1.454 1.454 0 0 0 1.226-.614 1.263 1.263 0 0 0-.104-1.332z"/>
    <path style="fill:#6e6e6e;fill-opacity:1;stroke-width:.458262" id="path16" d="m77.68 32.128.021-.044a.733.733 0 0 0 .053-.118 1.14 1.14 0 0 0 .053-.578 1.76 1.76 0 0 0-.221-.592l-5.124-9.014-.783-1.368-.778 1.368-5.12 9.014a1.825 1.825 0 0 0-.198.592 1.204 1.204 0 0 0 .074.68.85.85 0 0 0 .046.094 1.266 1.266 0 0 0 1.205.58h9.538a1.46 1.46 0 0 0 1.234-.614Zm-6-8.978 4.682 8.238H67z"/>
  </g>
</svg>
</div>
    <article>
  
      <ul class="flex flex-wrap text-center justify-evenly text-5xl p-10">
        <li class="p-5" v-for="post in posts" :key="post.slug">
          <NuxtLink class="hover:text-pink-600" :to="`blog/${post.slug}`">{{ post.title }}</NuxtLink>
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