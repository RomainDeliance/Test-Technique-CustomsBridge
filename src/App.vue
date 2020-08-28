<template>
  <v-container style="max-width: inherit; width: 95%;">
    <v-row>
      <v-text-field v-model="code" style="margin-right: 20px" placeholder="Taper votre code nomenclature"></v-text-field>
      <v-text-field v-model="rtc" placeholder="Décrivez votre RTC"></v-text-field>
    </v-row>
    <v-row>
        <Card></Card>
    </v-row>
  </v-container>
</template>

<script>
import Card from './components/Card.vue'

export default {
  name: 'App',
  data() {
    return {
      code: "",
      rtc: "",
      test: [],
    }
  },
  watch: {
    code() {
      console.log(this.code);
    },
    rtc() {
      console.log(this.rtc);
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
    Card
  }
}
</script>

<style>
</style>
