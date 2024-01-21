<template>
  <div v-for="(a, i) in products" :key="i">
    <img :src="a.image" class="room-img" />
    <h4
      @click="
        selectProduct(i);
        모달창열렸니 = true;
        누른거 = i;
      "
    >
      {{ a.title }}
    </h4>
    <p>{{ a.price }}</p>
    <button @click="increase(i)">허위매물신고</button>
    <span>신고수 : {{ 신고수[i] }}</span>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    모달창열렸니: Boolean,
    누른거: Number,
    products: Array,
    increase: Number,
    신고수: Array,
  },
};
</script>

<style></style>
