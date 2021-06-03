<template>
  <div id="home">
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
    <home-swiper :banners="banners"/>
    <recommend-view :recommends="recommends"/>
    <feature-view></feature-view>
    <tab-control :titles="['流行','新款','精选']"
    class="tab-control"
    ></tab-control>
    <ul>
      <li>liebiao1</li>
      <li>liebiao2</li>
      <li>liebiao3</li>
      <li>liebiao4</li>
      <li>liebiao5</li>
      <li>liebiao6</li>
      <li>liebiao7</li>
      <li>liebiao8</li>
      <li>liebiao9</li>
      <li>liebiao10</li>
      <li>liebiao11</li>
      <li>liebiao12</li>
      <li>liebiao13</li>
      <li>liebiao14</li>
      <li>liebiao15</li>
      <li>liebiao16</li>
      <li>liebiao17</li>
      <li>liebiao18</li>
      <li>liebiao19</li>
      <li>liebiao20</li>
      <li>liebiao21</li>
      <li>liebiao22</li>
      <li>liebiao23</li>
      <li>liebiao24</li>
      <li>liebiao25</li>
      <li>liebiao26</li>
      <li>liebiao27</li>
      <li>liebiao28</li>
      <li>liebiao29</li>
      <li>liebiao30</li>
      <li>liebiao31</li>
      <li>liebiao32</li>
      <li>liebiao33</li>
      <li>liebiao34</li>
      <li>liebiao35</li>
      <li>liebiao36</li>
      <li>liebiao37</li>
      <li>liebiao38</li>
      <li>liebiao39</li>
      <li>liebiao40</li>
      <li>liebiao41</li>
      <li>liebiao42</li>
      <li>liebiao43</li>
      <li>liebiao44</li>
      <li>liebiao45</li>
      <li>liebiao46</li>
      <li>liebiao47</li>
      <li>liebiao48</li>
      <li>liebiao49</li>
      <li>liebiao50</li>
      <li>liebiao51</li>
      <li>liebiao52</li>
      <li>liebiao53</li>
      <li>liebiao54</li>
      <li>liebiao55</li>
      <li>liebiao56</li>
      <li>liebiao57</li>
      <li>liebiao58</li>
      <li>liebiao59</li>
      <li>liebiao60</li>
      <li>liebiao61</li>
      <li>liebiao62</li>
      <li>liebiao63</li>
      <li>liebiao64</li>
      <li>liebiao65</li>
      <li>liebiao66</li>
      <li>liebiao67</li>
      <li>liebiao68</li>
      <li>liebiao69</li>
      <li>liebiao70</li>
      <li>liebiao71</li>
      <li>liebiao72</li>
      <li>liebiao73</li>
      <li>liebiao74</li>
      <li>liebiao75</li>
      <li>liebiao76</li>
      <li>liebiao77</li>
      <li>liebiao78</li>
      <li>liebiao79</li>
      <li>liebiao80</li>
      <li>liebiao81</li>
      <li>liebiao82</li>
      <li>liebiao83</li>
      <li>liebiao84</li>
      <li>liebiao85</li>
      <li>liebiao86</li>
      <li>liebiao87</li>
      <li>liebiao88</li>
      <li>liebiao89</li>
      <li>liebiao90</li>
      <li>liebiao91</li>
      <li>liebiao92</li>
      <li>liebiao93</li>
      <li>liebiao94</li>
      <li>liebiao95</li>
      <li>liebiao96</li>
      <li>liebiao97</li>
      <li>liebiao98</li>
      <li>liebiao99</li>
      <li>liebiao100</li>
    </ul>

  </div>
</template>

<script>
  import HomeSwiper from './childComps/HomeSwiper'
  import RecommendView from './childComps/RecommendView'
  import FeatureView from './childComps/FeatureView'

  import NavBar from 'components/common/navbar/NavBar'
  import TabControl from 'components/content/tabControl/TabControl'

  import {getHomeMultidata, getHomeGoods} from 'network/home'
  
  export default {
    name: "Home",
    components:{
      HomeSwiper,
      RecommendView,
      FeatureView,
      NavBar,
      TabControl
    
    },
    data() {
      return {
        banners:[],
        recommends:[],
        goods:{
          'pop':{page: 0, list: []},
          'new':{page: 0, list: []},
          'sell':{page: 0, list: []},
        }
      } 
    },
    created() {
      this.getHomeMultidata()
      //请求商品数据
      this.getHomeGoods('pop')
      this.getHomeGoods('new')
      this.getHomeGoods('sell')
      
    },
    
    methods:{
      getHomeMultidata(){
        getHomeMultidata().then(res =>{
        this.banners = res.data.banner.list
        this.recommends = res.data.recommend.list
      })
      },
      getHomeGoods(type){
        const page = this.goods[type].page + 1
        getHomeGoods(type,page).then((res) => {
          this.goods[type].list.push(...res.data.list)
          this.goods[type].page += 1
        })
      }
    }
  }
</script>

<style scoped>
  #home {
  padding-top: 44px;
}
  .home-nav {
    background-color:var(--color-tint) ;
    color:#fff;
    position: fixed;
    left: 0;
    right: 0;
    top: 0;
    z-index: 9;
  }
  .tab-control {
    position:sticky;
    top:44px
  }
</style>
