<template>
    <v-containter>
       <v-row justify="center">
           <v-col cols="12" sm="2" md="4">
               <v-card>
                   <v-card-title class="text-h5 text-center">
                       회원가입
                   </v-card-title>
                   <v-card-text>
                       <v-form @keydown.enter="create">
                           <v-text-field
                           label="이름"
                           v-model="name"
                           prepend-icon="mdi-account"
                           required
                           />
                           <v-text-field
                           label="email"
                           v-model="email"
                           type="email"
                           prepend-icon="mdi-email"
                           required
                           />
                           <v-text-field
                           label="password"
                           v-model="password"
                           type="password"
                           prepend-icon="mdi-lock"
                           required
                           />
                           <v-row>
                               <v-col cols="12">
                                   <v-btn color="secondary" block @click="create">등록</v-btn>
                               </v-col>
                           </v-row>
                       </v-form>
                   </v-card-text>
               </v-card>
           </v-col>
   
       </v-row>
    </v-containter>
   </template>
   <script>
   import axios from 'axios';
   
       export default{
           data(){
               return{
                    name:"",
                   email:"",
                   password:"",
   
               }
           },
           methods:{
               async create(){
                  try{
                    const data = {name:this.name, email:this.email, password:this.password}
                   await axios.post(`${process.env.VUE_APP_API_BASE_URL}/member/create`, data)
                   this.$router.push("/");
                  }catch(e){
                    console.log(e);
                    alert(e.response.data)
                  }
   
               }
   
           }
       }
   </script>