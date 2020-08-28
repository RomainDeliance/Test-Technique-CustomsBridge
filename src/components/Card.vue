<template>
  <v-row>
    <v-col cols="12" style=" width: 15vw; height: 30vh">
      <v-card style="width: 15vw; height: 30vh">
        <v-col style="display: flex; align-items: center">
          <country-flag :country="data.issuing_country"></country-flag>
          <span class="text-truncate">{{data.bti_ref}}</span>
        </v-col>
        <v-divider></v-divider>
        <v-col>
          <span v-if="data.description.length < 200">{{data.description}}</span>
          <span v-else>{{data.description.substring(0, 200) + "..."}}</span>
        </v-col>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>

  import CountryFlag from 'vue-country-flag';

export default {
  name: 'Card',
  props: {
    data: {},
  },
  components: {
    CountryFlag,
  }
}
</script>
