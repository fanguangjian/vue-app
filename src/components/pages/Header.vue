<template>
  <div class="header">  
    <div class="header-left">    
       <span class="iconfont icon-Homehomepagemenu"></span>
       <span class="ilume">ilume</span>     
    </div>
    <div class="header-input">
      <span class="iconfont icon-search" ></span>
      <input class="search-input" type="text" placeholder="Please enter name" 
      v-model="nameValue" @keyup.enter="searchName()"/> 
    </div>
     <div class="header-right"></div>
  </div>
</template>

<script>
export default {
  name: 'Header', 
  computed:{},
  data(){
    return{
      nameValue:''
    }
  }, 
  methods:{
    searchName(){
      // console.log(this.nameValue);
      this.$emit('searchData', this.nameValue);
    }, 
  }
}
</script>
<style lang="less" scoped>
    .header{
        display: flex;
        height: .89rem; ;
        line-height: .89rem;
        background:#3c3e45;
        color: #fff;
        .header-left{
            flex: 2;
            width: .64rem;
            float: left;
            .ilume{
                text-align: center;
                font-size: .4rem;
                font-weight: bolder;
                padding-left:.2rem;
            } 
        }
        .header-input{
            flex: 4;
            height: .64rem;
            line-height: .64rem;
            margin-top: .12rem;
            margin-left: .2rem;
            padding-left: .2rem;
            background: #fff;
            border-radius: .1rem;
            color: #ccc;
            flex-direction: row;
            justify-content: flex-start;
            .search-input{
              box-sizing: border-box;
              padding: 0 .1rem;
              border-radius: .06rem;
              color: #666;
            } 
        }
         .header-right{  
              flex: 1;

         }

    } 
   
   
   

</style>