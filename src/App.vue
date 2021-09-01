<template>
  <div class="container">
    <h1 class="text-center">Ürün Ekleme Uygulaması</h1>
    <hr>
    <add-product :products="products"></add-product>
    <br><br>
    <div class="progress">
      <div class="progress-bar bg-info" role="progressbar" :style="{width:products.length*10+'%'}" aria-valuenow="50"
           aria-valuemin="0"
           aria-valuemax="100">
        {{ products.length }}/10
      </div>
    </div>
    <br><br>
    <h3 class="text-center">Eklenen Ürünlerin Listesi</h3>
    <hr>
    <div class="row product-container">
      <product v-for="product in products" :product="product"></product>


    </div>

  </div>


</template>

<script>
import AddProduct from "./AddProduct";
import Product from "./Product";

export default {
  data() {
    return {
      products: []
    }
  },
  components: {addProduct: AddProduct, product: Product}

}
</script>

<style>
body {
  background-color: aliceblue;
  padding-top: 20px;
  padding-bottom: 20px;
}

.card {
  margin-right: 5px;
  margin-bottom: 5px;
}

.card:last-child {
  margin-right: 0px;
}

.col-md-2 {
  max-width: 15.666667% !important;
}

.product-container {
  margin-left: 15px;
}

</style>

