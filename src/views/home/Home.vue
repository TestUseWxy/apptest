<template>
  <div id="home">
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
    <tab-control :titles="['流行', '新款', '精选']" 
              @tabClick="tabClick(index)"
              ref="tabControl1" 
              class="tab-control" v-show="isTabFixed"/>
    <scroll class="content" 
            ref="scroll" 
            :probe-type="3" 
            @scroll="contentScroll"
            :pull-up-load="true"
            @pullingUp="loadMore">
          <home-swiper :banners="banners"/>
          <recommend-view :recommends="recommends"/>
          <feature-view/>
          <tab-control :titles="['流行', '新款', '精选']" 
                        @tabClick="tabClick"
                        ref="tabControl2"/>
    </scroll>
  </div>
</template>

<script>
  import NavBar from '../../components/common/navbar/NavBar.vue'
  import HomeSwiper from '../../views/home/childComps/HomeSwiper.vue'
  import RecommendView from '../../views/home/childComps/RecommendView.vue'
  import FeatureView from './childComps/FeatureView.vue'
  import TabControl from '../../components/content/tabControl/TabControl.vue'
  import scroll from '../../components/common/scroll/Scroll.vue'

  import { getHomeMultidata } from '../../network/home'

  export default {
    name: 'Home',
    components: {
      NavBar,
      HomeSwiper,
      RecommendView,
      FeatureView,
      TabControl,
      scroll
    },
    data () {
      return {
        banners: [],
        recommends: [],
        isTabFixed:false,
        currentType: 'pop'
      }
    },
    methods:{
      tabClick(index){
        console.log(index);
      },
      contentScroll(){},
      loadMore(){}
    },
    created () {
      // 1.请求多个数据
      getHomeMultidata().then(res => {
        // this.result = res;
        this.banners = res.data.banner.list
        this.recommends = res.data.recommend.list
      })
    }
  }
</script>

<style scoped>
  #home {
    height: 100vh;
    position: relative;
  }

  .home-nav {
    background-color: var(--color-tint);
    color: #fff;
  }

  .content {
    overflow: hidden;

    position: absolute;
    top: 44px;
    bottom: 49px;
    left: 0;
    right: 0;
  }

  .tab-control {
    position: relative;
    z-index: 9;
  }
</style>
