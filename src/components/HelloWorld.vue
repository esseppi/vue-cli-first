<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <div>{{ cryptos }}</div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from "axios"
export default {
  name: 'HelloWorld',

  data: () => ({
    cryptos: [],
    errors: [],
  }),
  created() {
    axios.get('https://min-api.cryptocompare.com/data/pricemulti?fsyms=BTC,ETH&tsyms=USD,EUR')
    .then(response => {
      this.cryptos = response.data
      console.log(response)
    })

  }
}


</script>
