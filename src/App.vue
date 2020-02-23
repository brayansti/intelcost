<template>
  <div id="app">
    <article class="bannerBox">
      <div class="bannerBox__logo">
        <img src="./assets/logo.png" alt="IntelCost">
      </div>
      <div class="bannerBox__image">
      </div>
      <div class="bannerBox__search searchBox">
          <input placeholder="Search Here" v-model="newsSearch" @keyup="changeInput" type="text">
      </div>
    </article>
    <div class="container mt40">
      <div class="row">
        <!-- Repeat Here -->
        <div class="col-md-4" v-for="(hit, $index) in dataFromAPI.hits" :key="$index">
          <item-box
            :likes=hit.likes
            :userImageURL=hit.userImageURL
            :user=hit.user
            :views=hit.views
            :webformatURL=hit.webformatURL
          ></item-box>
        </div>
      </div>
    </div>

    <!--  -->
  </div>
</template>

<script>
import axios from 'axios';
import itemBox from "./components/itemBox"

const apiData = {
  url : 'https://pixabay.com/api/?key=13119377-fc7e10c6305a7de49da6ecb25',
}

export default {
  name: 'app',
  components: {
    itemBox
  },
  data() {
    return {
      newsSearch: '',
      dataFromAPI: [],
    };
  },
  methods: {
    changeInput() {
      console.log('Changed')
    },
  },
  mounted: function(){
    // ↓↓↓ On mounted load default post ↓↓↓
    axios
        .get(apiData.url)
        .then(response => {
          this.dataFromAPI = response.data
        })
        .catch(error => console.log(error))
  }
  // computed:{
  //   number: function(){
  //     return parseInt(this.test)
  //   },
  // }
}
</script>

<style lang="scss">
@import "./scss/main.scss";
</style>
