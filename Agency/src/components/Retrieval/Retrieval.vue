<template>
  <div class="retrieval">
    <el-row type="flex" class="row-bg" justify="space-between">
      <el-col :span="12">
        <div class="grid-content retrieval-ft">
          公司名称：<el-input v-model="cName" placeholder="请输入内容"></el-input>
        </div>
      </el-col>
      <el-col :span="12">
        <div class="grid-content retrieval-rt">
          是否拜访：<el-select v-model="visit" placeholder="All">
            <el-option
              v-for="item in visitOptions"
              :key="item.value"
              :label="item.label"
              :value="item.value">
            </el-option>
          </el-select>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      visitOptions:[{
        value:'0',
        label:'是',
      },{
        value:'1',
        label:'否',
      },{
        value:'2',
        label:'All',
      }],
      cName: "",
      visit:'',
    };
  },
  methods: {
    alertTip() {
      this.$emit("alertTip");
    }
  }
};
</script>

<style lang="less" scoped>
.retrieval {
  padding: 10px 0;
  max-width: 1000px;
  margin: 0 auto;
  background-color: #eee;
}
.el-input {
  position: relative;
  font-size: 14px;
  display: inline-block;
  width: 180px;
}
</style>
