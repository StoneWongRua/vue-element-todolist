<template>
  <div class="Todolist">
    Todolist
    <el-input v-model="item" placeholder="按回车即可添加!" @keyup.13.native='addItem'></el-input>
  </div>
</template>

<script type="text/ecmascript-6">
export default {
  name: 'Todolist',
  data() {
    return {
      item
    };
  },
  methods: {
    addItem() {
      alert(1);
    }
  }
};
</script>