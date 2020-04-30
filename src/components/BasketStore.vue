<template>
  <div id="basket-store">
    <h3>Mon panier :</h3>
    <p>Prix total de mon panier TTC : {{totalPriceTtc}} €</p>
    <p>Dernière modification : {{lastUpdate}}</p>
    <div v-for="(product, index) in basket" :key="index">
      <span>{{product.name}} - {{product.priceHt}} € </span>
      <button @click="removeProductToBasket(index)">elenver de mon panier</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BasketStore',
  props: {
    basket: Array
  },
  data() {
    return {
      lastUpdate: 'no update'
    }
  },
  model: {
    prop: 'basket',
    event: 'changeBasketEvent'
  },
  computed: {
    totalPriceTtc() {
      return this.basket.length > 0
            ? this.basket
              .map(basket => basket.priceHt * 1.2)
              .reduce((totalPriceTtc, priceTtc) => totalPriceTtc + priceTtc)
              .toFixed(2)
            : 0;
    }
  },
  methods: {
    removeProductToBasket(indexProduct) {
      this.basket.splice(indexProduct, 1);
      this.$emit('changeBasketEvent', this.basket);
    }
  },
  watch: {
    basket() {
      const date = new Date();
      this.lastUpdate = `${date.getHours()}h${date.getMinutes()}m${date.getSeconds()}s`;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
