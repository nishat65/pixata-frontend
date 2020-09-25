<template>
  <div>
    <!-- <v-text-field label="Search Image" v-model="searchImage"></v-text-field> -->
    <div class="image-container">
      <ul style="list-style-type: none" v-for="(hit, index) in hits" :key="index">
        <li style="margin: 10px" @click="singleImageDisplay(index)">
          <div>
            <v-card class="mx-auto image-card" max-width="400">
              <v-img
                class="white--text align-end"
                :height="'250px'"
                :width="'250px'"
                :src="hit.largeImageURL"
              >
                <v-card-title>{{ hit.type }}</v-card-title>
              </v-img>

              <v-card-subtitle class="pb-0">
                <ul style="list-style-type: none; display: flex">
                  <li
                    class="image-tags"
                    v-for="(tag, index) in hit.tags.split(',')"
                    :key="index"
                  >{{ `#${tag}` }}</li>
                </ul>
              </v-card-subtitle>
              <div class="user-detail-card">
                <v-img :height="'50px'" :width="'50px'" :src="hit.userImageURL"></v-img>
                <v-card-subtitle class="pb-0">{{ hit.user }}</v-card-subtitle>
              </div>
            </v-card>
          </div>
        </li>
      </ul>
      <nuxt-child />
    </div>
  </div>
</template>

<script>
import ImageCard from '~/components/ImageCard.vue'
import axios from 'axios'
import Constant from '~/constant/constant'

export default {
  components: {
    ImageCard,
  },

  middleware() {
    console.log('running middleware!!', arguments)
  },

  data() {
    return {
      searchImage: '',
    }
  },

  async asyncData() {
    const { data } = await axios.get(
      `${Constant.api}?key=${Constant.secretKey}`
    )
    return { hits: data.hits }
  },

  methods: {
    singleImageDisplay(id) {
      const hit = this.hits.find((hit, index) => {
        if (index === id) return hit
      })
      this.$router.push({ path: `/image/${hit.id}`, params: { id: hit.id } })
    },
  },

  head() {
    return {
      title: 'HomePage',
    }
  },
}
</script>

<style scoped>
.image-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-content: center;
}

.image-card {
  max-width: 250px;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
}

.user-detail-card {
  display: flex;
  margin: 15px;
  justify-content: center;
}

.image-tags {
  margin: 0 2px;
  background: #31414e;
  padding: 3px;
  border-radius: 12px;
  color: white;
}
</style>
