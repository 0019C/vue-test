<template>
  <div id="app">
    <el-select v-model="currentSelects" :loading="loading" loading-text="请稍等..." filterable remote
               :remote-method="(query)=>{remoteGetOptions(query)}">
      <el-option v-for="item of currentOptions" :label="item" :key="item" :value="item"></el-option>

    </el-select>  <el-cascader :props="props" :options="['234','567']"></el-cascader>
  </div>
</template>

<script>
import InputButton from "@/components/InputButton.vue";
export default {
  name: 'App',
  components: {
    // eslint-disable-next-line vue/no-unused-components
    InputButton
  },
  data: function () {
    return {
      loading: false,
      casSelect:[],
      currentOptions: [],
      currentSelects: [],
      allOptions: ["Alabama", "Alaska", "Arizona",
        "Arkansas", "California", "Colorado",
        "Connecticut", "Delaware", "Florida",
        "Georgia", "Hawaii", "Idaho", "Illinois",
        "Indiana", "Iowa", "Kansas", "Kentucky",
        "Louisiana", "Maine", "Maryland"],

      cascadeOptions:[
        {value:"book",label:"书籍",children:[{value:"1",label:"1"},{value:"2",label:"2"}]},
        {value:"game",label:"游戏",children:[{value:"3",label:"3"},{value:"4",label:"4"}]}
      ],
      dialogVisible: false,
      props: {
        id:0,
        lazy: true,
        lazyLoad (node, resolve) {
          const { level } = node;
          console.log(node,level);
          setTimeout(() => {
            const nodes = Array.from({ length: level + 1 })
                .map(() => ({
                  value: ++this.id,
                  label: `选项${this.id}`,
                  leaf: level >= 2
                }));
            // 通过调用resolve将子节点数据返回，通知组件数据加载完成
            resolve(nodes);
          }, 1000);
        }
      }
    }

  },
  methods: {
    showDialog() {
      this.dialogVisible = this.dialogVisible !== true
    },
    remoteGetOptions: function (query) {
      this.loading = true
      setTimeout(() => {
        this.currentOptions = this.allOptions.filter((option) => {
          return option.indexOf(query) > -1;
        })
        this.loading = false
      }, 1000)
    }
  },
  mounted() {
    this.currentOptions = this.allOptions
  }
}
</script>

<style>

</style>
