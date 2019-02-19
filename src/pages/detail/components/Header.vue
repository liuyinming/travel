<template>
    <div>
        <router-link to="/" class="abs" v-show="ShowAbs">
            <div class="iconfont abs-iconfont">&#xe624;</div>
        </router-link>
        <div class="header-fixed" v-show="!ShowAbs">
            城市选择
          <router-link to="/">
             <div class="iconfont header-back">&#xe624;</div>
          </router-link>
        </div>
    </div>
</template>

<script>
export default {
    name:'DetailHeader',
    data(){
        return {
            ShowAbs:true,
        }
    },
    methods:{
      HandleScroll () {
       const top=document.documentElement.scrollTop
       if(top>60){
           this.ShowAbs=false
       }else{
           this.ShowAbs=true
       }
      }
    },
    activated(){
        window.addEventListener('scroll',this.HandleScroll)
    }
}
</script>

<style lang="stylus" scoped>
.abs
  position : absolute
  left 0.2rem
  top:.2rem
  width :.8rem
  height :.8rem
  text-align :center
  line-height :.8rem
  border-radius :50%
  background :rgba(0, 0, 0, 1)
  .abs-iconfont
     color :#fff
     font-size :.4rem
.header-fixed {
  position :fixed;
  top:0;
  left:0;
  right:0;
  overflow: hidden;
  height: 0.86rem;
  line-height: 0.86rem;
  text-align: center;
  color: #fff;
  background: #00bcd4;
  .header-back {
     position: absolute;
     top: 0;
     left: 0;
     width: 0.64rem;
     text-align: center;
     font-size: 0.4rem;
     color :#fff
  }
}
</style>
