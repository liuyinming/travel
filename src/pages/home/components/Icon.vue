<template>
  <div class="icons">
    <swiper>
      <swiper-slide v-for="(page,index) of pages" :key="index">
        <div class="icon" v-for="item of page" :key="item.id">
          <router-link to="/Good">
            <div class="icon-image">
              <img class="icon-imgcontent" :src="item.imgUrl">
              <p class="icon-desc">{{item.desc}}</p>
            </div>
          </router-link>
        </div>
      </swiper-slide>
    </swiper>
  </div>
</template>

<script>
export default {
  name: "HomeIcon",
  props:{
    list:Array
  },
  methods:{
    HandleShow(){
          alert("王者冲，真滴帅")
    }
  },
  // data() {
  //   return {
  //     iconList: [
  //       {
  //         id: "01",
  //         iconurl:
  //           "http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png",
  //         icondesc: "景点门票"
  //       },
  //       {
  //         id: "02",
  //         iconurl:
  //           "http://img1.qunarzz.com/piao/fusion/1804/ff/fdf170ee89594b02.png",
  //         icondesc: "武汉必游"
  //       },
  //       {
  //         id: "03",
  //         iconurl:
  //           "http://img1.qunarzz.com/piao/fusion/1803/95/8246f27355943202.png",
  //         icondesc: "游乐场"
  //       },
  //       {
  //         id: "04",
  //         iconurl:
  //           "http://img1.qunarzz.com/piao/fusion/1803/b6/37560ece9c62b502.png",
  //         icondesc: "城市观光"
  //       },
  //       {
  //         id: "05",
  //         iconurl:
  //           "http://img1.qunarzz.com/piao/fusion/1803/50/26ffa31b56646402.png",
  //         icondesc: "海洋馆"
  //       },
  //       {
  //         id: "06",
  //         iconurl:
  //           "http://img1.qunarzz.com/piao/fusion/1804/5a/13ceb38dcf262f02.png",
  //         icondesc: "一日游"
  //       },
  //       {
  //         id: "07",
  //         iconurl:
  //           "http://img1.qunarzz.com/piao/fusion/1811/f6/e54fad3ea337b02.gif",
  //         icondesc: "年终大促"
  //       },
  //       {
  //         id: "08",
  //         iconurl:
  //           "http://img1.qunarzz.com/piao/fusion/1803/b1/528a9e80403b8c02.png",
  //         icondesc: "武汉欢乐谷"
  //       },
  //       {
  //         id: "09",
  //         iconurl:
  //           "http://img1.qunarzz.com/piao/fusion/1803/50/26ffa31b56646402.png",
  //         icondesc: "极地海洋"
  //       },
  //       {
  //         id: "10",
  //         iconurl:
  //           "http://img1.qunarzz.com/piao/fusion/1803/20/831d62d2e1c7be02.png",
  //         icondesc: "名胜古迹"
  //       }
  //     ]
  //   };
  // },
  computed: {
    pages() {
      const pages = [];
      this.list.forEach((item, index) => {
        const page = Math.floor(index / 8);
        if (!pages[page]) {
          pages[page] = [];
        }
        pages[page].push(item);
      });
      return pages;
    }
  }
};
</script>

<style lang="stylus" scoped>
.icons>>>.swiper-container {
  height: 0;
  padding-bottom: 50%;
  margin-top: 0.1rem;

  .icon {
    position: relative;
    overflow: hidden;
    float: left;
    width: 25%;
    height: 0;
    padding-bottom: 25%;

    .icon-image {
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0.44rem;
      box-sizing: border-box;
      padding: 0.1rem;

      .icon-imgcontent {
        display: block;
        margin: 0 auto;
        height: 100%;
      }

      .icon-desc {
        position: absolute;
        left: 0;
        right: 0;
        bottom: 0;
        height: 0.44rem;
        line-height: 1.2rem;
        text-align: center;
      }
    }
  }
}
</style>
