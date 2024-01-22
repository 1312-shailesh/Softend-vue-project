<template>
    <div class="Header-Nav">
    <a href="#" >Update</a>
    <a v-on:click="logout" href="#">Log Out</a>
    </div>

    <h1>Hello {{name}} ,Welcome to Home Page</h1>
    <table border="1 px">
        <tr>
            <td>Id</td>
            <td>Name</td>
            <td>Email</td>

        </tr>
        <tr v-for="item in users" :key="item.id">
            <td>{{item.id}}</td>
            <td>{{item.name}}</td>
            <td>{{item.email}}</td>

        </tr>
    </table>
</template>

<script>
import axios from 'axios';
import Header from './Header.vue'
export default {
    name: 'Home',
    components:{
        Header
    },
    methods:{
        logout()
        {
            localStorage.clear();
            this.$router.push({name:'Login'})
        }
    },
    data(){
        return{
            name:'',
            users:[],
        }
    },
    async mounted() {
        let user = localStorage.getItem('UserInfo');
        this.name= JSON.parse(user).name
        if (!user) {
            this.$router.push({ name: 'SignUp' })
        }
        let result = await axios.get("http://localhost:3000/users");
        console.warn(result)
        this.users=result.data
    },
    
}
</script>
<style>
td{
    width: 150px;
    border-style: dotted;
    margin-left: auto;
    margin-right: auto;
    align-items: center;
}
</style>

