<template>
  <div class="menu">
    <!-- <a>Home</a>
    <a>Producets</a>
    <a>About</a> -->
    <a v-for="(item, index) in menu" :key="index">{{ item }}</a>
  </div>
  <!-- <div>
    <h4>{{ products[0] }}</h4>
  </div> -->

  <div v-for="(item, idx) in items" :key="idx">
    <h4>{{ item.name }}</h4>
    <p>{{ item.price }}만원</p>
    <button v-on:click="increase(idx)">허위매물신고</button> <span>신고수 : {{ item.report }} </span>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      신고수 : 0,
      menu: ["Home", "Producets", "About"],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
      price: ["50", "60", "70"],

      items: [
        {
          name: "역삼동원룸",
          price: "50",
          report : 0,
        },
        {
          name: "천호동원룸",
          price: "60",
          report : 0,

        },
        {
          name: "마포구원룸",
          price: "70",
          report : 0,

        },
      ],
    };
  },
  methods : {
    increase(idx){
      console.log('idx===================',idx)
      this.items[idx].report += 1
    }
  }
};
</script>

<style>
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
