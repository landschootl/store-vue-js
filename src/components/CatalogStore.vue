<template>
  <div id="catalog-store">
    <h3>Les produits en vente :</h3>
    <div v-for="(product, index) in products" :key="index">
      <span>{{product.name}} - {{product.priceHt}} € </span>
      <button @click="addProductToBasket(product)">ajouter à mon panier</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CatalogStore',
  data() {
    return {
      products: [
        {name: 'Banane', priceHt: 1.5},
        {name: 'Oeuf', priceHt: 2.2},
        {name: 'Kiwi', priceHt: 3.3},
        {name: 'Lait', priceHt: 0.9}
      ]
    }
  },
  methods: {
    addProductToBasket(product) {
      this.$emit('addProductToBasketEvent', product);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
