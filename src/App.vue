<template>
  <v-container style="max-width: inherit; width: 95%;">
    <v-row>
      <v-text-field v-model="code" style="margin-right: 20px" placeholder="Taper votre code nomenclature"></v-text-field>
      <v-text-field v-model="rtc" placeholder="Décrivez votre RTC"></v-text-field>
    </v-row>
    <v-row>
      <v-col cols="12" lg="3" md="4" sm="6" v-for="item in data" :key="item.bti_ref">
        <Card :data="item"></Card>
      </v-col>
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
      data: {},
    }
  },
  beforeMount() {
    this.display();
  },
  watch: {
    code() {
      fetch("https://api.customsbridge.ai/ebti?filter_on_code")
      .then(response => response.json())
      .then(data => (this.data = data));
      console.log(this.data);
    },
    rtc() {
      fetch("https://api.customsbridge.ai/ebti?search")
      .then(response => response.json())
      .then(data => (this.data = data));
      console.log(this.rtc);
    }
  },
  methods: {
    display() {
      fetch("https://api.customsbridge.ai/ebti?limit=100")
      .then(response => response.json())
      .then(data => (this.data = data));
    }
  },
  components: {
    Card
  }
}
</script>

<style>
</style>
