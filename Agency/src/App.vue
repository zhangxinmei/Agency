<template>
  <div id="app">
    <div class="agency">
      <div class="agency-hd">
        <h1 class="hd-title">标题</h1>
        <retrieval @alertTip="showAlert"></retrieval>
      </div>
      <div class="list">
        <ul>
          <li v-for="(item,index) in listOption2" :key="index" :id="item.id">
            <span>{{item.id}}</span>
            <span @click="selectItem(item)">{{item.text}}</span>
          </li>
        </ul>
      </div>
      <el-button type="primary" @click="btnClick">主要按钮</el-button>
      <el-button type="primary" @click="validClick" :disabled="disabledValid">{{validText}}</el-button>
      <el-dialog title="详情" :visible.sync="dialogFormVisible">
        <el-tabs v-model="activeName" @tab-click="handleClick">
          <el-tab-pane label="用户管理" name="first">
            <div class="detail-form">
              <el-form ref="form" :model="form" label-width="80px">
                <el-form-item label="id">
                  <el-input v-model="form.name" :disabled="isDisabled"></el-input>
                </el-form-item>
                <el-form-item label="名称">
                  <el-input v-model="form.name2" :value="itemOptions.text" :disabled="isDisabled"></el-input>
                </el-form-item>
                <p v-show="showMD">有效名单</p>
                <!-- <el-form-item>
                  <el-button type="primary" @click="edit">编辑</el-button>
                  <el-button @click="cancel">取消</el-button>
                </el-form-item> -->
              </el-form>
            </div>
          </el-tab-pane>
          <el-tab-pane label="配置管理" name="second">配置管理</el-tab-pane>
          <el-tab-pane label="角色管理" name="third">角色管理</el-tab-pane>
          <el-tab-pane label="定时任务补偿" name="fourth">定时任务补偿</el-tab-pane>
        </el-tabs>
        <div slot="footer" class="dialog-footer">
          <el-button type="primary" @click="edit">编辑</el-button>
          <el-button type="primary">确 定</el-button>
        </div>
      </el-dialog>
  
  
  
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
        activeName: 'first',
        disabledValid:false,
        validText:"无效",
        isDisabled: true,
        showDetailForm: false,
        showMD: true,
        dialogFormVisible: false,
        listOption1: [{
          id: 1,
          text: '苹果'
        }, {
          id: 2,
          text: '香蕉'
        },{
          id: 4,
          text: '芒果'
        },{
          id: 5,
          text: '香梨'
        },{
          id: 6,
          text: '猕猴桃'
        }, ],
        listOption2: [],
        itemOptions: {},
        form: {
          name: '',
          name2: ''
        }
      }
    },
    watch: {
  
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
        this.listOption2 = this.listOption1
  
      },
      btnClick() {
        this.listOption1.push({
          id: 3,
          text: '橘子'
        })
        console.log('listOption1', this.listOption1)
        console.log('listOption2', this.listOption2)
      },
      selectItem(item) {
        this.itemOptions = item;
        this.form.name = item.id;
        this.form.name2 = item.text;
        this.dialogFormVisible = true;
        this.isDisabled = true;
        this.showMD = true;
        // this.showDetailForm = true;
        console.log(555, this.itemOptions)
      },
      edit() {
        this.isDisabled = false;
        this.showMD = false;
      },
      cancel() {
        this.form.name = this.itemOptions.id;
        this.form.name2 = this.itemOptions.text;
      },
      handleClick(tab, event) {
        console.log(tab, event);
      },
      validClick() {
        this.validText="有效";
        this.disabledValid=true;
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

