<template>
    
    <div class="test">
        <div v-html="myHtml"></div>
        <div v-if="showName">
            <h1>{{title + user.firstname +user.lastname }}</h1>
        </div>
        <div v-else>
            <h1>No se puede mostrar User</h1>
        </div>
        <hr>
        <ul>
            <li v-for="team in teams" >
                <!-- Sólo a  MOODO de Ejemplo. No tiene sentido crear una lista de esta Forma -->
                {{team.name + " es del país: " + team.pais}}    
            </li>   
        </ul>
        <input type="text" v-on:keyup.enter="typingEnter">
        <button type="button"  v-on:click="saludar(user.firstname )">
            CLICK ME!
        </button>
        <div>
            {{fullname}}
        </div>
        <p>
            {{msg}}
        </p>
    </div>
</template>    
<script>
export default {
    data(){
        return {
            title: "Hola ",
            user:{
                firstname:"Nicolás ",
                lastname: "Alonso   "
            },
            myHtml: '<h3> Hola VUEJS</h3>',
            showName: true,
            teams:[
                { name:"Boca Juniors",pais:"Argentina"},
                { name:"Flamengo", pais:"Brasil"},
                { name:"Barcelona", pais:"España"},
                { name:"Juevntus", pais:"Italia"},
                { name:"Bayer Munich", pais:"Alemania"},
            ]
        }
    },
    methods:{
        saludar(name){
            alert(`${name} Usted presionó el Botón`)
        },
        typingEnter(e){
            console.log(e.target.value)

            
        }    
    },
    computed:{
            fullname(){
                return this.user.firstname + " " + this.user.lastname
            }
    },
    props:{
        msg:{
            type: String,
            default:"Este mensaje es por Defecto"
        }
    }
    
}
</script>

<style>
    .test{
        background-color: #eee;
        
    }
</style>