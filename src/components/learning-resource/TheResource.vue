<template>
  <base-card>
    <base-button
      :mode="setStoredBtn"
      @click="setSelectedTab('stored-resource')"
    >
      Stored Resource</base-button
    >
    <base-button :mode="setResBtn" @click="setSelectedTab('add-resource')">
      Add Resource
    </base-button>
  </base-card>
  <!-- <stored-resource
    :resource="storedResources"
    v-if="selectedTab === 'stored-resource'"
  ></stored-resource>
  <add-resource v-if="selectedTab === 'add-resource'"> </add-resource> -->
  <keep-alive>
    <component :is="selectedTab"> </component>
  </keep-alive>
</template>

<script>
import { v4 } from 'uuid';
import AddResource from './AddResource.vue';
import StoredResource from './StoredResource.vue';

export default {
  components: {
    StoredResource,
    AddResource,
  },

  computed: {
    setStoredBtn() {
      return this.selectedTab === 'stored-resource' ? null : 'flat';
    },
    setResBtn() {
      return this.selectedTab === 'add-resource' ? null : 'flat';
    },
  },

  data() {
    return {
      selectedTab: 'stored-resource',
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The Official vue.js documentation',
          link: 'https://vuejs.org',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn to Google',
          link: 'https://google.com',
        },
      ],
    };
  },

  provide() {
    return {
      resources: this.storedResources,
      addNewResource: this.addNewResource,
      onDeleteResource: this.onDeleteResource,
    };
  },

  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addNewResource(title, description, link) {
      const newResource = {
        id: v4(),
        title: title,
        description: description,
        link: link,
      };

      this.storedResources.unshift(newResource);
      this.selectedTab = 'stored-resource';
    },
    onDeleteResource(id) {
      console.log(id);
      const findIdx = this.storedResources.find((res) => res.id === id);
      this.storedResources.splice(findIdx, 1);
    },
  },

  //   mounted(){
  //     console.log(this.$props);
  //   }
};
</script>

<style scoped></style>
