<template>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <!-- v-if : 조건식이 참일때만 보여줌 
    데이터에따라 UI가 어떻게 보일지 작성-->
    <div class="white-bg">
      <h4>{{ products[누른거].title }}</h4>
      <p>{{ products[누른거].content }}</p>
      <Discount />
      <!-- <button @click="모달창열렸니 = false">닫기</button> -->
      <button @click="$emit('closeModal', false)">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal",
  props: {
    products: Array,
    누른거: Number,
    모달창열렸니: Boolean,
  },
  data() {
    return {};
  },
};
</script>

<style></style>
