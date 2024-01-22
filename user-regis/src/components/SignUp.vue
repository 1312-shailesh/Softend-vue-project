<template>
    <img class='logo' src="../assets/logo.png" />
    <h1>Sign Up</h1>
    <div class='register'>
        <input type="text" v-model ="name" placeholder="Enter Name.." />
        <input type="text" v-model="email" placeholder="Enter Email.." />
        <input type="password" v-model="password" placeholder="Enter Password.." />
        <button v-on:click="signup">Sign Up</button>
        <p>
            <router-link to="/login">Login</router-link>
        </p>
    </div>
</template>

  
<script>
import axios from 'axios'
export default {
    name: 'SignUp',
    data()
    {
        return {
            name:'',
            email:'',
            password:''
        }
    },
    methods:{
     async   signup(){
            console.warn("signup",this.name,this.email,this.password)
            let result=await axios.post("http://localhost:3000/users",{
                email:this.email,
                name:this.name,
                password:this.password
            });
            console.warn(result);
            if(result.status==201)
            {
                alert("Sign Up Succeessful")
                this.$router.push({name:'Login'})
            
            localStorage.setItem("UserInfo",JSON.stringify(result.data))
        
            }
        }
    },
    mounted()
    {
        let user = localStorage.getItem('UserInfo');
        if(user)
        {
            this.$router.push({name:'Login'})
        };
    }
}
</script>

<style>

</style>
