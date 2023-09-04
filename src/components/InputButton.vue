<template>
  <div>
    <el-row type="flex" justify="center">
      <el-col :span="8">
        <el-input :placeholder="plh_msg" :value="value" @input="$emit('update:value',$event)"></el-input>
      </el-col>
      <el-col :span="3">
        <el-button @click="$emit('showDialog')">{{ bt_text }}</el-button>
      </el-col>
    </el-row>
  </div>


</template>

<script>
export default {
  name: "input-button",
  data:function (){
    return {
      input:""
    }
  },
  methods: {
    alertWarn:function (){
      alert(this.input)
    }
  },
  props: {
    value:String,
    plh_msg: String,
    bt_text: String
  }
}
</script>

<style scoped>

</style>