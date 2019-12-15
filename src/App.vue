<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>

    <button @click="getPic">快照</button>

    <img id="img" class="img" v-show="showPic">
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
      return html2canvas(obj).then(function(canvas){
        that.showPic = true
        console.log(canvas.toDataURL())
        img.src = canvas.toDataURL()
      })
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
.img{
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

@keyframes showImg{
  from{
    width: 120%
  }
  to{
    width: 50%
  }
}
</style>
