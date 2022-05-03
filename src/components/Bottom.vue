<template>
  <!-- bottom -->
  <footer v-show="total">
    <input type="checkbox" 
      v-model="todoAll"
    />
    <span>已完成{{BottomComplete}}/全部{{total}}</span>
    <button @click="itemClear">清除已完成任务</button>
  </footer>
</template>

<script>
export default {
  name: "todoBottom",
  props:["todos","checkAll","todoClear"],
  methods:{
    itemClear(){
      this.todoClear()
    }
  },
  computed:{
    // 总数
    total(){
      return this.todos.length
    },
    // 完成数
    BottomComplete(){
     return this.todos.reduce((count,val)=>{
        return count+(val.done?1:0)
      },0)
    },
    // 全选反选
    todoAll:{
      get(){
        return this.BottomComplete === this.total && this.total != 0
      },
      set(val){
        this.checkAll(val)
      }
    }
  }
};
</script>

<style scoped>
footer {
  position: relative;
  padding: 15px 6px 10px;
}
footer button {
  position: absolute;
  bottom: 10px;
  right: 5px;
  padding: 0 5px;
  background-color: rgb(176, 53, 53);
  color: #fff;
  border: none;
  outline: none;
  cursor: pointer;
}
</style>