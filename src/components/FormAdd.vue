<template>
   <div class="addForm">
      <form @submit.prevent="submit" action="">
        <div class="goroup">
         <label for="select">Type</label>
         <select @change="value" v-model="formData.type" id="select">
            <option value="INCOME">INCOME</option>
            <option value="OUTCOME">OUTCOME</option>
         </select>
        </div>
        <div class="group">
          <label for="comment">comments</label>
          <input  v-model="formData.comment" type="text" id="comment">
        </div>
        <div class="group">
         <label for="value">value</label>
         <input required v-model="formData.value" id="value" type="text">
       </div>
         <button class="btn btn-primary">Submit</button>
      </form>
   </div>
</template>

<script>
   export default {
      props: ["onSubmit"],
      data() {
        return {
           formData: {
             type: 'INCOME',
             comment: "",
             value: ""
           }
        }
      },
      methods: {
         submit() {
            this.onSubmit(this.formData.value, this.formData.comment, this.formData.type)
         },
         value() {
            if(this.formData.type == "OUTCOME") {
              return this.formData.value = "-" + this.formData.value
            } else {
              return this.formData.value = ""
            }
         }
      }
   }
</script>

<style  scoped>
   .addForm {
      padding: 20px;
      border: 1px solid rgba(0, 0, 0, 0.3);
      width: 50%;
      margin: 30px auto 30px auto;
   }
   label {
      display: block;
      margin: 20px 0 5px 0;
   }
   input, select {
      width: 100%;
   }
   button {
      display: block;
      margin: 20px auto 0 auto;
   }
</style>