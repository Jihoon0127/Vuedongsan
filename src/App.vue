<template>
  <div v-if="ture">안녕하세요</div>
  <div v-else>안녕하세요2</div>
  <!-- 위에있는 v-if가 참이 아니라면 v-else -->
  <!-- v-else-if : if문 연달아 여러개 쓰고싶을 경우 -->

  <Modal :products="products" :누른거="누른거" :모달창열렸니="모달창열렸니" />
  <!-- props 사용법 : 데이터 보내고 등록후 사용
  v-bind 와 : 같음 -->

  <div class="menu">
    <a v-for="a in 메뉴들" :key="a">{{ a }}</a>
    <!-- v-for="작명 in 몇번반복" :key 안쓰면 에러남 
    변수 작명 2개까지 가능
    - 왼쪽 변수는 array내의 데이터
    - 오른쪽 변수는 1씩 증가하는 정수-->
  </div>

  <Discount />
  <!-- 반복문  -->
  <!-- <div v-for="(a, i) in products" :key="i">
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
  </div> -->
  <Card
    :products="products"
    :누른거="누른거"
    :모달창열렸니="모달창열렸니"
    :increase="increase"
    :신고수="신고수"
  />

  <!-- 노가다 -->
  <div>
    <h4 class="red">{{ products[0] }}</h4>
    <!-- :속성 ="데이터이름" -->
    <p>{{ price1[0] }}</p>
    <button @click="increase">허위매물신고</button>
    <span>신고수 : {{ 신고수[0] }}</span>
    <!-- 버튼 클릭시 자바스크립트 실행하려면 기존방식 : onclick="" Vue방식 @click ="" 
    Vue는 데이터 변경시 HTML에 바로 반영
  @mouseover : 마우스 갖다댈떄-->
  </div>

  <div>
    <h4>{{ products[1] }}</h4>
    <p>{{ price1[1] }} 만원</p>
    <button @click="increase">허위매물신고</button>
    <span> 신고수 : {{ 신고수[1] }}</span>
  </div>

  <div>
    <h4>{{ products[2] }}</h4>
    <p>{{ price1[2] }} 만원</p>
    <button @click="increase">허위매물신고</button>
    <span>신고수 : {{ 신고수[2] }}</span>
  </div>
</template>
<!-- {{데이터 바인딩을 하는 이유}} 
1. HTML에 하드코딩해놓으면 나중에 변경이 어려움
2. Vue의 실시간 자동 렌더링-->
<script>
import oneroomdata from "./assets/oneroom";
import Discount from "./Discount.vue";
import Modal from "./Modal.vue";
import Card from "./Card.vue";

export default {
  name: "App",
  data() {
    return {
      누른거: 0,
      모달창열렸니: false,
      신고수: [0, 0, 0],
      price1: ["10", "20", "30"],
      products: oneroomdata,
      메뉴들: ["Home", "Shop", "About"],
      selectContent: null,
    };
  },
  methods: {
    //함수 만드는 공간
    increase(i) {
      this.신고수[i] += 1;
      // 함수안에서 데이터 쓸 땐 this.데이터명
    },
    selectProduct(i) {
      this.selectContent = this.products[i].content;
      this.모달창열렸니 = true;
    },
  },
  components: {
    Discount: Discount,
    Modal: Modal,
    Card: Card,
    // 컴포넌트화 방법 : 스크립트 아래 import, components에 정의
  },
};
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  background: black;
  position: fixed;
  padding: 2px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
.room-img {
  width: 300px;
  margin-top: 40px;
}
</style>
