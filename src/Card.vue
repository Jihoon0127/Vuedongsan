<template>
  <div>
    <img :src="원룸.image" class="room-img" />
    <h4
      @click="send"
      
    >
    <!-- 제목을 누를떄 원룸.id 담아서 메세지 전달 -->
    <!-- 부모에게 데이터 보낼때 $emit('작명', 데이터 ) -->
      {{ 원룸.title }}
    </h4>
    <p>{{ 원룸.price }}원</p>
    <!-- <button @click="increase(i)">허위매물신고</button>
    <span>신고수 : {{ 신고수[i] }}</span> -->
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    
    원룸: Object,
    
  },
  methods :{
    send(){
      this.$emit('openModal', this.원룸.id)
    }
  },
};
</script>

<style></style>
