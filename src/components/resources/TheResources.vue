<template>
  <BaseCard>
    <BaseButton
      :mode="storedResourceActiveTab"
      @click="setSelectedTab('StoredResources')"
    >
      Stored Resources</BaseButton
    >
    <BaseButton
      :mode="addResourceActiveTab"
      @click="setSelectedTab('AddResources')"
    >
      Add Resource</BaseButton
    ></BaseCard
  >
  <component :is="selectedTab"></component>
</template>
<script>
import StoredResources from './StoredResources.vue';
import AddResources from './AddResources.vue';
export default {
  components: {
    StoredResources,
    AddResources,
  },
  data() {
    return {
      selectedTab: 'StoredResources',
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The official vue.js documentaiton',
          link: 'https://vuejs.org',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn to google',
          link: 'https://google.com',
        },
      ],
    };
  },
  provide() {
    return {
      storedResources: this.storedResources,
      addResource: this.addResource,
      removeResource: this.removeResource,
    };
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(resource) {
      this.storedResources.unshift({
        id: resource.id,
        title: resource.title,
        description: resource.description,
        link: resource.url,
      });
      this.selectedTab = 'StoredResources';
    },
    removeResource(resourceId) {
      const resourceIndex = this.storedResources.findIndex(
        (res) => res.id === resourceId
      );
      this.storedResources.splice(resourceIndex, 1);
    },
  },
  computed: {
    storedResourceActiveTab() {
      return this.selectedTab === 'StoredResources' ? null : 'flat';
    },
    addResourceActiveTab() {
      return this.selectedTab === 'AddResources' ? null : 'flat';
    },
  },
};
</script>
<style></style>
