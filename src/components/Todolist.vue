<template>
  <div class="Todolist">
    <h1>Todolist</h1>
    <el-row>
      <el-col :span="12" :offset="6">
        <el-input v-model="item" placeholder="按回车即可添加!" @keyup.13.native='addItem'>
          <template slot="append">
            <el-button @click.native="addItem">添加</el-button>
          </template>
        </el-input>
      </el-col>
    </el-row>
    <el-row>
      <el-col :span="12" :offset="6">
        <el-tabs v-model="activeTab" :stretch="true">
          <el-tab-pane label="全部" name="all" class="text-left">
            <p v-for="(v,k) in items" :key="k">
              <el-checkbox v-model="boxs" :label="v.name">
                <span :class="{finsh: true}">{{k+1}}.{{v.name}}</span>
              </el-checkbox>
            </p>
          </el-tab-pane>
          <el-tab-pane label="已完成" name="done" class="text-left">
            <p v-for="(v,k) in doneList" :key="k">
              <el-checkbox :label="v.name">
                <span :class="{finsh: true}">{{k+1}}.{{v.name}}</span>
              </el-checkbox>
            </p>
          </el-tab-pane>
          <el-tab-pane label="未完成" name="todo" class="text-left">
            <p v-for="(v,k) in todoList" :key="k">
              <el-checkbox :label="v.name">
                <span :class="{finsh: true}">{{k+1}}.{{v.name}}</span>
              </el-checkbox>
            </p>
          </el-tab-pane>
        </el-tabs>
      </el-col>
    </el-row>

  </div>
</template>

<script type="text/ecmascript-6">
export default {
  name: 'Todolist',
  data() {
    return {
      item: '',
      items: [],
      boxs: [],
      doneList: [],
      todoList: [],
      activeTab: 'all'
    };
  },
  methods: {
    addItem() {
      if (this.item) {
        this.items.push({ done: false, name: this.item });
        this.item = '';
      } else {
        this.$message({
          message: '请先输入添加任务内容!',
          type: 'error'
        });
      }
    }
  }
};
</script>

<style lang="stylus" scoped>
.Todolist
  .el-row
    margin-top 15px
  .text-left
    text-align left
  .finsh
    text-decoration line-through
</style>
