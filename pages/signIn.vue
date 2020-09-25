<template>
  <div>
    <v-card class="mx-auto" max-width="400">
      <v-card-title class="sign-in-title">Sign In</v-card-title>
      <v-card-actions>
        <v-text-field label="Email" v-model="email"></v-text-field>
      </v-card-actions>
      <v-card-actions>
        <v-text-field label="Password" v-model="password"></v-text-field>
      </v-card-actions>
      <v-card-actions>
        <v-btn color="primary" @click="signInHandler">Sign In</v-btn>
      </v-card-actions>
    </v-card>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
    }
  },
  methods: {
    signInHandler() {
      // console.log(this.email, this.password)
      this.$router.push('/')
    },
  },
  head() {
    return {
      title: 'Sign In',
    }
  },
}
</script>

<style scoped>
.sign-in-title {
  display: flex;
  justify-content: center;
  background: #2a4656;
  text-transform: uppercase;
}
</style>
