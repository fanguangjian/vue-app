<!--
 * @Author       : G.F
 * @Date         : 2021-07-07 21:56:36
 * @LastEditTime : 2021-07-08 02:42:29
 * @LastEditors  : G.F
 * @FilePath     : /vue-app-ilume/src/components/pages/Header.vue
 * @Description  : 
-->
<template>
  <div class="header">  
    <div class="header-left">
      <!-- <div class="iconfont back-icon">&#xe624;</div> -->
       <span class="iconfont icon-Homehomepagemenu"></span>
    </div>
    <div class="header-input">
      <span class="iconfont icon-search"></span>
      <input v-model="keyword" class="search-input" type="text" placeholder="Please enter name" />    
    </div>
  </div>
</template>

<script>
export default {
  name: 'Header', 
}
</script>
<style lang="less" scoped>
 .header{
        display: flex;
        height: .89rem; ;
        line-height: .89rem;
        background: cyan;
        color: #fff;
        .header-left{
            width: .64rem;
            float: left;
            .back-icon{
                text-align: center;
                font-size: .4rem;
            } 
        }
        .header-input{
            flex: 1;
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
              // width: 100%;
              // height: .62rem;
              padding: 0 .1rem;
              // line-height: .62rem;
              text-align: center;
              border-radius: .06rem;
              color: #666;
            }
     
             

        }   

    } 
   
   
   

</style>