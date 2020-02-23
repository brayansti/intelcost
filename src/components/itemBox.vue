<template>
  <a target="_blank" href="#" class="itemBox">
    <div class="itemBox__container">
      <div class="itemBox__divider itemBox__divider--top">
        <figure class="itemBox__image">
          <img src="" alt="default">
        </figure>
        <div class="itemBox__credits">
          100 credits
        </div>
      </div>
      <div class="itemBox__divider itemBox__divider--bottom" style="background-image: url(https://mytablemesa.com/Content/uploads/684a5f05-af87-438e-b32a-82bf7e92e729.png)">
        <div>
          <h2 class="itemBox__title">
            item.author
          </h2>
          <p class="itemBox__description">
            item.title
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
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
