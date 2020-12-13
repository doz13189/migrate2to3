<template>
  <div>

    <div id="example-1">
      <button v-on:click="counter += 1">Add 1</button>
      <p>The button above has been clicked {{ counter }} times.</p>
    </div>

    <div id="example-2">
      <button v-on:click="greet">Greet</button>
    </div>

    <div id="example-3">
      <button v-on:click="say('hi')">Say hi</button>
      <button v-on:click="say('what')">Say what</button>
    </div>

    <button v-on:click="warn('Form cannot be submitted yet.', $event)">
      Submit
    </button>

    <HelloWorld/>

    <!-- <SalutationName/> -->
    <SalutationName
      v-model:salutation="form.salutation"
      v-model:name="form.name"
    />
    <pre>{{ form }}</pre>

  </div>
</template>

<script>
import { reactive } from 'vue'

import HelloWorld from './components/HelloWorld.vue'
import SalutationName from './components/SalutationName.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    SalutationName
  },
  data() {
    return {
      counter: 0,
      name: 'Vue.js'
    }
  },
  methods: {
    greet: function (event) {
      alert('Hello ' + this.name + '!')
      console.log(event.target)

      if (event) {
        alert(event.target.tagName)
      }
    },
    say: function (message) {
      alert(message)
    },
    warn: function (message, event) {
      console.log('event', event)
      if (event) {
        event.preventDefault()
      }
      alert(message)
    }
  },
  setup () {
    const form = reactive({
      salutation: '',
      name: ''
    })

    return {
      form
    }
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
