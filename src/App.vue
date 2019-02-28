<template>
  <div id="app">
    <Home v-if="!isLogin"></Home>
    <Editor v-else :user="userData"></Editor>
  </div>
</template>

<script>
import Home from "./components/Home.vue"
import Editor from "./components/Editor.vue"

export default {
  name: "app",
  data () {
    return {
      isLogin: false,
      userData: null
    }
  },
  components: {
    Home: Home,
    Editor: Editor
  },
  created: function() {
    firebase.auth().onAuthStateChanged(user => {
      console.log(user)
      if(user) {
        this.isLogin = true,
        this.userData = user
      }
      else {
        this.isLogin = false,
        this.userData = null
      }
    })
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
}
#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
