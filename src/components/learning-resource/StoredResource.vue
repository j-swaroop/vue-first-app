<template>
  <ul>
    <learning-resource
      v-for="res in resources"
      :key="res.id"
      :id="res.id"
      :title="res.title"
      :description="res.description"
      :link="res.link"
    >
    </learning-resource>
  </ul>
</template>

<script>
import LearningResource from './LearningResource.vue';

export default {
  components: {
    LearningResource,
  },
  // props: {
  //   resource: {
  //     type: Array,
  //     required: true,
  //   },
  // },
  inject: ['resources']
};
</script>

<style scoped>
    ul{
        padding: 0;
        list-style: none;
        margin: auto;
        max-width: 50rem;
        /* background-color: aliceblue; */
    }
</style>