<template>
  <div>
    <div class="recommmend-title">热销推荐</div>
    <div> 
        <ul >
            <li class="item" v-for="item of list" :key="item.id">
                <div class="item-img-wrapper">
                    <img class="item-img" :src="item.imgUrl"/>
                </div>
                <div class="item-info">
                    <p class="item-title">{{item.title}}</p>
                    <p  class="item-desc">{{item.desc}}</p>
                    <button class="item-btn">查看详情</button>
                </div>
            </li>
        </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "HomeRecommend",
  props:{
     list:Array
  },
  // data (){
  //   return{
  //     recommendList:[{
  //       id:'01',
  //       imgurl:'http://img1.qunarzz.com/sight/p0/1712/18/18b8d3d36d30c17da3.img.jpg_200x200_e6518ecc.jpg',
  //       title:'武汉极地海洋游乐观',
  //       desc:'本测试报告能实现是否符合用户需本测试报告能实现是否符合用户需本测试报告能实现是否符合用户需'
  //     },
  //     {
  //       id:'02',
  //       imgurl:'http://img1.qunarzz.com/sight/p0/1712/18/18b8d3d36d30c17da3.img.jpg_200x200_e6518ecc.jpg',
  //       title:'武汉极地海洋游乐观',
  //       desc:'本测试报告能实现是否符合用户需本测试报告能实现是否符合用户需本测试报告能实现是否符合用户需'
  //     },
  //     {
  //       id:'03',
  //       imgurl:'http://img1.qunarzz.com/sight/p0/1712/18/18b8d3d36d30c17da3.img.jpg_200x200_e6518ecc.jpg',
  //       title:'武汉极地海洋游乐观',
  //       desc:'本测试报告能实现是否符合用户需本测试报告能实现是否符合用户需本测试报告能实现是否符合用户需'
  //     }]
  //   }
  // }
};
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/mixins.styl'
.recommmend-title
  margin-top :.2rem
  line-height :.8rem
  background :#eee
  text-text-indent :.2rem
.item
  overflow:hidden
  display:flex
  height :1.9rem
//   .item-img-wrapper
       .item-img
         width:1.9rem
         height:1.7rem
         padding :0.1rem
    .item-info
      flex:1
      padding:.1rem
      min-width :0
      .item-title
         line-height :.54rem
         font-size :.32rem
         ellipsis()
       .item-desc
         line-height :.54rem
         color :#ccc
         white-space: nowrap; 
         text-overflow:ellipsis;
         overflow:hidden;     
        .item-btn
          background :yellow
          padding :0,.1rem
          border-radius: .06rem
          color :#fff
</style>
