
<template> 
  <Header @searchData="searchFunc"></Header>
  <Content :pageData="pageList" v-if="pageList.length"></Content>
  <Detail v-if="vShow"  :detailData="detailInfo"></Detail>
  <Footer></Footer>
</template>

<script>
import Header from './pages/Header.vue'
import Content from './pages/Content.vue'
import Detail from './pages/Detail.vue'
import Footer from './pages/Footer.vue'
import axios from 'axios'



export default {
  name: 'Home',
  props: {
    msg: String
  },
  components: {
    Header,
    Content,
    Detail,
    Footer
  },   
  data(){
    return {
        pageList: [],
        vShow:false,
        detailInfo:'',
        pageIndex:0
    }
  },
  mounted(){
    this.getHomeinfo(0);
  },
  methods:{
    /**
     * @description:  fetch content list data
     * @param {*}
     * @return {*}
     */    
    
    getHomeinfo(pageIndex){
      axios.get('https://rickandmortyapi.com/api/character/?page='+pageIndex).then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc(res){
      console.log(res);
      if(res.data){
         this.pageList = res.data.results;
      }
    },

      /**
     * @description:  Header search
     * @param {*}
     * @return {*}
     */    
    searchFunc(param){
      // console.log(param, 'param');
      this.getDataBySearch(param);
    },
    // search name function
    getDataBySearch(name){
      var _that = this
       axios.get('https://rickandmortyapi.com/api/character/?name='+ name)
       .then(function(res){
          //  console.log(res, 'Search Data');
          if(res.data){
            _that.pageList = res.data.results;
          }
       })
       .catch(function(error){
         alert(error)
       })
    },

      /**
     * @description:  fetch detail data
     * @param {*}
     * @return {*}
     */  
     getDetail(id){
      var _that = this
       axios.get('https://rickandmortyapi.com/api/character/'+ id)
       .then(function(res){
           console.log(res, 'get Data');
          if(res.data){
            _that.vShow = true;
            _that.detailInfo = res.data;
          }
       })
       .catch(function(error){
         alert(error)
       })
    },
    closeDetail(){
       this.vShow = false;
    },

      /**
     * @description:  Simple pagination
     * @param {*}
     * @return {*}
     */    
    showPre(){     
       console.log(  this.pageIndex);
       if( this.pageIndex < 1){
         return;
       } else {
        this.pageIndex = --this.pageIndex;
         this.getHomeinfo(this.pageIndex);
       }
    },
    showNext(){
       this.pageIndex = ++this.pageIndex;
       console.log(  this.pageIndex);
       this.getHomeinfo(this.pageIndex);
    },

   
  },
 
    
}
</script>

