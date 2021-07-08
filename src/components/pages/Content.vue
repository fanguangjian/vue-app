<!--
 * @Author       : G.F
 * @Date         : 2021-07-07 21:56:36
 * @LastEditTime : 2021-07-09 00:03:12
 * @LastEditors  : G.F
 * @FilePath     : /vue-app-ilume/src/components/pages/Content.vue
 * @Description  : 
-->
<template>
  <div class="hello">    
      <ul>
        <li 
          class="item border-bottom"
          v-for="item of pageData"
          :key="item.id"
          @click="showDetail(item.id)"
          >
           <div class="flex-container">
              <div class="flex-image">
                  <img :src="item.image" >
              </div>
              <div class="flex-text">
                  <div class="item-text">          
                    <div>
                      <span class="name">{{item.name}}</span>
                    </div>          
                    <div>
                      <span class="status">
                        <span class="status-icon">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>{{item.status}}-{{item.species}}
                      </span>
                    </div>
                  </div>
                  <div class="item-text">
                      <span class="title">Last known location:</span>    
                      <div class="title-info">{{item.location.name}}</div>
                  </div>
                  <div class="item-text">
                      <span class="title">First seen in:</span>   
                      <div class="title-info">{{item.origin.name}}</div>
                  </div>          
              </div>
            </div>
        </li>
      </ul>

     
  </div>
</template>

<script>
export default {
  name: 'Content', 
  props: {
      pageData: Array
  },
  setup(props) {
    console.log(props.pageData);  
  },
  methods:{
    showDetail(id){
       console.log('show detail');
      //  this.getDetail(id);
       this.$parent.getDetail(id);
    },
   
  
  }
}
</script>
<style lang="less" scoped>
    .flex-container {
        display: -webkit-flex;
        display: flex;
        width: 100%;
        background-color: #242830;
        padding: .2rem 2rem .4rem .4rem;
    }
    .flex-container:hover .name{
        color:#f49804;
    }

    .flex-image {
        width: 30%;
        border-top-left-radius: .12rem;
        border-bottom-left-radius: .12rem;
        overflow:hidden;
        img{
          width:100%
        }
    }
    .flex-text {
       background-color:#3c3e45;
        width: 60%;
        display: flex;
        -webkit-flex-direction: column;
        flex-direction: column;
        -webkit-justify-content: center;
        justify-content: center;
        border-top-right-radius: .12rem;
        border-bottom-right-radius: .12rem;

    }
    .item-text {
        display: flex;
        justify-content: center;
        width: 80%;
        height: 33.3%;
        -webkit-flex-direction: column;
        flex-direction: column;
        align-items: flex-start;
        margin-left:.2rem;
        .name{
           font-size:.4rem;
           font-weight:bolder;
           color:#fff;
        }
        .status{
          color:#fff;
          font-size:.2rem;
          margin-top:.2rem;
          .status-icon{                    
              height: 0.5rem;
              width: 0.5rem;
              margin-right: 0.375rem;
              background: rgb(85, 204, 68);
              border-radius: 50%;
          }
        }
        .title{
          color:#9e9e9e;
        }
        .title-info{
          color:#ebebeb;
          margin-top:.2rem;
        }
    }
</style>

