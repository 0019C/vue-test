<template>
  <div id="app">
    <el-container style="margin: 0">
      <el-aside></el-aside>

      <el-container>
        <el-header>h</el-header>
        <el-main>
          <input-button plh_msg="请输入..." bt_text="提交" :value.sync="input" @showDialog="showDialog"></input-button>
          <el-dialog :title="input" v-show="dialogVisible" style="height: 200px" @close="showDialog">
            <input-button bt_text="67"></input-button>
          </el-dialog>
        </el-main>
        <el-footer>f</el-footer>
      </el-container>


    </el-container>

  </div>
</template>

<script>
import InputButton from "@/components/InputButton.vue";

export default {
  name: 'App',
  components: {
    InputButton
  },
  data: function () {
    return {
      input: "45",
      dialogVisible: false
    }
  },
  methods: {
    showDialog: function () {
      this.dialogVisible = this.dialogVisible !== true
    }
  }
}
</script>

<style>

</style>
