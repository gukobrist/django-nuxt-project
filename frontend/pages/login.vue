<template>
  <section class="login">
    <h1 class="title">Вход</h1>
    <div class="auth-form">
      <b-field label="Username">
        <b-input v-model="user.username" type="text " />
      </b-field>
      <b-field label="Password">
        <b-input v-model="user.password" type="password" />
      </b-field>
      <b-button class="is-primary" @click="login">Login</b-button>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      user: {},
    }
  },
  methods: {
    async login() {
      try {
        await this.$auth.loginWith('local', {
          data: this.user,
        })
        this.$toasted.global.defaultSuccess({
          msg: 'Авторизация прошла успешно',
        })
      } catch (err) {
        this.$toasted.global.defaultError({
          msg: 'Логин или пароль неверные',
        })
      }
    },
  },
}
</script>
