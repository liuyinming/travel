<template>
    <div>
        <div class="search">
            <input class="search-input" type="text" placeholder="输入城市名或拼音" v-model="keyword"> 
        </div>
        <div class="search-content" ref="search" v-show="keyword">
            <ul >
                <li  class="search-item border-bottom"
                v-for="item of list" :key="item.id">{{item.name}}</li>
                <li  class="search-item border-bottom" v-show="hasNoData">没有找到匹配的城市</li>
            </ul>
        </div>
    </div>
</template>

<script>
import BScroll from 'better-scroll'
import { setTimeout } from 'timers';
import { clearTimeout } from 'timers';
export default {
    
  name: "CitySearch",
  props:{
      cities:Object
  },
  data(){
      return{
          keyword:'',
          list:[],
          timer:null,
      }
  },
  mounted(){
      this.scroll = new BScroll(this.$refs.search);
  },
  computed:{
     hasNoData (){
      return !this.list.length;
     }
  },
  watch:{
      keyword (){
          if (!this.keyword){
            this.list=[];
            return 
          }
          if(this.timer){
              clearTimeout(this.timer)
          }
        this.timer=setTimeout(()=>{
           const result=[];
           for(let i in this.cities){
               this.cities[i].forEach((value) => {
                   if(value.spell.indexOf(this.keyword)>-1||value.name.indexOf(this.keyword)>-1){
                      result.push(value);
                   }
               });
           }
           this.list=result;
        },100)
      }
  }
};
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/varibles.styl';

.search {
  height: 0.72rem;
  padding: 0 0.1rem;
  background: $bgColor;
  .search-input{
      box-sizing :border-box;
      width :100%;
      height :.62rem;
      padding :0 .1rem;
      line-height :.62rem;
      border-radius:.1rem; 
      text-align :center;
      color :#666;
  }
}
.search-content{
    z-index :1
    overflow hidden
    position :absolute
    top:1.58rem
    right :0
    bottom :0
    left :0
    background :#eee
    .search-item{
      line-height :.62rem
      padding :.2rem
      background :#fff
      color :#666
    }
}
</style>
