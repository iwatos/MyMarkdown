<template>
  <div id="home">
    <p class="titleLogo">MyMarkdown</p>
    <h1>{{ msg }}</h1>
    <button @click="googleLogin">Googleアカウントでログイン</button>
    <p>ブラウザでマークダウン形式の文章が作成・保存できます。</p>
    <p>Gooleアカウントですぐにログインできます。</p>
  </div>
</template>

<script>
export default {
  name: 'home',
  data () {
    return {
      msg: "Welcome to MyMarkdown"
    }
  },
  methods: {
    googleLogin: function() {
      firebase.auth().signInWithRedirect(new firebase.auth.GoogleAuthProvider())
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
