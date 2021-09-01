<template>
  <div class="row">
    <div class="card offset-2 col-md-3">
      <div class="card-body tex-center d-flex align-items-center flex-column">
        <img height="128" class="img-responsive text-center mb-3"
             :src="product.selectedImage == null ? '/src/assets/default.png' : product.selectedImage">
        <input id="deneme" ref="file" type="file" style="display: none;" @change="onChange($event)"
               class="form-control">
        <button class="btn btn-outline-secondary " type="button" @click="$refs.file.click()">Resim Seç</button>
      </div>
    </div>
    <div class="col-md-5">
      <div class="col-md-11 card">
        <div class="card-body">
          <div class="form-group">
            <label>Ürün Adı</label>
            <input type="text" class="form-control" placeholder="adını giriniz"
                   @input="$event=>{product.name=$event.target.value}">
          </div>
          <div class="row">
            <div class="form-group col-md-6">
              <label>Ürün Adeti</label>
              <input type="text" class="form-control" placeholder="adetini giriniz"
                     @input="$event=>{product.quantity=$event.target.value}">>
            </div>
            <div class="form-group col-md-6">
              <label>Ürün Fiyatı</label>
              <input type="text" class="form-control" placeholder="fiyatını giriniz"
                     @input="$event=>{product.price=$event.target.value}">>
            </div>
          </div>
          <button class="btn btn-outline-info btn-block" @click="submitHandler($event)">Ekle!</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AddProduct",
  props: ["products"],
  data() {
    return {
      product: {
        selectedImage: null,
        name: "",
        quantity: "",
        price: "",
      }

    }

  },
  methods: {
    onChange(e) {
      const file = e.target.files[0];
      this.product.selectedImage = URL.createObjectURL(file);

    },
    submitHandler(e) {
      e.preventDefault();
      if (this.products.length === 10) {
        alert("En fazla 10 ürün ekleyebilirsiniz.")
      } else {
        let newitem = {};
        Object.assign(newitem, this.product)
        console.log(newitem)
        this.products.push(newitem);
      }
    }
  }
}
</script>
