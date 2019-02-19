<template>
    <div>
        <detail-banner :sightName="sightName"
        :bannerImg="bannerImg"
        :bannerImgs="bannerImgs"></detail-banner>
        <detail-header></detail-header>
        <div class="content">
            <detail-list :list="list"></detail-list>
        </div>
        
    </div>
</template>

<script>
import DetailBanner from "./components/Banner.vue"
import DetailHeader from "./components/Header.vue"
import DetailList from "./components/List.vue"
import axios from 'axios'
export default {
    name:"Detail",
    components:{
     DetailBanner,
     DetailHeader,
     DetailList
    },
    data(){
        return{
            sightName:'',
            bannerImg:'',
            bannerImgs:[],
            list:[],
            // list:[{
            //     title:'成人票',
            //     children:[{
            //         title:'成人三馆连票',
            //         children:[{
            //             title:'成人三馆连票-江南连锁店',
            //         }]
            //     },{
            //         title:'成人五馆连票'
            //     }]
            // },{
            //     title:'儿童票'
            // },{
            //     title:'学生票'
            // },{
            //     title:'特惠票'
            // },]
        }
    },
    methods:{
      getDetailInfo(){
        axios.get('/api/detail.json?id=' , {
            params:{
                id:this.$route.params.id
            }
        }).then(this.HandleGetDataSuccess)  
      },
      HandleGetDataSuccess(res){
           res=res.data;
            if (res.ret&&res.data){
                const data=res.data;
                this.sightName=data.sightName;
                this.bannerImg=data.bannerImg;
                this.bannerImgs=data.gallaryImgs;
                this.list=data.categoryList;
            }
           
        }
    },
    mounted(){
        this.getDetailInfo () 
    }
}
</script>

<style lang="stylus" scoped>
.content
   height :50rem
</style>
