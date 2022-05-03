<template>
  <li class="item">
    <input type="checkbox" v-model="todo"/>{{t.title}}
    <button @click="itemDelete(t.id)">删除</button>
  </li>
</template>

<script scoped>
  export default {
    name: "todoItem",
    // 声明接收
    props:['t',"checkStatus","todoDelete"],
    computed:{
      todo:{
        get(){
          return this.t.done
        },
        set(){
          let id = this.t.id
          this.checkStatus(id);
        }
      }
    },
    methods: {
      itemDelete(x){
        this.todoDelete(x);
      }
    },
  };
</script>



<style scoped>
   .item {
    position: relative;
    border: 1px solid #ccc;
    border-bottom: none;
    padding: 5px;
  }
   .item:last-child {
    border-bottom: 1px solid #ccc;
  }
   .item:hover {
    background-color: rgb(205, 203, 203);
  }

  .item input {
    vertical-align: middle;
  }

  .item button {
    display: none;
    position: absolute;
    right: 5px;
    top: 5px;
    background-color: rgb(176, 53, 53);
    color: #fff;
    padding: 0 5px;
    border: none;
    outline: none;
    cursor: pointer;
  }
  .item:hover button {
    display: block;
  }

</style>