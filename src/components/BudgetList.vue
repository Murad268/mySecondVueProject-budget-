<template>
   <div class="list">
      <div class="btns">
         <button @click="setFilter('all')" class="btn btn-warning">ALL</button>
         <button @click="setFilter('income')" class="btn btn-warning">INCOME</button>
         <button @click="setFilter('outcome')" class="btn btn-warning">OUTCOME</button>
      </div>
      <div class="list__tittle">{{header}}</div>
      <template v-if="isEmpty">
         <div class="lists">
            <ListItem :delteItem="delteItem" v-for="(item, prop) in list" :key ="prop" :item = "item" />
         </div>
      </template>
      <template v-else>
         {{emptyTitle}}
      </template>
   </div>
</template>

<script>
import ListItem from './ListItem.vue'
   export default {
      components: {
         ListItem
      },
      data: () => ({
         header: "Budget list",
         emptyTitle: "Empty Title"
      }),
      props: {
         list: {
            type: Object,
            default: () => ({})
         },
         delteItem: {
            type: Function,
            default: () => ({})
         },
         setFilter: {
            type: Function,
            default: () => ({})
         }
      },
      computed: {
         isEmpty() {
            return Object.keys(this.list).length
         }
      }
   }
</script>

<style  scoped>
   .list {
      width: 50%;
      margin: 40px auto;
      border: 1px solid rgba(0, 0, 0, 0.3);
      padding: 20px;
   }
   .list__tittle {
      text-align: center;
       border-bottom: 1px solid rgba(0, 0, 0, 0.3);
       padding-bottom: 5px;
   }
   button {
      display: block;
      font-weight: 800;

   }
   .btns {
      display: flex;
      width: 60%;
      justify-content: space-between;
      margin: 0 auto 20px auto;
   }
</style>