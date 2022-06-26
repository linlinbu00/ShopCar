<template>
  <div class="my-counter">
    <button type="button" class="btn btn-light" @click="decrease">-</button>
    <input
      type="number"
      class="form-control inp"
      v-model.number="goodsList.goods_count"
    />
    <button
      type="button"
      class="btn btn-light"
      @click="goodsList.goods_count++"
    >
      +
    </button>
  </div>
</template>

<script>
export default {
  props: {
    goodsList: {
      type: Object,
      required: true
    }
  },
  computed: {},
  methods: {
    decrease() {
      if (this.goodsList.goods_count === 1) return
      this.goodsList.goods_count--
    }
  }
  // watch: {
  //   goodsList: {
  //     deep: true,
  //     immediate: true,
  //     handler(newVal) {
  //       if (newVal.goods_count < 1) {
  //         this.goods.goods_count = 1
  //       }
  //     }
  //   }
  // }
}
</script>

<style lang="less" scoped>
.my-counter {
  display: flex;
  .inp {
    width: 45px;
    text-align: center;
    margin: 0 10px;
  }
  .btn,
  .inp {
    transform: scale(0.9);
  }
}
</style>
