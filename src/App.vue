<template>
  <div id="app">
    <search-bar v-on:changekeyword=sendkeyword></search-bar>
    <news-card v-bind:items="topten"></news-card>
    <naver-list v-bind:tophun="tophun"></naver-list>

  </div>
</template>

<script>
  import cleanStr from './add_js/cleanString'
  import child from './components/Child'
  import NaverList from './components/NaverList'
  import axios from 'axios'
  import SearchBar from './components/SearchBar'
  import NewsCard from './components/NewsCard'

  let clientId = "K99rkGyg42Jf0FBSTQgO";
  let clientSecret = "M0BbIqUL5F";

  export default {
    name: 'App',
    components: {
      child,
      NaverList,
      SearchBar,
      NewsCard,
    },
    data() {
      return {
        title: [],
        link: [],
        tophun: [],
        topten: [],
        parentKeyWord: "세종대",

      }
    },
    mounted() {
      this.search();
    },
    methods: {
      search: function () {
        axios({
          method: "get",
          url: "/naversearch",
          params: {
            query: this.parentKeyWord,
            display: "100"
          },
          crossDomain: true,
          headers: {
            "X-Naver-Client-Id": clientId,
            "X-Naver-Client-Secret": clientSecret
          }
        }).then((result) => {
          //console.log(result.data.items[50]);

          let news = result.data.items;

          console.log(news)

          for (let i in news) {
            var tmp = {
              title: cleanStr(news[i].title, "title"),
              link: (news[i].originallink)
            };
            this.tophun.push(tmp);
          }
          for (let i = 0; i < 10; i++) {
            console.log(news[i])
            var tmp = {
              title: cleanStr(news[i].title, "title"),
              link: (news[i].originallink),
              desc: cleanStr(news[i].description,"title")
            };
            this.topten.push(tmp);
          }
        })
      },
      sendkeyword: function (val) {
        this.tophun = [];
        this.topten = [];
        this.parentKeyWord = val;
        this.search();
      }
    },

  }
</script>

<style>
  #app {
    margin: 10px auto;
    width: 1000px;
  }
</style>
