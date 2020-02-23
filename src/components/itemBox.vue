<template>
  <a target="_blank" href="#" class="itemBox">
    <div class="itemBox__container">
      <div class="itemBox__divider itemBox__divider--top">
        <figure class="itemBox__image">
          <img :src="userImageURL" alt="default">
        </figure>
        <div class="itemBox__credits">
          Likes: {{likes}}
        </div>
      </div>
      <div class="itemBox__divider itemBox__divider--bottom" v-bind:style="{ 'background-image': 'url(' + webformatURL + ')' }">
        <div>
          <h2 class="itemBox__title">
            {{user}}
          </h2>
          <p class="itemBox__description">
            {{views}}
          </p>
        </div>
        <div class="d-flex justify-content-between">
          <div>
            <h2 class="itemBox__title itemBox__price">
              <!-- $14.15 -->
              item.objectID
            </h2>
          </div>
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
