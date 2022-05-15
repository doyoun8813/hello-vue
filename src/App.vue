<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <h1>{{ language }}</h1>
  <p>{{ greeting }}</p>

  <h1>첨단 IT기기 쇼핑몰에 오신것을 환영합니다.</h1>
  <h3>{{ title }}</h3>
  <ul>
    <li>{{ products[0] }}</li>
    <li>{{ products[1] }}</li>
    <li>{{ products[2] }}</li>
  </ul>
  <h6>{{ copyright }}</h6>
  <p>{{ isUppercase ? subTitle.toUpperCase() : subTitle }}</p>

  
  <h3>상품목록</h3>
  <ul>
    <!-- <li v-for="(post, index) in posts" :key="index">
      상품명: {{post.id}} 가격{{post.title}} 출시년도 {{post.body}}
    </li> -->
  </ul>

  <starwars-header></starwars-header>
  <starwars-main></starwars-main>
  

  <button @click="buttonClicked()">최신상품 가져오기</button>
</template>

<script>
import axios from 'axios';
import StarwarsMain from './components/StarwarsMain.vue';
import StarwarsHeader from './components/StarwarsHeader.vue';

export default {
  components: { StarwarsMain, StarwarsHeader },
  name: 'App',
  // created() {
  //   axios.get('http://jsonplaceholder.typicode.com/posts')
  //   .then(result => {
  //     this.posts = result.data;
  //     console.log(result.data);
  //   });
  // },
  created() {
    // axios.get('https://swapi.dev/api/films')
    // .then(result => {
    //   console.log(result.data.results);
    //   this.films = result.data.results;
    // });
    this.getData();
  },
  methods: {
    buttonClicked(){
      axios.get('http://jsonplaceholder.typicode.com/posts')
      .then(result => {
        this.posts = result.data;
        console.log(result.data);
      });
    },
    async getData(){
      axios.get('https://swapi.dev/api/films')
      .then(result => {
        console.log(result.data.results);
        this.films = result.data.results;
      });
    }
  },
  data() {
    return {
      greeting: 'gg 반가워요',
      language: 'vue.js',
      title: '상품목록',
      products: ['아이폰13', '갤럭시22', '노트북(맥북 최신형'],
      copyright: 'Copyright',
      subTitle: 'My Component',
      isUppercase: true,
      posts: [],
      films: [],
      products2: [
        {
          productName: 'iPhone13',
          price: 140000,
          productDate: 2021,
        },
        {
          productName: 'Galaxi',
          price: 130000,
          priductDate: 2022,
        },
        {
          productName: 'Monitor',
          price: 10000,
          priductDate: 2000,
        },
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1{
  color: royalblue;
}
p{
  font-style: italic;
}
</style>
