<template>
  <base-card>
    <base-button
      @click="setSelectedTab('stored-resources')"
      :mode="storedResButtonMode"
      >Stored Resources</base-button
    >
    <base-button
      @click="setSelectedTab('add-resource')"
      :mode="addResButtonMode"
      >Add Resources</base-button
    >
  </base-card>

  <keep-alive>
    <component :is="selectedTab"></component> 
  </keep-alive>
</template>

<script>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';
export default {
  components: {
    StoredResources,
    AddResource
  },
  data() {
    return {
      selectedTab: 'stored-resources',
      storedResources: [
        {
          id: 'google',
          title: 'Google',
          description: 'You have to know how to use Google...',
          link: 'https://google.com'
        },
        {
          id: 'youtube',
          title: 'YouTube',
          description: 'Learn lots of things from YouTube',
          link: 'https://youtube.com'
        }
      ]
    };
  },
  computed: {
    addResButtonMode() {
      return this.selectedTab === 'add-resource' ? null : 'flat';
    },
    storedResButtonMode() {
      return this.selectedTab === 'stored-resources' ? null : 'flat';
    }
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addResource,
      removeResource: this.removeResource
    };
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, description, link) {
      const newResource = {
        id: new Date().toISOString(),
        title: title,
        description: description,
        link: link
      };
      this.storedResources.unshift(newResource);
      this.selectedTab = 'stored-resources';
    },
    removeResource(resId){
      const removeIndex = this.storedResources.findIndex(res => res.id === resId);
      this.storedResources.splice(removeIndex, 1);
    }
  }
};
</script>
