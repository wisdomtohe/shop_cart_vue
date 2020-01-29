<template>
  <div class="container">
    <div class="row">
      <div class="col-md-7">
        <div class="row">
          <div class="col-md-6" v-for="product in products" :key="product.id">
            <product :estEnPanier="estEnPanier(product)" v-on:ajouter_au_pannier="ajouterAuPanier(product)" :product="product" ></product>
          </div>
        </div>
      </div>
      <div class="col-md-5 my-5">
        <panier v-on:pay="pay()" v-on:enlever="enlever($event)" :elements='panier'></panier >
      </div>
    </div>
  </div>
</template>

<script>

import products from "@/products.json";

import Product from "@/components/Product.vue";
import Panier from "@/components/Panier.vue";

export default {
  name: 'app',
  data(){
    return {
      products,
      panier:[]
    }
  },
  components: {
    Product,
    Panier
  },
  methods:{
    ajouterAuPanier(product){
      this.panier.push(product);
    },
    estEnPanier(product){
      const item = this.panier.find(item => item.id === product.id);
      if (item) {
        return true
      }
      return false
    },
    enlever(product){
      this.panier = this.panier.filter(element => element.id !== product.id)
    },
    pay(){
      this.panier =[]
      alert("Vous avez bien regle votre commande")
    }
  }
}
</script>

<style>
/* #app {

} */
body{
  background-color: #FBFBF8;
}
</style>
