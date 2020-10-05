<template>
  <div>
    <the-header :title="'The Learning Resources App'"></the-header>
    <the-resource></the-resource>
  </div>
</template>

<script>
import TheHeader from './components/layouts/TheHeader';
import TheResource from './components/learning-resoures/TheResource';

export default {
  components: {
    TheHeader,
    TheResource
  },
  data() {
    return {
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The vue.js official guide',
          link: 'https://vuejs.org'
        },
        {
          id: 'google',
          title: 'Google',
          description: 'You need to learn how to google',
          link: 'https://google.com'
        }
      ]
    };
  },
  methods: {
    addResource(title, description, link) {
      const newResource = {
        id: Date.now().toString(),
        title,
        description,
        link
      };
      this.storedResources.unshift(newResource);
    },
    deleteResource(id) {
      const resIdx = this.storedResources.findIndex(res => res.id === id);
      this.storedResources.splice(resIdx, 1);
    }
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addResource,
      deleteResource: this.deleteResource
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
