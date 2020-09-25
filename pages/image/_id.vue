<template>
  <v-card class="mx-auto image-card" max-width="500">
    <div v-for="item in hit" :key="item.id">
      <div>
        <v-img class :height="'500px'" :width="'500px'" :src="item.largeImageURL"></v-img>
        <v-card-title class="user-detail-heading">{{ item.type }}</v-card-title>
      </div>
      <div>
        <v-card-subtitle>
          <ul class="detail-list-tags">
            <li
              class="image-tags"
              v-for="(tag, index) in item.tags.split(',')"
              :key="index"
            >{{ `#${tag}` }}</li>
          </ul>
        </v-card-subtitle>
      </div>
      <div class="user-detail-card">
        <v-img :height="'50px'" :width="'50px'" :src="item.userImageURL"></v-img>
        <v-card-subtitle style="background: #31414e; color: white" class="pb-0">{{ item.user }}</v-card-subtitle>
      </div>
      <div class="image-footer-container">
        <v-card-subtitle class="pb-0 image-footer">
          {{
          `downloads: ${item.downloads}`
          }}
        </v-card-subtitle>
        <v-card-subtitle class="pb-0 image-footer">
          {{
          `Favourites: ${item.favorites}`
          }}
        </v-card-subtitle>
        <v-card-subtitle class="pb-0 image-footer">
          {{
          `Likes: ${item.likes}`
          }}
        </v-card-subtitle>
        <v-card-subtitle class="pb-0 image-footer">
          {{
          `Views: ${item.views}`
          }}
        </v-card-subtitle>
      </div>
      <v-card-actions>
        <v-btn color="primary" @click="$router.push({ path: '/' })">Back</v-btn>
      </v-card-actions>
    </div>
  </v-card>
</template>

<script>
import axios from 'axios'
import Constant from '~/constant/constant'

export default {
  data() {
    return { hit: {} }
  },
  async created() {
    const { data } = await axios.get(
      `${Constant.api}?key=${Constant.secretKey}&id=${this.$route.params.id}`
    )
    this.hit = data.hits
  },
  head() {
    return {
      title: 'image-page',
    }
  },
}
</script>

<style scoped>
.user-detail-heading {
  display: flex;
  justify-content: center;
  text-transform: capitalize;
  background: #31414e;
}

.user-detail-card {
  display: flex;
  margin: 15px;
  justify-content: center;
}

.detail-list-tags {
  list-style-type: none;
  display: flex;
  justify-content: center;
  font-size: 1rem;
}

.image-tags {
  margin: 0 2px;
  background: #31414e;
  padding: 3px;
  border-radius: 12px;
  color: white;
}

.image-footer-container {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 12px;
}

.image-footer-container .image-footer {
  background: #31414e;
  text-transform: capitalize;
  padding: 5px;
  color: white;
  margin: 12px;
}
</style>
