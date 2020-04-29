<template>
  <div id="manage-store">
    <h3>Administration du magasin :</h3>
    <p><button @click="openOrCloseStore()">{{store.isOpen ? 'Fermer le magasin' : 'Ouvrir le magasin'}}</button></p>
    <p>Nom du magasin :  <input type="text" v-model="store.name"/></p>
    <p>Magasin ouvert :  <input type="checkbox" v-model="store.isOpen"/></p>
  </div>
</template>

<script>
export default {
  name: 'ManageStore',
  props: {
    store: Object
  },
  model: {
    prop: 'store',
    event: 'storeChange'
  },
  methods: {
    openOrCloseStore() {
      this.store.isOpen = !this.store.isOpen;
      this.$emit('storeChange', this.store);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  #manage-store {
    background-color: aliceblue;
    padding: 10px;
  }
</style>
