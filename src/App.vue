<template>
  <TransitionDemo msg="Welcome to Your Vue.js App"/>
  <!-- <TemplateTagDemo msg="Welcome to Your Vue.js App"/> -->
  <!-- <KeyAttributeDemo msg="Welcome to Your Vue.js App"/> -->
</template>

<script>
import TransitionDemo from './components/TransitionDemo.vue';
// import TemplateTagDemo from './components/TemplateTagDemo.vue';
// import KeyAttributeDemo from './components/KeyAttributeDemo.vue';

export default {
  name: 'App',
  components: {
    TransitionDemo: TransitionDemo,
    // TemplateTagDemo: TemplateTagDemo,
    // KeyAttributeDemo: KeyAttributeDemo
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
