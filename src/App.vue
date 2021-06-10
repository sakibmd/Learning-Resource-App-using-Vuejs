<template>
  <div>
    <learning-resource
      v-for="res in storedResources"
      :key="res.id"
      :title="res.title"
      :description="res.description"
      :link="res.link"
    ></learning-resource>
  </div>
</template>
<script>
import LearningResource from './components/learning-resource/LearningResource.vue';
export default {
  components: {
    LearningResource
  },
  data() {
    return {
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
  }
};
</script>
