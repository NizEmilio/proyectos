<template>
  <div id="app">
    <h1>Hola Mundooo!</h1>
    <nav>
        <ul>
            <li>
                <router-link to='/test'>
                  Test
                </router-link>
            </li>
            <li>
              <router-link to='/'>
                  User
                </router-link>
            </li>
        </ul>
    </nav>

    <router-view></router-view>

    <!-- <Test msg="Estoy pasando un Párrafo de un Contenedor Padre"/>
    <User/> -->
  </div>
</template>

<script>

import Test from "./components/Test";
import User from "./components/User";


export default {
  name: 'App',
  components: {
    Test,
    User,
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
