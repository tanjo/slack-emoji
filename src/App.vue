<script lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import SlackEmoji from './components/SlackEmoji.vue'

export default {
  components: {
    HelloWorld,
    SlackEmoji
  },
  data() {
    return {
      currentComponent: 'HelloWorld'
    };
  },
};
</script>

<template>
  <button v-if="currentComponent !== 'HelloWorld'" @click="currentComponent = 'HelloWorld'">
    HelloWorld
  </button>
  <button v-if="currentComponent !== 'SlackEmoji'" @click="currentComponent = 'SlackEmoji'">
    SlackEmoji
  </button>
  <KeepAlive>
    <component v-bind:is="currentComponent" />
  </KeepAlive>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
