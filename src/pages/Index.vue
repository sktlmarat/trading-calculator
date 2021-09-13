<template>
  <q-page class="q-pt-md">
    <div class="row justify-center">
      <img
        alt="Bullish logo"
        src="~assets/main_page.png"
        style="height: 100px; width: auto"
      >
    </div>

    <div class="row flex justify-center q-col-gutter-md q-mt-md">
      <div class="col-2">
        <q-input outlined v-model="buy_price" label="Buy price">
          <template v-slot:append>
            <q-icon name="attach_money" />
          </template>
        </q-input>
      </div>
      <div class="col-2">
        <q-input outlined v-model="sell_price" label="Sell price">
          <template v-slot:append>
            <q-icon name="attach_money" />
          </template>
        </q-input>
      </div>
      <div class="col-2">
        <q-input outlined v-model="shares" label="Shares" />
      </div>
      <div class="col-2">
        <q-chip v-if="revenue" :color="revenue > 0 ? 'green' : 'red'" style="height:30px" class="text-white">
          {{ (revenue > 0 ? '+ ' : '') + revenue + ' $' }}
        </q-chip>
      </div>
    </div>
  </q-page>
</template>

<script>
export default {
  name: 'PageIndex',
  data () {
    return {
      buy_price: null,
      sell_price: null,
      shares: null
    }
  },
  computed: {
    revenue () {
      if (this.buy_price && this.sell_price && this.shares) {
        return (this.sell_price * this.shares) - (this.buy_price * this.shares)
      }
      return null
    }
  }
}
</script>
