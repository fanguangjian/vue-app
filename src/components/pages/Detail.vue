<template>
  <div id="detail" style="width:80vw">  
          <div class="flex-container"> 
            <div class="close-x" @click="close()">Close X</div>         
            <div class="flex-text">
                <div class="item-text">
                    <span class="name">{{detailData.name}}</span>                    
                    <span class="status">
                      <span class="status-icon">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>{{detailData.status}}-{{detailData.species}}
                    </span>
                </div>
                <div class="item-text">
                    <span class="title">Gender:</span>    
                    <div class="title-info">{{detailData.gender}}</div>
                </div>
                <div class="item-text">
                    <span class="title">Last known location:</span>    
                    <div class="title-info">{{detailData.location.name}}</div>
                </div>
                <div class="item-text">
                    <span class="title">First seen in:</span>   
                    <div class="title-info">{{detailData.origin.name}}</div>
                </div>  
                <div>
                  <hr>
                  <div style="color:cyan" @click="showEpisode()" v-show="!isShowEpisode"><span class="iconfont icon-icon-test1" ></span> Show More</div>
                  <div style="color:red" @click="showEpisode()" v-show="isShowEpisode"><span class="iconfont icon-icon-test" ></span> Show Less</div>
                </div>
                <div class="item-text show-episode" v-show="isShowEpisode">
                    <span class="title">Episode:</span>   
                    <div class="title-info">
                      <ul>
                          <li 
                            class="item border-bottom"
                            v-for="item of detailData.episode"
                            :key="item"                        
                            >{{item}}</li>
                      </ul>

                    </div>
                </div>          
            </div>
        </div>
  </div>
</template>

<script>
export default {
  name: 'Detail', 
  props: {
      detailData:{}
  },
  setup(props) {
    console.log(props.detailData);  
  },
  data(){
    return{
      isShowEpisode:false
    }
  },
 
  methods:{
    close(){
       this.$parent.closeDetail();
    },
    showEpisode(){
      this.isShowEpisode = !this.isShowEpisode;
    }  
  }
}
</script>
<style lang="less" scoped>

@keyframes ani
{
	from {width:0px;}
	to {}
}
@keyframes ani-border
{
	from {background:#fff;;}
	to {background:#9e9e9e;}
}
@keyframes ani-epi
{
	from {height:0px;}
	to {}
}
#detail{
   position: fixed;
   top:3rem;
   margin-left: 10vw;
   animation:ani 1s;
   .flex-container {
        display: -webkit-flex;
        display: flex;
        background-color:  #9e9e9e;
        border-radius: .2rem;
        padding: .1rem;
        animation:ani-border 1s;

        .close-x{
          color:#fff;
          font-size:.4rem;
          font-weight:bolder;
          position:absolute;
          top:.2rem;
          right: .2rem;
        }
      
        .flex-text {
          background-color:#3c3e45;
            width: 100vw;
            display: flex;
            -webkit-flex-direction: column;
            flex-direction: column;
            -webkit-justify-content: center;
            justify-content: center;
            border-top-right-radius: .12rem;
            border-bottom-right-radius: .12rem;
             .show-episode{
                 animation:ani-epi 1s;
             }
            .item-text {
              display: flex;
              justify-content: center;
              height: 8vh;
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
        }

   

    }
  


}
   
</style>

