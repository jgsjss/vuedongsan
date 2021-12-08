<template>
  <div class="black-bg" v-if="checkModal == true">
    <div class="white-bg">
      <img :src="products[clickNum].image" style="width: 100%" />
      <h4>{{ products[clickNum].title }}</h4>
      <p>{{ products[clickNum].content }}</p>
      <input type="number" v-model="month" />
      <p>{{ month }}개월 선택 : {{ products[clickNum].price * month }} 원</p>
      <button class="btn btn-primary" @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal",
  data() {
    return {
      month: 0,
    };
  },
  props: {
    products: Array,
    checkModal: Boolean,
    clickNum: Number,
  },
  watch: {
    month(a) {
      if (a > 18) {
        alert("최대 선택 기간은 18개월 입니다.");
        this.month = 18;
      }
      if (isNaN(a) == true) {
        alert("숫자만 입력 가능합니다.");
        this.month = 1;
      }
    },
  },
};
</script>

<style>
</style>