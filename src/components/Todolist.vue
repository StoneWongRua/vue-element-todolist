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
    <el-row v-for="(v,k) in items" :key="k">
      <el-col :span="12" :offset="6" class="text-left">
       <el-checkbox v-model="doneList" :label="v.name"><span  :class="{done: v.done}">{{k+1}}.{{v.name}}</span></el-checkbox>
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
      doneList: []
    };
  },
  methods: {
    addItem() {
      this.items.push({ done: false, name: this.item });
    }
  }
};
</script>

<style lang="stylus" scoped>
  .Todolist
    .text-left
      text-align left
    .done
      text-decoration line-through
</style>
