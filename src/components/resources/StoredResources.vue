<template>
  <div>
    <ul>
      <LearningResource
        v-for="storedResource in storedResources"
        :key="storedResource.id"
        :resource="storedResource"
      />
    </ul>
  </div>
</template>
<script>
import LearningResource from './LearningResource.vue';

export default {
  inject: ['storedResources'],
  components: { LearningResource },
};
</script>
<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>
