<template>
  <v-container>
    <HelloWorld></HelloWorld>
    <v-row>
      <v-col style="border: 1px" cols="12" lg="12" md="6" sm="3">
        {{data}}
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  data() {
    return {
      data: {},
    }
  },
  beforeMount() {
    this.getName();
  },
  methods: {
    async getName() {
      const res = await fetch('https://api.agify.io/?name=michael');
      const data = await res.json();
      this.data = data;
    }
  },
  components: {
    HelloWorld
  }
}
</script>

<style>
</style>
