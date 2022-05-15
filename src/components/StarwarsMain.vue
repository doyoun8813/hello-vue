<template>
    <h3>상품목록</h3>
  <ul>
    <li v-for="film in films" :key="film.episode_id">
      상품명: {{film.title}} 가격{{film.episode_id}} 출시년도 {{film.producer}}
    </li>
  </ul>
  <button @click="buttonClicked()">최신상품 가져오기</button>
</template>

<script>
import axios from 'axios';

export default {
    created() {
        this.getData();
    },
    methods: {
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
            films: [],
        }
    },
}
</script>

<style>

</style>