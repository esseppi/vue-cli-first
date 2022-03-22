<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <v-row v-for="(value, id) in coins" :key="value.id">
          <v-col>
            <div>{{ id }}</div>
            <div>{{ value.id }}</div>
            <img :src="value.image.large">
            <div>{{ value.market_data.current_price.usd }}</div>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from "axios"
export default {
  name: 'HelloWorld',
  data: () => ({
    coins:[],
    errors: [],
  }),
  methods: {

  },
  created() {
    axios.get('https://api.coingecko.com/api/v3/coins/')
    .then(response => {
      this.coins = response.data
    }).catch(e => {
      this.errors.push(e)
    })
  }
}


</script>
<style scoped>
img{
  width: 50px;
  height: 50px;
}
</style>