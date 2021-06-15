<template>
  <div>
    <ul class="products-pagination modal-page">
      <li :class="{ 'disabled' : !pages.hasPage}">
        <a href="#" class="prev" @click.prevent="$emit('get-product', pages.currentPage - 1)">
          <i class="fa fa-chevron-left"></i>
            Previous
        </a>
      </li>
      <li v-for="page in pages.pageTotal" :key="page">
        <a href="#" @click.prevent="$emit('get-product', page)" :class="{ 'active' : page === pages.currentPage }">{{ page }}</a>
      </li>
      <li :class="{ 'disabled' : !pages.hasNext}">
        <a href="#" class="next" @click.prevent="$emit('get-product', pages.currentPage + 1)"> Next
          <i class="fa fa-chevron-right"></i>
        </a>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  data () {
    return {
      /*
      products: [], // 產品列表
      page: {
        dataLen: 0, // 全部資料長度
        pageTotal: 1, // 根據產品總筆數算出的總頁數
        currentPage: 1, // 當前頁數
        hasPage: false,
        hasNext: false
      },
      AllProducts: []
      */
    }
  },
  props: ['pages']
  /*
  methods: {
    getPageLen (nowPage = 1) {
      const vm = this
      const api = `${process.env.VUE_APP_APIPATH}/api/${process.env.VUE_APP_CUSTOMPATH}/products/all`
      vm.$http.get(api).then((res) => {
        console.log('產品 All 列表', res.data)
        if (res.data.success) {
          vm.products = res.data.products
          vm.page.dataLen = vm.products.length // 取得全部資料長度
          const perpage = 8 // 要顯示在畫面上的資料數量，預設每一頁只顯示五筆資料。
          vm.page.pageTotal = Math.ceil(vm.page.dataLen / perpage)
          if (nowPage > vm.page.pageTotal) {
            nowPage = vm.page.pageTotal
          }
          const minData = (nowPage * perpage) - perpage + 1
          const maxData = (nowPage * perpage)
          vm.AllProducts = []
          vm.products.forEach((item, index) => {
            const num = index + 1
            if (num >= minData && num <= maxData) {
              vm.AllProducts.push(item)
            }
          })
          console.log(vm.AllProducts)
        } else {
          vm.toastTopEnd(res.data.message, 'error')
        }
      })
    },
    getCurrentPage (page) {
      this.page.currentPage = page
      console.log(page, this.page.currentPage)
      this.getPageLen(page)
      if (page > 1) {
        this.page.hasPage = true
      }
      if (page < this.page.pageTotal) {
        this.page.hasNext = true
      } else if (page === this.page.pageTotal) {
        this.page.hasNext = false
      }
      console.log('可往前', this.page.hasPage)
      console.log('可往後', this.page.hasNext)
    }
  },
  created () {
    this.getPageLen()
  }
  */
}
</script>
