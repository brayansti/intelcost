<template>
  <div id="app">
    <article class="bannerBox">
      <div class="bannerBox__logo">
        <img src="./assets/logo.png" alt="IntelCost">
      </div>
      <div class="bannerBox__image">
      </div>
      <form class="container bannerBox__search" v-on:submit.prevent="onSearch">
        <div class="row">
          <div class="col-md-6">
            <div class="searchBox">
                <input placeholder="Search Here" v-model="searchName" @keyup="changeInput" type="text">
            </div>
          </div>
          <div class="col-md-6">
            <v-select 
              class="style-chooser" 
              label="label" 
              placeholder="Select category"
              v-model="searchSelect"
              :options="selectOptions">
            </v-select>
          </div>
        </div>
        <div class="row justify-content-center mt30">
          <div class="col-md-4">
            <button class="btn btn--square btn--square-full btn--purple" type="submit">Buscar</button>
          </div>
        </div>
      </form>
    </article>
    <div class="container mt40">
      <div class="row">
        <!-- Repeat Here -->
        <div class="col-md-4" v-for="(hit, $index) in dataFromAPI.hits" :key="$index">
          <item-box
            :pageURL=hit.pageURL
            :likes=hit.likes
            :userImageURL=hit.userImageURL
            :user=hit.user
            :views=hit.views
            :webformatURL=hit.webformatURL
            :comments=hit.comments
            :id=hit.id
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
import vSelect from 'vue-select'
import 'vue-select/dist/vue-select.css';

const apiData = {
  url : 'https://pixabay.com/api/',
  key: '13119377-fc7e10c6305a7de49da6ecb25',
  lang: 'es',
  exapleSearch : 'https://pixabay.com/api/?key=13119377-fc7e10c6305a7de49da6ecb25&lang=es&q=portatil&category=science'
}

export default {
  name: 'app',
  components: {
    itemBox,
    vSelect
  },
  data() {
    return {
      selectOptions: [
        {
          label: 'Todas',
          value: '',
        },
        {
          label: 'Science',
          value: 'science',
        },
        {
          label: 'Education',
          value: 'education',
        },
        {
          label: 'People',
          value: 'people',
        },
        {
          label: 'Feelings',
          value: 'feelings',
        },
        {
          label: 'Computer',
          value: 'computer',
        },
        {
          label: 'Buildings',
          value: 'buildings'
        },
      ],
      searchName: '',
      searchSelect: '',
      dataFromAPI: [],
    };
  },
  methods: {
    onSearch(){
      axios
      // https://pixabay.com/api/?key=13119377-fc7e10c6305a7de49da6ecb25&lang=es&q=portatil&category=science
      .get(`${apiData.url}?key=${apiData.key}&lang=${apiData.lang}&q=${this.searchName}&category=${this.searchSelect.value}`)
      .then(response =>{
        this.dataFromAPI = response.data
      })
      // .catch(error => console.log(error))
    },
    changeInput() {
    },
  },
  mounted: function(){
    // ↓↓↓ On mounted load default post ↓↓↓
    axios
        .get(`${apiData.url}?key=${apiData.key}&lang=${apiData.lang}`)
        .then(response => {
          this.dataFromAPI = response.data
        })
        // .catch(error => console.log(error))
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

  .style-chooser .vs__search::placeholder,
  .style-chooser .vs__dropdown-toggle,
  .style-chooser .vs__dropdown-menu {
    // width: 100%;
    // background: #dfe5fb;
    // border: none;
    // color: #394066;
    // padding: 10px;
    // @include fontSize(20);
    width: 100%;
    min-height: 44px;
    margin-top: 10px;
    border: none;
    border-bottom: 1px solid $gray-border;
    background-color: #fff;
    border-radius: 0;
    color: $gray-text;
    @include fontSize(16);
  }

  .style-chooser .vs__clear,
  .style-chooser .vs__open-indicator {
    fill: #394066;
  }
</style>
