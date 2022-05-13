<script setup lang="ts">
import { reactive, ref } from 'vue'

defineProps<{ msg: string }>()
const formValue = reactive({
  email:"",
  password:null
})
const formValidate = reactive({
  isRequired:true
})
const step = ref(0)

const checkForm = () =>{
  formValidate.isRequired = !formValidate.isRequired
  const isValidForm = formValue.email && formValue.password
  if(isValidForm){
    formValidate
    step.value++
  }
  else{
    console.log("this form has error");
    
  }
}

</script> 

<template>
  <h1>{{ msg }}</h1>
  <div class="row ">
      <div class="col">
        <label class="form-title">Enter your Email</label>
        <input type="email" v-model="formValue.email" placeholder="example@gmail.com" name="form-email" id="email_form">
      </div> 

        <div class="col">
          <label class="form-title">Enter your Password</label>
          <input type="password" v-model="formValue.password" placeholder="password" name="user-password" id="password_form" >
        </div>
        <button class="btn btn-primary" @click="checkForm" > next step</button> 
       <p>{{step}}</p>
      <div class="error bg-danger" v-if="!formValidate.isRequired">All input required</div>
  </div>

</template>

<style scoped>
 .btn{
   margin: 20px;
 }

</style>
