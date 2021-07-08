
<!--
 * @Author       : G.F
 * @Date         : 2021-07-07 21:56:36
 * @LastEditTime : 2021-07-09 00:33:49
 * @LastEditors  : G.F
 * @FilePath     : /vue-app-ilume/src/components/pages/Footer.vue
 * @Description  : 
-->
<template>
  <div class="footer">
  
    
     <div class="flex-container">
        <div class="flex-item">  
          <button type="button" @click="pre()">
            <span class="iconfont icon-shangyibu"></span>Previous
          </button>
        </div>
        <div class="flex-item"> 
          <button type="button"  @click="next()">
           Next  <span class="iconfont icon-next"></span>
          </button>
        </div>
      </div>
  </div>
</template>

<script>
export default {
  name: 'Footer', 
   methods:{
    pre(){
       this.$parent.showPre();
    },
    next(){     
      this.$parent.showNext();
    }  
  }
}
</script>
<style lang="less" scoped>
.footer{
  .flex-container {
    display: -webkit-flex;
    display: flex;
    -webkit-justify-content: center;
    justify-content: center;
    // width: 400px;
    // height: 250px;
      background-color: #3c3e45;
  }

  .flex-item {
      flex:1;
  }
  .flex-item:hover button {     
        color:#fff;
        background:#f49804;
  }
}

</style>


