<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button-wrapper">
            <div class="button">{{this.currentCity}}</div>
          </div>
        </div>
      </div>
      <div class="title border-topbottom">热门城市</div>
      <div class="button-list">
        <div class="button-wrapper" v-for="item of hotCities" :key="item.id" 
        @click="handleCityClick(item.name)">
          <div class="button">{{item.name}}</div>
        </div>
      </div>
      <div class="area"  v-for="(item, key) of cities" :key="key" :ref="key" >
        <div class="title border-topbottom">{{key}}</div>   <!-- 这里的Key代表的是对象  -->
        <div class="item-list" v-for="innerItem of item" :key="innerItem.id" @click="handleCityClick(innerItem.name)">
          <div class="item border-bottom">{{innerItem.name}}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
import { readlink } from 'fs';
import {mapState, mapMutations} from 'vuex'
export default {
  name: "CityList",
  props:{
      hotCities:Array,
      cities:Object,
      letter:String,
  },
  methods:{
       handleCityClick(city){
         //this.$store.commit('changeCity',city);
         this.changeCity(city);
         this.$router.push('/');
       },
       ...mapMutations(['changeCity'])
  },
  computed:{
    ...mapState({
      currentCity:'city'
    })
  },
  mounted(){
      this.scroll = new BScroll(this.$refs.wrapper);
  },
  watch: {
      letter (){
          if(this.letter){
          const element=this.$refs[this.letter][0];
          this.scroll.scrollToElement(element);
          }
      }
  }
};
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/varibles.styl';

.border-topbottom {
  &:before {
    border-color: #ccc;
  }

  &:after {
    border-color: #ccc;
  }
}

.border-bottom {
  &:before {
    border-color: #ccc;
  }
}

.list {
  overflow: hidden;
  position: absolute;
  top: 1.58rem;
  right: 0;
  bottom: 0;
  left: 0;

  .title {
    line-height: 0.44rem;
    background: #eee;
    padding-left: 0.2rem;
    color: #666;
    font-size: 0.26rem;
  }

  .button-list {
    padding: 0.1rem 0.6rem 0.1rem 0.1rem;
    overflow: hidden;

    .button-wrapper {
      float: left;
      width: 33.33%;

      .button {
        margin: 0.1rem;
        padding: 0.1rem 0;
        text-align: center;
        border: 0.02rem solid #ccc;
        border-radius: 0.06rem;
      }
    }
  }

  .item-list {
    .item {
      line-height: 0.72rem;
      padding-left: 0.2rem;
    }
  }
}
</style>  
