<template>
  <div>
    <div class="weekend-title">周末去哪</div>
    <div> 
        <ul >
            <li class="item" v-for="item of list" :key="item.id">
                <div class="item-img-wrapper">
                    <img class="item-img" :src="item.imgUrl"/>
                </div>
                <div class="item-info">
                    <p class="item-title">{{item.title}}</p>
                    <p  class="item-desc">{{item.desc}}</p>
                </div>
            </li>
        </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "HomeWeekend",
  props:{
    list: Array
  }
  // data (){
  //   return{
  //     recommendList:[{
  //       id:'01',
  //       imgurl:'http://img1.qunarzz.com/sight/source/1505/d5/abe8a48a6ef8bf.jpg_r_640x214_7c41cc81.jpg',
  //       title:'武汉极地海洋游乐观',
  //       desc:'本测试报告能实现是否符合用户'
  //     },
  //     {
  //       id:'02',
  //       imgurl:'http://img1.qunarzz.com/sight/source/1711/4f/59f533696344fe.jpg_r_640x214_f8aa8c8f.jpg',
  //       title:'武汉极地海洋游乐观',
  //       desc:'本测试报告能实现是否符合用户需本测'
  //     },
  //     {
  //       id:'03',
  //       imgurl:'http://img1.qunarzz.com/sight/source/1811/6d/5afbf529076ef6.jpg_r_640x214_7414b151.jpg',
  //       title:'武汉极地海洋游乐观',
  //       desc:'本测试报告能实现'
  //     }]
  //   }
  // }
};
</script>
<style lang="stylus" scoped>
@import '~@/assets/styles/mixins.styl'
.weekend-title
  line-height :.8rem
  background :#eee
  text-text-indent :.2rem
.item-img-wrapper
    overflow :hidden
    height :0
    padding-bottom:37.09%
    .item-img
        width:100%
.item-info
    padding:.1rem
    .item-title
        line-height :.54rem
        font-size :.32rem
        ellipsis()
    .item-desc
        line-height :.4rem
        color :#ccc
</style>
