<template>
<div>
    <home-header></home-header>
    <home-swiper :list="swiperList"></home-swiper>
    <home-icon :list="iconList"></home-icon>
    <home-recommend :list="recommendList" ></home-recommend>
    <home-weekend :list="weekendList"></home-weekend>
</div>
</template>

<script>
import HomeHeader from './components/Header.vue'
import HomeSwiper from './components/Swiper.vue'
import HomeIcon from './components/Icon.vue'
import HomeRecommend from './components/Recommend.vue'
import HomeWeekend from './components/Weekend.vue'
import axios from 'axios'
import {mapStore, mapState} from 'vuex'
export default {
    name: 'Home',
    components:{
        HomeHeader,
        HomeSwiper,
        HomeIcon,
        HomeRecommend,
        HomeWeekend
    },
    data(){
        return{
            lastCity:'',
            swiperList:[],
            iconList:[],
            recommendList:[],
            weekendList:[]
        }
    },
    computed:{
       ...mapState(['city'])
    },
    methods:{
        getHomeInfo(){
        axios.get('/api/index.json?city=' + this.city).then(this.getHomeInfoSucc)  
        },
        getHomeInfoSucc(res){
           res=res.data;
            if (res.ret&&res.data){
                const data=res.data;
                this.swiperList=data.swiperList;
                this.iconList=data.iconList;
                this.recommendList=data.recommendList;
                this.weekendList=data.weekendList
            }
           
        }
    },
    mounted (){   //当页面初次加载的时候会执行
    this.lastCity=this.city;
    this.getHomeInfo()
    },
    activated (){ //当页面再次显示的时候会执行
    if(this.lastCity!==this.city){
        this.lastCity=this.city;
         this.getHomeInfo();
    }
    
    }
}
</script>

<style>

</style>
 