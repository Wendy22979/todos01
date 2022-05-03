<template>
  <div id="app">
    <div class="container">
      <Add :gain="gain"/>
      <List 
      :todos="todos" 
      :checkStatus="checkStatus"
      :todoDelete="todoDelete"
      />
      <Bottom 
       :todos="todos" 
       :checkAll="checkAll"
       :todoClear="todoClear"
      />
    </div>
  </div>
</template>

<script>
// 引入添加组件
import Add from "./components//Add.vue";
// 引入底部组件
import Bottom from "./components/Bottom.vue";
// 引入列表组件
import List from "./components/List/List.vue";

export default {
  name: "App",
   data(){
    return {
      todos:[
        {id:"001",title:"吃饭",done:false},
        {id:"002",title:"睡觉",done:true},
        {id:"003",title:"打代码",done:false},
      ]
    }
  },
  methods:{
    // 添加数据
    gain(x){
     this.todos.unshift(x);
    },
     // 同步item状态为false/true，双向绑定
    checkStatus(x){
      this.todos.forEach((val) => {
        if(val.id === x) val.done = !val.done;
      });
    },
    // 删除数据
    todoDelete(x){
      if(confirm("你确定删除吗？")){
          this.todos = this.todos.filter((val)=>{
          return val.id != x
        })
      }
     },
    //  全选反选
    checkAll(x){
       this.todos.forEach((val) => {
        val.done = x
      });
    },

    // 清除已完成的任务
    todoClear(){
       if(confirm("你确定删除吗？")){
          this.todos = this.todos.filter((val)=>{
          return val.done == false
        })
      }
    }
    
  },
  components: {
    Add,
    Bottom,
    List,
  },
};
</script>

<style>
  /* base区域 */
  * {
    margin: 0;
    padding: 0;
  }
  #app {
    width: 700px;
    padding: 8px 15px 30px;
    margin: 20px auto;
    border: 1px solid #ccc;
    font-size: 14px;
  }
  .container {
    border: 1px solid #ccc;
    padding: 5px;
  }

  
</style>
