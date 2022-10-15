<template>

  <v-container>
    <PhotoForm @addPhoto="addPhoto" />
    <!-- <div v-else>Вы не можете добавить больше фотографий</div> -->
    <v-row>
      <V_photo v-for="photo in $store.getters.getAllPhotos" :photo="photo" :key="photo.id" />
    </v-row>
    <PhotoDialog />
  </v-container>
</template>

<script>

import V_photo from "@/components/photo/V_photo.vue";
import PhotoForm from "@/components/photo/PhotoForm"
import PhotoDialog from "@/components/photo/PhotoDialog.vue";
import { mapActions } from "vuex";


export default {
  components: {
    V_photo,
    PhotoForm,
    PhotoDialog
  },
  data: () => ({
    photos: [],
    // currentPhoto: {},
    // dialogVisible: false
  }),
  mounted() {
    // this.fetchTodo()
    // this.$store.dispatch("fetchPhotos")
    this.fetchPhotos()
  },
  methods: {

    ...mapActions(['fetchPhotos']),

    // fetchTodo() {
    //   this.axios.get('https://jsonplaceholder.typicode.com/photos?_limit=10')
    //     .then(response => this.photos = response.data)
    // },
    addPhoto(photo) {
      this.photos.push(photo)
    },
    openPhoto(photo) {
      this.currentPhoto = photo
      this.dialogVisible = true
    }
  }
}

</script>

<style scoped>
</style>