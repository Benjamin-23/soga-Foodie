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
<div class="flexed ">
 
  <div class="flex-column">
    <div class="primary-bg container">
      <div class="flex-column">
        <label class="form-title">Enter your Email</label>
        <input type="email" v-model="formValue.email" placeholder="example@gmail.com" name="form-email" id="email_form">
      </div>

        <div class="flex-column">
          <label class="form-title">Enter your Password</label>
          <input type="password" v-model="formValue.password" placeholder="password" name="user-password" id="password_form" >
        </div>
        
        <button class="btn btn-primary" @click="checkForm" > next step</button> 
       <p>{{step}}</p>
      <div class="error error-bg" v-if="!formValidate.isRequired">All input required</div>
      </div>
  </div> 
  <div class="text-centered">
    <p>{{ msg }}</p>
    </div>
  
</div>
</template>

<style scoped>
 .btn{
   margin: 20px;
 }
 .container{ 
  width: 400px;
 
 }
label{ 
  text-align:left ;
  margin-top: 10px;
}
 .text-centered p {
  text-align: center;
  font-size: 30px;
  font-weight: 800;
}
</style>
