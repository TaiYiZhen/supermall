<template>
  <div id="home">
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
    <home-swiper :banners="banners"/>
    <recommend-view :recommends="recommends"/>
    <feature-view/>
    <tab-control :titles="['流行','新款','精选']"/>
    <h1>--------------</h1>
    <h1>--------------</h1>
    <h1>--------------</h1>
    <h1>--------------</h1>
    <h1>--------------</h1>
    <h1>--------------</h1>
    <h1>--------------</h1>
    <h1>--------------</h1>
    <h1>--------------</h1>
    <h1>--------------</h1>
    <h1>--------------</h1>
    <h1>--------------</h1>
  </div>
</template>

<script>
  import NavBar from 'components/common/navbar/NavBar';
  import tabControl from 'components/content/tabControl/tabControl'

  import HomeSwiper from './childComps/HomeSwiper';
  import RecommendView from './childComps/RecommendView';
  import FeatureView from './childComps/FeatureView.vue'

  import {getHomeMultidata} from "network/home";

  export default {
    name: "Home",
    components: {
      NavBar,
      HomeSwiper,
      RecommendView,
      FeatureView,
      tabControl
    },
    data(){
      return{
        banners:[],
        recommends:[],
        goods:{
          'pop':{page:0,list:[]},
          'news':{page:0,list:[]},
          'sell':{page:0,list:[]},
        }
      }
    },
    created(){
      //1.请求多个数据
     getHomeMultidata().then(res => {
       // this.result = res;
       this.banners = res.data.banner.list;
       this.recommends = res.data.recommend.list;
     })
    }
  }
</script>

<style scoped>
  #home{
    padding-top: 44px;
  }
  .home-nav{
    background-color: var(--color-tint);
    color: white;

    position: fixed;
    left: 0;
    right: 0;
    top:0;
    z-index: 9;
  }

  .tab-control{
    position: sticky;
    top: 44px;
  }
</style>
