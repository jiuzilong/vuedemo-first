<template>
  <div>
    <div id="app-wrapper">
   <div class="fl w33 b p" :style="cssStr"><p>{{text}}</p></div>
  </div>
    <Changer></Changer>
    <Changer></Changer>
  </div>
</template>

<script>
import Changer from './components/Changer.vue'
export default {
  data () {
    return {
      text: "",
      cssStr:""
    }
  },
  events:{
    bindInputChange:function(jsonStr){
      this.text = jsonStr.content;
      this.cssStr = jsonStr;
    }
  },
  components: {
    Changer
  }
}
</script>

<style>
  body{background-color: #eee}
  *{box-sizing: border-box;}
  .b{border: 2px solid #ccc; background-color: #fff;}
  .p{padding: 1em;}
  .fl{float: left;}
  .w50{width: 50%;}
  .w33{width: 33%;}
</style>
