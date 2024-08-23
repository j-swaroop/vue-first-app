<template>
  <header>
    <h1>{{ title }}</h1>
  </header>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scoped>
header {
  height: 5rem;
  background-color: #640032;
  width: 100vw;
  display: flex;
  align-items: center;
  justify-content: center;
  
}
header h1 {
  color: white;
  margin: 0;
}
</style>
