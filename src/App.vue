<template>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <!-- v-if : 조건식이 참일때만 보여줌 
    데이터에따라 UI가 어떻게 보일지 작성-->
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>{{ selectContent }}</p>
      <button @click="모달창열렸니 = false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="a in 메뉴들" :key="a">{{ a }}</a>
    <!-- v-for="작명 in 몇번반복" :key 안쓰면 에러남 
    변수 작명 2개까지 가능
    - 왼쪽 변수는 array내의 데이터
    - 오른쪽 변수는 1씩 증가하는 정수-->
  </div>

  <!-- 반복문  -->
  <div v-for="(a, i) in products" :key="a">
    <img :src="a.image" class="room-img" />
    <h4 @click="selectProduct(i)">{{ a.title }}</h4>
    <p>{{ a.price }}</p>
    <button @click="increase(i)">허위매물신고</button>
    <span>신고수 : {{ 신고수[i] }}</span>
  </div>

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

export default {
  name: "App",
  data() {
    return {
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
  components: {},
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
