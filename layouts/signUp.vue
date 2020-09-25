<template>
  <v-app dark>
    <v-list>
      <ul class="nav-link">
        <li class="nav-link-list">
          <NuxtLink to="/">Home page</NuxtLink>
        </li>
        <li class="nav-link-list">
          <NuxtLink to="/signIn">Sign In</NuxtLink>
        </li>
      </ul>
    </v-list>
    <div>Sign Up</div>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<style scoped>
.nav-link {
  display: flex;
  list-style-type: none;
  margin: 12px;
  justify-content: flex-end;
  align-items: center;
}

.nav-link-list {
  padding: 12px;
  background: #2a4656;
  margin: 12px;
}

.nav-link-list a {
  text-decoration: none;
  color: white;
}
</style>
