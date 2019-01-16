<template>
    <div class="wrapper">
    <swiper :options="swiperOption" >
    <!-- slides -->
    <swiper-slide v-for="item of swiperList" :key="item.id">
        <img class="swiper-image" :src="item.imgurl">
    </swiper-slide>
   
    <!-- Optional controls -->
    <div class="swiper-pagination"  slot="pagination"></div>
    <!-- <div class="swiper-button-prev" slot="button-prev"></div>
    <div class="swiper-button-next" slot="button-next"></div> -->
    </swiper>
    </div>
</template>

<script>
export default {
    name : 'HomeSwiper',
    data (){
        return{
          swiperOption:{
              pagination:'.swiper-pagination',
              loop:true
          } ,
          swiperList:[{
              id:'001',
              imgurl:'http://img1.qunarzz.com/piao/fusion/1812/d6/daa880b254940402.jpg_750x200_b114308a.jpg'
          },{
              id:'002',
              imgurl:'http://img1.qunarzz.com/piao/fusion/1811/31/da037478f37cf202.jpg_750x200_fe28d396.jpg'
          },{
              id:'003',
              imgurl:'http://img1.qunarzz.com/piao/fusion/1811/7c/8e5c4ab8ee8b7402.jpg_750x200_dd7a38dd.jpg'
          }] 
        }
    },
    // computed:{
    //     swiper() {
    //     return this.$refs.mySwiper.swiper
    //   }
    // },
    // mounted() {
    //   // current swiper instance
    //   // 然后你就可以使用当前上下文内的swiper对象去做你想做的事了
    //   console.log('this is current swiper instance object', this.swiper)
    //   this.swiper.slideTo(3, 1000, true)
    // }
}
</script>

<style lang="stylus" scoped>
.wrapper>>> .swiper-pagination-bullet-active
  background :#fff
.wrapper
  overflow 
  width: 100%
  height:0
  padding-bottom :31.25%
  .swiper-image
     width : 100%
     height :120px
</style>
