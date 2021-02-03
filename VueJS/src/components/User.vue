<template>
    <div class="user">
        <h1>User Component</h1>
        <ul>
            <li v-for="user in users">
                {{user.name}} - {{user.username}} 
                <button v-on:click="deleteUser(user)">X</button>
            </li>
        </ul>

        <form v-on:submit.prevent="addUser"> 
            <input v-model="newUser.name" placeholder="Nombre">
            <input v-model="newUser.username" placeholder="Usuario">
            <button type="submit">
                Add
            </button>

        </form>
    </div>
</template>

<script>
export default {
    data(){
        return{
            users:[
                //USAMOS AXIOS PARA TRAER DATOS
                // {
                //     name:"Nicolás",
                //     edad:29,
                //     contacted:true
                // },
                // {
                //     name:"Fernando",
                //     edad:29,
                //     contacted:false
                // },
                // {
                //     name:"Selene",
                //     edad:26,
                //     contacted:true
                // }
            ],
            newUser:{}
        }
    },
    methods:{
        addUser(){
            this.users.push(this.newUser);
            this.newUser={};
        },
        deleteUser(user){
            this.users.splice(this.users.indexOf((user),1));
        }
    },
    created(){
        console.log("Hemos creado algo")
        //Alternativa para el VUERESOURCE usando axios
        // axios.get("https://jsonplaceholder.typicode.com/users")
        // .then(res => this.users = res.data)
        this.$http.get("https://jsonplaceholder.typicode.com/users")
        .then(res => {
            this.users=res.body;
        });
        
    }
}
</script>

<style>
    .user{
        background-color: #333;
        color: #fff;
        padding: 20px;
    }
</style>