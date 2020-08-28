<template>
  <v-row>
    <v-col style="height: 40vh">
      <v-card style="height: 37vh">
        <v-col style="display: flex; align-items: center">
          <country-flag :country="data.issuing_country"></country-flag>
          <span class="text-truncate">{{data.bti_ref}}</span>
        </v-col>
        <v-divider></v-divider>
        <v-col>
          <span v-if="data.description.length < 200">{{data.description}}</span>
          <span v-else>{{data.description.substring(0, 200) + "..."}}</span>
          <v-img v-if="data.file_urls" :src="data.file_urls[0]" height="200px"></v-img>
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
