<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>

    <button @click="getPic">快照</button>

    <div v-show="showPic" class="imgView">
      <div class="close" @click="close">X</div>
      <img id="img" class="img">
      <div class="imgViewOPt">
        <div class="imgViewOPtItem">保存</div>
        <div class="imgViewOPtItem">分享</div>
      </div>
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import html2canvas from 'html2canvas'


export default {
  name: 'app',
  data() {
    return {
      showPic: false
    }
  },
  mounted() {
    console.log(document.body.clientHeight)
  },
  methods: {
    getPic(){
      let that = this
      let obj = document.querySelector("#app")
      let img = document.querySelector('#img')
    
      return html2canvas(obj,{backgroundColor:'#ffffff'}).then(function(canvas){
        that.showPic = true
        img.src = canvas.toDataURL()
      })  
    },
    close(){
      let img = document.querySelector('#img')
      img.src = ''
      this.showPic = false
    }
  },
  components: {
    HelloWorld
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  position: relative;
}
.close{
  width: 25px;
  height: 25px;
  line-height: 25px;
  text-align: center;
  border: 1px solid #DCDFE6;
  position: absolute;
  top: -10px;
  right: -10px;
  border-radius: 50%;
  background: #F56C6C;
  color: white
}
.imgView{
  width: 50%;
  position: absolute;
  top: 0;
  z-index: 99;
  left: 50%;
  top: 50%;
  transform: translate(-50%,-50%);
  border: 1px solid #DCDFE6;
  animation: showImg 2s
}
.img{
  width: 100%
}
.imgViewOPt{
  display: flex;
  flex-direction: row;
  background: white;
  padding: 10px;
  border-top: 1px solid #DCDFE6
}
.imgViewOPtItem{
  width: 50%
}

@keyframes showImg{
  0%{
    width: 150%
  }
  50%{
    width: 40%
  }
  100%{
    width: 50%
  }
}
</style>
