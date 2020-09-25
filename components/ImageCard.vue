<template>
  <v-card class="mx-auto" max-width="400">
    <v-img class="white--text align-end" :height="height" :src="src">
      <v-card-title>{{ type }}</v-card-title>
    </v-img>

    <v-card-subtitle class="pb-0">{{ tags }}</v-card-subtitle>
    <v-card-subtitle class="pb-0">{{ user }}</v-card-subtitle>
  </v-card>
</template>
<script>
export default {
  props: {
    height: {
      type: String,
      default: '100px',
    },
    type: {
      type: String,
    },
    tags: {
      type: String,
    },
    user: {
      type: String,
    },
  },
}
</script>
