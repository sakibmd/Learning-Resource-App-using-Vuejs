<template>
  <div>
    <the-header title="Remember Me"></the-header>
    <stored-resources :resources="storedResources"></stored-resources>
  </div>
</template>
<script>
import StoredResources from './components/learning-resource/StoredResources.vue';
import TheHeader from './components/layouts/TheHeader.vue';
export default {
  components: {
    StoredResources,
    TheHeader
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

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}

</style>
