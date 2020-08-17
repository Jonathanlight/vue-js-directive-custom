<template>
  <div id="app">
    <input v-color-border="['red', 'blue', 'green', 'black']" type="text" />
  </div>
</template>

<script>
import Vue from 'vue';

Vue.directive('colorBorder', {
  bind(el, binding, VNode, oldVNode) {
    console.log('bind')
    let i = 0;

    console.log(VNode, oldVNode);

    el.addEventListener('input', () => {
      const colors = binding.value;
      el.style.borderColor = colors[i % colors.length];
      i++;
    })
  },
  inserted() {
    console.log('inserted')
  },
  update() {
    console.log('update')
  },
  componentUpdated() {
    console.log('componentUpdated')
  },
  unbind() {
    console.log('unbind')
  },
});

export default {
  name: 'App',
  /*directives: {
    borderColor: (el) => {
      let i = 0;

      el.addEventListener('input', () => {
        const colors = ['red', 'blue', 'green', 'yellow'];
        el.style.borderColor = colors[i % 4];
        i++;
      })
    }
  },*/
  components: {
    
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
  height: 100vh;
}

input {
  outline: 0;
  display: block;
  width: 200px;
  margin: auto;
  margin-top: 150px;
  padding: 15px 20px;
}
</style>
