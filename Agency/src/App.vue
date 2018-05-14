<template>
  <div id="app">
    <div class="agency">
      <div class="agency-hd">
        <h1 class="hd-title">供销商合同设定</h1>
        <retrieval @alertTip="showAlert"></retrieval>
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
  methods: {
    showAlert() {
      alert(32323);
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

