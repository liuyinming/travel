<template>
    <div>
        <div class="banner" @click="HandleBannerClick">
            <img class="banner-img" :src="bannerImg"/> 
            <div class="banner-info">
                <div class="banner-title">
                {{this.sightName}}
                </div>
                <div class="banner-number">
                    <span class="iconfont">&#xe67f;</span>
                    {{this.bannerImgs.length}}
                </div>
            </div>
        </div>
        <common-gallary :imgs="bannerImgs" v-show="ShowGallary" @close="HandleBannerClose"></common-gallary>
    </div>
</template>

<script>
import CommonGallary from 'common/gallary/Gallary.vue'
export default {
    name:"DetailBanner",
    components:{
        CommonGallary
    },
    props:{
        sightName:String,
        bannerImg:String,
        bannerImgs:Array
    },
    data () {
        return {
            ShowGallary:false,
        }
    },
    methods:{
        HandleBannerClick (){
            this.ShowGallary=true
        },
        HandleBannerClose(){
          this.ShowGallary=false  
        }
    }
}
</script>

<style lang="stylus" scoped>
.banner
  position relative
  overflow hidden
  height: 0
  padding-bottom:55%
  .banner-img
     width :100%
  .banner-info
     display :flex
     position :absolute
     left: 0
     right:0
     bottom:0
     line-height: .6rem
     color :#fff
     .banner-title
         font-size :.32rem
         padding :0 .2rem
         flex:1
     .banner-number
         padding :0 .4rem
         margin-top :.14rem
         height :.32rem
         line-height :.32rem
         border-radius: 0.2rem
         background: rgba(0, 0, 0, .8)
         font-size :.24rem
         .iconfont
            font-size :.24rem


</style>
