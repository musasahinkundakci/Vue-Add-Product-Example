<template>
  <div class="col-md-2 card">
    <img class="card-img-top" :src="product.selectedImage" alt="Card image cap">
    <div class="card-body">
      <h5 class="card-title">{{ product.name }}</h5>
      <small>
        <strong>Adet : </strong> {{ product.quantity }}
      </small>
      <br>
      <small>
        <strong>Fiyat : </strong> {{ product.price }}
      </small>
      <br>
      <small>
        <strong>Tutar : </strong> {{ product.price * product.quantity }}
      </small>
    </div>
  </div>
</template>

<script>
export default {
  name: "Product",
  props: ["product"]
}
</script>

