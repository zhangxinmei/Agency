<template>
  <div id="app">
    <div class="agency">
      <div class="agency-hd">
        <h1 class="hd-title">标题</h1>
        <retrieval @alertTip="showAlert"></retrieval>
      </div>
      <div class="list">
        <ul>
          <li v-for="(item,index) in listOption2" :key="index" :id="item.id" @click="selectItem(item)">{{item.text}}</li>
        </ul>
      </div>
      <el-button type="primary" @click="btnClick">主要按钮</el-button>
      <div class="detail">
        <div>
          <span>{{itemOptions.id}}</span>
          <span>{{itemOptions.text}}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import retrieval from "./components/Retrieval/Retrieval";
export default {
  name: "App",
  components: {
    retrieval
  },
  data() {
    return {
      listOption1:[{
        id:1,
        text:'苹果'
      },{
        id:2,
        text:'香蕉'
      },],
      listOption2:[],
      itemOptions:{},
    }
  },
  watch:{
   
    btnwatchClick() {
      this.showList()
    }
   
  },
  created() {
    this.showList()
  },
  methods: {
    showAlert() {
      alert(32323);
    },
    showList() {
      this.listOption2=this.listOption1
     
    },
    btnClick() {
      this.listOption1.push({id:3,text:'橘子'})
      console.log('listOption1',this.listOption1)
      console.log('listOption2',this.listOption2)
    },
    selectItem(item) {
      this.itemOptions=item
      console.log(555,this.itemOptions)
    }
  }
};
</script>

<style lang="less">
@import "./style/common/reset.less";
.agency-hd {
  padding: 20px;
  .hd-title {
    font-size: 20px;
    font-weight: 400;
  }
}
</style>

