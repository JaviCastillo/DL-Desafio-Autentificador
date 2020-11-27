<template>
  <div>
    <h1 class="my-5">Login</h1>
    <form class="container text-left">
      <div class="form-group">
        <label >Correo</label>
        <input type="email" class="form-control" v-model="formLabelAlign.user">
      </div>
      <div class="form-group">
        <label>Contraseña</label>
        <input type="password" class="form-control" v-model="formLabelAlign.password">
      </div>
      <button type="submit" class="btn btn-primary" @click.prevent="login">Entrar</button>
    </form>
  </div>
</template>

<script>
import Firebase from 'firebase'

export default {
  name: 'Login',
  data() {
        return {
            formLabelAlign: {
                user: '',
                password: ''
            }
        }
    },
    methods: {
        login() {
            console.log(this.formLabelAlign.user);
            Firebase.auth()
            .signInWithEmailAndPassword(
                this.formLabelAlign.user, 
                this.formLabelAlign.password
            )
            .then(() =>{
                alert('Entraste');
                this.$router.push('home')
            },
            reject =>{
                alert(reject.message)
            })
        }
    },

}
</script>