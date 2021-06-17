<template>
<section class="product">
  <loading v-model:active="isLoading">
    <img src="https://upload.cc/i1/2021/06/12/N7mIQ1.gif
" alt="loading">
  </loading>
  <div class="w-100 product-banner position-relative mb-13">
    <nav aria-label="breadcrumb" class="nav-breadcrumb">
      <ol class="breadcrumb">
        <li class="breadcrumb-item"><router-link :to="{ name: 'Home' }">首頁</router-link></li>
        <li class="breadcrumb-item"><router-link :to="{ name: 'Products' }">產品總覽</router-link></li>
        <li class="breadcrumb-item active" aria-current="page">{{ product.category }}</li>
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
          <li class="mb-7">
            <span class="badge bg-secondary rounded-pill h5 px-5 py-2">{{ product.category }}</span>
          </li>
          <li class="h6 mb-7">{{ product.description }}</li>
          <li>{{ product.content }}</li>
        </ul>
      </div>
    </div>
  </div>
</section>
</template>
<script>
import { mapGetters, mapActions } from 'vuex'
export default {
  data () {
    return {
      productId: ''
    }
  },
  computed: {
    ...mapGetters(['isLoading']),
    ...mapGetters('productModules', ['products', 'product'])
  },
  methods: {
    ...mapActions('productModules', ['getProducts', 'getProduct'])
  },
  created () {
    console.log(this.$route.params.id)
    this.productId = this.$route.params.id
    this.getProduct(this.productId)
  }
}
</script>
