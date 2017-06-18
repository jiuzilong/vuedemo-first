<template>
  <div class="fl w33 p">
    <p>内容：<input class="textInputEl" v-model="content" @keyup="inputChange" /></p>
    <p>字号：<input class="textInputEl" v-model="fontSize" @keyup="inputChange"/></p>
    <p>颜色：<input class="textInputEl" v-model="color" @keyup="inputChange" /></p>
    <p><button @click="doSave">保存</button></p>
  </div>
</template>

<script>
export default {
  data () {
    return {
      content:"",
      fontSize:"",
      color:""
    }
  },
  computed:{
    jsonStr:function(){
      return {
        content:this.content,
        fontSize:/^\d+(\.\d+)?$/.test(this.fontSize)?(this.fontSize+"px"):this.fontSize,
        color:/^[0-9a-fA-F]{3,6}$/.test(this.color)?"#"+this.color:this.color
      }
    }
  },
  methods:{
    inputChange:function(ev){
      //console.log(this.content,this.fontSize,this.color);
      console.log(this.jsonStr);
      this.$dispatch("bindInputChange",this.jsonStr);
      //this.$emit("inputsChange","dssdf")
    },
    doSave:function(){
      alert(JSON.stringify(this.jsonStr));
    }
  }
}
</script>
