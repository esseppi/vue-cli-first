<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <v-row v-for="(value, id) in coins" :key="value.id">
          <v-col>
            <div>{{ id }}</div>
          </v-col>
          <v-col>
            <div>{{ value.USD.PRICE }}</div>
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
    activeCoin: '',
    coins:[],
    errors: [],
  }),
  methods: {
    convert() {
      this.result = this.value.USD.PRICE * this.amount
    },

  },
  created() {
    axios.get('https://min-api.cryptocompare.com/data/pricemultifull?fsyms=LUNA,DOT,ETH,BTC&tsyms=USD')
    .then(response => {
      this.coins = response.data.DISPLAY
      // this.eth = response.data.DISPLAY.ETH.USD
      // this.btc = response.data.DISPLAY.BTC.USD
      // this.dot = response.data.DISPLAY.DOT.USD
      // this.luna = response.data.DISPLAY.LUNA.USD
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