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
  </div>
  <div class="container">
    <div class="row">
      <div class="col-5">
        <div class="productPicture">
          <img :src="product.imageUrl" class="p-3" alt="productPicture">
        </div>
      </div>
      <div class="col-7">
        <ul class="ms-7">
          <li><h2 class="product-title fw-bolder">{{ product.title }}</h2></li>
          <li>
            <span class="badge bg-secondary align-self-center">{{ product.category }}</span>
          </li>
          <li>{{ product.description }}</li>
          <li>{{ product.content }}</li>
        </ul>
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
