<template>
   <div class="total">
      <span>Balance: </span>
      <span :class="className" class="totaling">{{totalBalance}}</span>
   </div>
</template>

<script>
   export default {
      props: {
         totalBalance: {
            type: Number,
            default: 0
         }
      },
      computed: {
         className() {
            return this.totalBalance > 0?"text-success":this.totalBalance==0?"text-dark":"text-danger"
         }
      }
   }
</script>

<style scoped>
   .total {
      width: 50%;
      margin: 0 auto;
      text-align: center;
   }
   span {
      font-size: 40px;
      font-weight: 800;
   }
  
</style>