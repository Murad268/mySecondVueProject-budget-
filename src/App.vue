<template>
  <div>
    <FormAdd :onSubmit="onSubmit"/>
    <TotalAll :totalBalance="totalBalance"/>
    <BudgetListVue :delteItem="delteItem" :list="sort(filter, list)" :setFilter="setFilter"/>
  </div>
</template>

<script>
import BudgetListVue from './components/BudgetList.vue';
import TotalAll from './components/TotalAll.vue'
import FormAdd from './components/FormAdd.vue'
  export default {
    components: {
      BudgetListVue,
      TotalAll,
      FormAdd
    },
    data: () => ({
     list: {
      1: {
        type: "INCOME",
        value: 100,
        comment: "some comment",
        id: 1
      },
      2: {
        type: "OUTCOME",
        value: -50,
        comment: "some outcome comment",
        id: 2
      }
     },
     count: 3,
     filter: "all"
    }),
    methods: {
      delteItem(id) {
        const question = confirm("Eminsiz?")
        if(question) {
          return this.list = Object.values(this.list).filter(item => {
            return item.id != id
          })
        } else {
          return this.list
        }
      
      },
      onSubmit(value, comment, type) {
        this.count += 1
        const newObj = {
          id: new Date(),
          value: value,
          comment: comment,
          type: type
        }
        this.list[this.count] = newObj
      },
      sort(filter, items) {
        switch(filter) {
          case "all":
            return items
          case "outcome":
            return Object.values(items).filter(item => item.type == "OUTCOME")
          case "income":
             return Object.values(items).filter(item => item.type == "INCOME")
        }
      },
      setFilter(filter) {
        return this.filter = filter
      }
    },
    computed: {
      totalBalance() {
        return Object.values(this.list).reduce((a, b) => isNaN(b.value)?"duzgün pul daxil edin": (a + +b.value, 0) + "$") 
      }
    }
  }
</script>

<style lang="scss" scoped>

</style>