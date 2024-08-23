<template>
  <li>
    <base-card>
      <header>
        <h3>{{ title }}</h3>
        <base-button mode="flat" @click="deleteResource">Delete</base-button>
      </header>
      <p>{{ description }}</p>
      <nav>
        <a :href="link" target="_blank"> View Resource </a>
      </nav>
    </base-card>
  </li>
</template>

<script>
import BaseButton from '../UI/BaseButton.vue';
export default {
  inject: ['onDeleteResource'],
  components: { BaseButton },
  props: {
    id: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    description: {
      type: String,
      required: true,
    },
    link: {
      type: String,
      required: true,
    },
  },
  data() {
    return {};
  },
  methods: {
    deleteResource() {
      this.onDeleteResource(this.id);
    },
  },
};
</script>

<style scoped>
li {
  margin: auto;
  /* width: 100%;
  max-width: 40rem; */
}
header {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
h3 {
  font-size: 1.3rem;
  margin: 0.5rem 0;
}
p {
  margin: 0.5rem 0;
}
a {
  text-decoration: none;
  color: #ce5c00;
}
a:hover,
a.active {
  color: #c89300;
}
</style>
