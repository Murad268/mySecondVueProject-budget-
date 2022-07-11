<template>
   <div class="item">
     <div class="comment">
      {{item.comment}}
     </div>
     <div class="right">
      <div class="value">
         {{item.value}}
      </div>
      <button @click="delteItem(item.id)" class="btn btn-danger">delete</button>
     </div>
   </div>
</template>

<script>
   export default {
      props: ["item", "delteItem"]
   }
</script>

<style scoped>
   .item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-top: 10px;
   }
   .right {
      width: 30%;
      display: flex;
      justify-content: space-between;
      align-items: center;
   }
   button {

   }
</style>