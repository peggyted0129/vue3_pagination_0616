<template>
<section class="product">
  <div class="w-100 product-banner position-relative mb-13">
    <nav aria-label="breadcrumb" class="nav-breadcrumb">
      <ol class="breadcrumb">
        <li class="breadcrumb-item"><a href="#">Home</a></li>
        <li class="breadcrumb-item"><a href="#">Library</a></li>
        <li class="breadcrumb-item active" aria-current="page">Data</li>
      </ol>
    </nav>
    <div class="container">
      <div class="row">
        <div class="col-7">
          <div class="productPicture">
            <img :src="product.imageUrl" alt="productPicture">
          </div>
        </div>
        <div class="col-5"></div>
      </div>
    </div>
  </div>
</section>
</template>
<script>
export default {
  data () {
    return {
      isLoading: false,
      productId: '',
      product: {}
    }
  },
  methods: {
    getProduct (productId) {
      const vm = this
      vm.isLoading = true
      const api = `${process.env.VUE_APP_APIPATH}/api/${process.env.VUE_APP_CUSTOMPATH}/product/${productId}`
      vm.$http.get(api).then((res) => {
        console.log(res.data)
        vm.product = res.data.product
      })
    }
  },
  created () {
    console.log(this.$route.params.id)
    this.productId = this.$route.params.id
    this.getProduct(this.productId)
  }
}
</script>
