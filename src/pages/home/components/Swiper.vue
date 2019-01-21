<template>
    <div class="wrapper">
    <swiper :options="swiperOption" v-if="showSwiper" >
    <!-- slides -->
    <swiper-slide v-for="item of list" :key="item.id">
        <img class="swiper-image" :src="item.imgUrl">
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
    props:{
        list:Array
    },
    data (){
        return{
          swiperOption:{
              pagination:'.swiper-pagination',
              loop:true
          } 
        }
    },
    computed:{
        showSwiper(){
            return this.list.length
        }
    }
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
