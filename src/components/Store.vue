<template>
  <div id="store">
    <div class="bloc">
      <div class="sub-bloc">
        <img src="https://img.pngio.com/shop-icon-png-175739-free-icons-library-store-icon-png-1024_1024.jpg" id="img-store"/>
        <h1>{{fullName}}</h1>
        <!--    <h2 class="open" v-if="store.isOpen">Magasin : open</h2>-->
        <!--    <h2 class="close" v-else>Magasin : close</h2>-->
        <h2 v-bind:class="{ 'open': store.isOpen, 'close': !store.isOpen }">Magasin : {{store.isOpen ? 'Open' : 'Close'}}</h2>
        <ManageStore v-model="store"></ManageStore>
      </div>
      <div class="sub-bloc">
        <CatalogStore @addProductToBasketEvent="addProductToBasket($event)"></CatalogStore>
        <BasketStore v-model="basket"></BasketStore>
      </div>
    </div>
  </div>
</template>

<script>
import ManageStore from "./ManageStore";
import CatalogStore from "./CatalogStore";
import BasketStore from "./BasketStore";

export default {
  name: 'Store',
  components: {
    BasketStore,
    CatalogStore,
    ManageStore
  },
  data() {
    return {
      store: {
        name: 'Fred',
        isOpen: false
      },
      basket: []
    }
  },
  computed: {
    fullName() {
      return `Magasin de ${this.store.name}`;
    }
  },
  methods: {
    addProductToBasket(product) {
      this.basket.push(product);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  #store {
    height: 100%;
  }

  .bloc {
    width: calc(50vw - 43px);
    float: left;
    margin: 12px;
    border: thick double #32a1ce;
  }

  .sub-bloc {
    width: calc(25vw - 52px);
    float: left;
    margin: 15px;
  }

  .open {
    color: green;
  }

  .close {
    color: red;
  }

  #img-store {
    width: 30%;
  }
</style>
