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
  <div class="container mb-15">
    <div class="row mb-13">
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
          <li class="h5 mb-7">{{ product.description }}</li>
          <li class="h6 mb-7">{{ product.content }}</li>
          <li class="h6 mb-7 d-flex justify-content-between align-items-end">
            <p class="h4">售價 NT$ {{ product.price }}</p>
            <div class="d-flex flex-column justify-content-end">
              <!-- +、- 按鍵 -->
              <div class="input-group justify-content-start align-items-center mb-2" style="width:150px">
                <button type="button" class="input-group-text btn btn-theme" @click="cartBtn('minus')" :disabled="num === 1">
                  <i class="fas fa-minus"></i>
                </button>
                <input type="number" v-model.number="num" class="form-control text-center ps-7 m-0 cartNum" readonly>
                <button type="button" class="input-group-text btn btn-theme" @click="cartBtn('add')" :disabled="num === 10">
                  <i class="fas fa-plus"></i>
                </button>
              </div>
              <!-- 加入購物車 -->
              <button type="button" class="btn btn-theme hvr-bounce-to-right">
                <i class="fas fa-shopping-cart pe-3"></i>加入購物車
              </button>
            </div>
          </li>
        </ul>
      </div>
    </div>
    <div class="product-content mb-10">
      <h3>值得信賴的好品牌</h3>
    </div>
    <ul class="product-line">
      <li class="d-flex align-items-center">
        <div class="w-40">
          <img src="https://images.unsplash.com/photo-1567896079745-b0b7e5a47679?ixid=MnwxMjA3fDB8MHx0b3BpYy1mZWVkfDI1fGJvOGpRS1RhRTBZfHxlbnwwfHx8fA%3D%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60" alt="">
        </div>
        <div class="w-40 h-100 ms-20">
          <div class="product-left d-flex flex-column align-items-center justify-content-center p-13">
            <h4 class="h3 text-sgreen">經典暢銷品</h4>
            <p class="h5">累積熱銷超過 1300 座台北 101</p>
          </div>
        </div>
        <div class="product-linebadge">
          <i class="far fa-thumbs-up"></i>
        </div>
      </li>
      <li class="d-flex align-items-center">
        <div class="w-40 order-2">
          <img src="https://images.unsplash.com/photo-1567896079745-b0b7e5a47679?ixid=MnwxMjA3fDB8MHx0b3BpYy1mZWVkfDI1fGJvOGpRS1RhRTBZfHxlbnwwfHx8fA%3D%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60" alt="">
        </div>
        <div class="w-40 h-100 me-auto ms-9 order-1">
          <div class="product-right d-flex flex-column align-items-center justify-content-center p-13">
            <h4 class="h3 text-sgreen">肌膚最佳守門員</h4>
            <p class="h5">溫和淨膚無添加有害物質、不含防腐劑</p>
          </div>
        </div>
        <div class="product-linebadge">
          <i class="far fa-thumbs-up"></i>
        </div>
      </li>
      <li class="d-flex align-items-center">
        <div class="w-40">
          <img src="https://images.unsplash.com/photo-1567896079745-b0b7e5a47679?ixid=MnwxMjA3fDB8MHx0b3BpYy1mZWVkfDI1fGJvOGpRS1RhRTBZfHxlbnwwfHx8fA%3D%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60" alt="">
        </div>
        <div class="w-40 h-100 ms-20">
          <div class="product-left d-flex flex-column align-items-center justify-content-center p-13">
            <h4 class="h3 text-sgreen">精選歐盟法規認證成分</h4>
            <p class="h5">歐洲防過敏研究中心認證</p>
          </div>
        </div>
        <div class="product-linebadge">
          <i class="far fa-thumbs-up"></i>
        </div>
      </li>
       <li class="d-flex align-items-center">
        <div class="w-40 order-2">
          <img src="https://images.unsplash.com/photo-1567896079745-b0b7e5a47679?ixid=MnwxMjA3fDB8MHx0b3BpYy1mZWVkfDI1fGJvOGpRS1RhRTBZfHxlbnwwfHx8fA%3D%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60" alt="">
        </div>
        <div class="w-40 h-100 me-auto ms-19 order-1">
          <div class="product-right d-flex flex-column align-items-center justify-content-center p-13">
            <h4 class="h3 text-sgreen">醫師研發植萃配方</h4>
            <p class="h5">逾半世紀對敏弱肌地細心呵護</p>
          </div>
        </div>
        <div class="product-linebadge">
          <i class="far fa-thumbs-up"></i>
        </div>
      </li>
    </ul>
  </div>
</section>
</template>
<script>
import { mapGetters, mapActions } from 'vuex'
export default {
  data () {
    return {
      productId: '',
      num: 1
    }
  },
  computed: {
    ...mapGetters(['isLoading']),
    ...mapGetters('productModules', ['products', 'product'])
  },
  methods: {
    ...mapActions('productModules', ['getProducts', 'getProduct']),
    cartBtn (status) {
      if (status === 'add') {
        this.num += 1
      } else if (status === 'minus') {
        this.num -= 1
      }
    }
  },
  created () {
    console.log(this.$route.params.id)
    this.productId = this.$route.params.id
    this.getProduct(this.productId)
  }
}
</script>
