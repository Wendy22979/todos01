<template>
   <ul class="list">
        <Item 
        v-for="t in todos"  
        :key="t.id" 
        :t="t"
        :checkStatus="checkStatus"
        :todoDelete="todoDelete"
        />
        
      </ul>

    
</template>

<script>
// 引入子组件
import Item from "./Item.vue"

export default {
  name:"todoList",
  props:["todos","checkStatus","todoDelete"],
  components:{
    Item,
  }
}
</script>

<style scoped>
  /* list */
  .list {
    box-sizing: border-box;
    list-style: none;
    width: 688px;
    margin-top: 10px;
  }

  
</style>