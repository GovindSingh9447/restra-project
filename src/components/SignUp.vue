<template>
<img class="logo" src="../assets/logo.svg"/>
    <h1>Sign Up</h1>

    <div class="register">
        <input type="text" v-model="name" placeholder="Enter Name"/>
         <input type="text" v-model="email" placeholder="Enter Email"/>
          <input type="password" v-model="password" placeholder="Enter Password"/>
          <button v-on:click="signUp">Sign Up</button>
    </div>


//Hey this is comment.


</template>


<script>
import axios from 'axios'
export default{
    name:'SignUp',
    data()
    { 
        return{
            name:'',
            email:'',
            password:''
        }
    },
    methods:{
        async signUp(){
            
            let result = await axios.post("http://localhost:3000/users",{
                name:this.name,
                email:this.email,
                passwod:this.password
            });
             //console.warn("signup", this.name,this.email,this.password)
             console.warn(result);
             if(result.status==201)
             {
                 alert("signUp Done!!")
             }

        }
    }
}
</script>

<style>
.logo{
    width:100px
}
.register input{
    width: 300px;
    height: 40px;
    padding-left: 20px;
    display: block;
    margin-bottom: 30px;
    margin-right: auto;
    border: 1px solid rgb(135, 235, 168);
    margin-left: auto;

}

.register button{
    width: 320px;
    height: 40px;
    border: 11px solid #033b1b;
    background: #033b1b;
    color: rgb(255, 255, 255);
    cursor: pointer;
}
</style>