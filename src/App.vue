<template>
  <div id="app">
    <MyHeader title="购物车案例" color="white" />
    <MyGoods v-for="item in goodsList" :key="item.id" :goodsList="item" />
    <MyFooter :goodsList="goodsList" />
  </div>
</template>

<script>
import MyHeader from '#/MyHeader'
import MyGoods from '#/MyGoods'
import MyFooter from '#/MyFooter'
import axios from 'axios'

export default {
  name: 'App',
  data() {
    return {
      goodsList: []
    }
  },
  components: {
    MyHeader,
    MyGoods,
    MyFooter
  },
  created() {
    this.getGoodsList()
  },
  methods: {
    async getGoodsList() {
      const res = await axios({ url: '/api/cart' })
      // console.log(res)
      this.goodsList = res.data.list
    }
  }
}
</script>

<style lang="less">
#app {
  padding: 45px 0 50px;
}
</style>
