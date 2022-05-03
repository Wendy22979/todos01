<template>
   <!-- 添加部分 -->
      <div class="add">
        <input type="text" placeholder="请输入你的任务名称，按回车键确认" @keyup.enter="add($event)"/>
      </div>
</template>

<script>
// 引入id生成器
import  {nanoid} from "../../node_modules/nanoid/nanoid"
export default {
  name: "todoAdd",
  props:["gain"],
  methods:{
    add(e){
      // 获取添加内容，然后生成数据
      let obj = {id:nanoid(),title:e.target.value,done:false}
      // 调用父组件的函数，向父组件传值
      this.gain(obj);
      // 清空input框
      e.target.value = ""
    },
  },
};
</script>
    
<style scoped>
  /* add */
  .add input {
    box-sizing: border-box;
    border: 1px solid #ccc;
    outline-color: rgba(16, 237, 249, 0.5);
    width: 688px;
    padding: 5px;
  }
</style>