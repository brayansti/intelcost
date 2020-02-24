<template>
  <a target="_blank" :href="pageURL" class="itemBox">
    <div class="itemBox__container">
      <div class="itemBox__divider itemBox__divider--top">
        <figure class="itemBox__image">
          <img :src="userImageURL" alt="default">
        </figure>
        <div class="itemBox__credits">
          {{user}}
        </div>
      </div>
      <div class="itemBox__divider itemBox__divider--bottom" v-bind:style="{ 'background-image': 'url(' + webformatURL + ')' }">
        <div class="d-flex justify-content-between">
          <div>
            <h2 class="itemBox__title">
              ID: {{id}}
            </h2>
          </div>
          <p>
            {{comments}}
            <font-awesome-icon icon="comment" />
          </p>
        </div>
      </div>
      <div class="itemBox__divider">
        <div class="pt10 pb10">
          <h2 class="itemBox__title">
            Likes: {{likes}}  
          </h2>
          <p class="itemBox__description">
            Vistas: {{views}}
          </p>
        </div>
      </div>
    </div>
  </a>
</template>

<script>
export default {
  name: 'item-box',
  props: {
    id: Number,
    pageURL: String,
    type: String,
    tags: String,
    previewURL: String,
    previewWidth: Number,
    previewHeight: Number,
    webformatURL: String,
    webformatWidth: Number,
    webformatHeight: Number,
    largeImageURL: String,
    imageWidth: Number,
    imageHeight: Number,
    imageSize: Number,
    views: Number,
    downloads: Number,
    favorites: Number,
    likes: Number,
    comments: Number,
    user_id: Number,
    user: String,
    userImageURL: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
