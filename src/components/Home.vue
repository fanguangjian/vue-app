<template> 
  <Header></Header>
  <Content :pageData="pageList" v-if="pageList.length"></Content>
  <Footer></Footer>
</template>

<script>
import Header from './pages/Header.vue'
import Content from './pages/Content.vue'
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
    Footer
  },   
  data(){
    return {
        pageList: [],
    }
  },
  methods:{
    getHomeinfo(){
      axios.get('https://rickandmortyapi.com/api/character/').then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc(res){
      console.log(res);
      if(res.data){
         this.pageList = res.data.results;
      }
    }
      
  },
  mounted(){
    this.getHomeinfo()
  }
    
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
