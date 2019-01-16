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
              imgurl:'https://imgs.qunarzz.com/p/tts9/1710/ee/7d44297c48ebfe02.jpg_r_390x260x90_c3b80ff8.jpg'
          },{
              id:'002',
              imgurl:'https://imgs.qunarzz.com/p/tts3/1507/d3/2ea8d53597e8da.jpg_r_390x260x90_1dc7ed34.jpg'
          },{
              id:'003',
              imgurl:'https://imgs.qunarzz.com/p/tts2/1609/21/d547c74398480d02.jpg_r_390x260x90_63645dc4.jpg'
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

</style>
