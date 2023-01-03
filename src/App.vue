<template>
  <!-- 모달창 -->
  <div class="black-bg" v-if="modalOpen">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <span>
        {{ oneroom_data[clickRoomIdx].content }}
      </span>
      <div class="close-btn">
        <div @click="handleClickClose" class="close-text">닫기</div>
      </div>
    </div>
  </div>

  <div class="menu">
    <!-- <a>Home</a>
    <a>Producets</a>
    <a>About</a> -->
    <a v-for="(item, index) in menu" :key="index">{{ item }}</a>
  </div>
  <!-- <div>
    <h4>{{ products[0] }}</h4>
  </div> -->

  <div v-for="(item, idx) in oneroom_data" :key="idx">
    <img class="main-img" :src="item.image" />
    <h4 @click="handleClickOpen(idx)">{{ item.title }}</h4>
    <p>{{ item.price }}만원</p>
    <!-- <button v-on:click="increase(idx)">허위매물신고</button>
    <span>신고수 : {{ item.report }} </span> -->
  </div>
</template>

<script>
import oneroom_data from "./assets/oneroom";
console.log("oneroom_data====================", oneroom_data);
export default {
  name: "App",
  components: {},
  data() {
    return {
      clickRoomIdx: 0,
      oneroom_data: oneroom_data,
      modalOpen: false,
      신고수: 0,
      menu: ["Home", "Producets", "About"],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
      price: ["50", "60", "70"],

      items: [
        {
          name: "역삼동원룸",
          price: "50",
          report: 0,
          image: "./assets/room0.jpg",
        },
        {
          name: "천호동원룸",
          price: "60",
          report: 0,
          image: "./assets/room1.jpg",
        },
        {
          name: "마포구원룸",
          price: "70",
          report: 0,
          image: "./assets/room2.jpg",
        },
      ],
    };
  },
  methods: {
    increase(idx) {
      console.log("idx===================", idx);
      this.items[idx].report += 1;
    },
    handleClickOpen(idx) {
      this.clickRoomIdx = idx;
      console.log("idx===================", idx);

      this.modalOpen = true;
    },
    handleClickClose() {
      console.log("handleClickClose===================");

      this.modalOpen = false;
    },
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
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 30%;
    background: white;
    border-radius: 8px;
    padding: 20px;
    top: 35%;
    position: fixed;
    left: 35%;
}
.close-btn {
  display: flex;
  justify-content: flex-end;
}
.close-text {
  padding: 10px;
  background-color: red;
  color: white;
  border-radius: 4px;
}
.main-img {
  width: 300px;
  height: 300px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background-color: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
</style>
