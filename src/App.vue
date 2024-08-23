<template>
  <the-header title="RememberMe"></the-header>
  <!-- <stored-resource :resource="storedResources"></stored-resource> -->
  <the-resource></the-resource>
</template>

<script>
import TheHeader from './components/layouts/TheHeader.vue';
// import StoredResource from './components/learning-resource/StoredResource.vue';
import TheResource from './components/learning-resource/TheResource.vue';

export default {
  components: {
    // StoredResource,
    TheResource,
    TheHeader,
  },
  // data() {
  //   return {
  //     storedResources: [
  //       {
  //         id: 'official-guide',
  //         title: 'Official Guide',
  //         description: 'The Official vue.js documentation',
  //         link: 'https://vuejs.org',
  //       },
  //       {
  //         id: 'google',
  //         title: 'Google',
  //         description: 'Learn to Google',
  //         link: 'https://google.com',
  //       },
  //     ],
  //   };
  // },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Bree+Serif&family=Caveat:wght@400;700&family=Lobster&family=Monoton&family=Open+Sans:ital,wght@0,400;0,700;1,400;1,700&family=Playfair+Display+SC:ital,wght@0,400;0,700;1,700&family=Playfair+Display:ital,wght@0,400;0,700;1,700&family=Roboto:ital,wght@0,400;0,700;1,400;1,700&family=Source+Sans+Pro:ital,wght@0,400;0,700;1,700&family=Work+Sans:ital,wght@0,400;0,700;1,700&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
html {
  font-family: 'Roboto';
}

body {
  margin: 0;
  padding: 0;
}
</style>
