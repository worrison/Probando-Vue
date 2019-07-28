<template>
  <div>
    <div class="column">
      <div class="box">
        <!-- <div class="card-image">
          <figure class="image is-4by3">
            <img src="" alt="Placeholder image" />
          </figure>
        </div> -->
        <h1>{{album.title}}</h1>
        <nuxt-link :to="`albums/${album.id}`" class="button is-primary">Link</nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AlbumCard.vue",
  props: {
    album: {},
  }
};
</script>
<style lang="css">
  .box
  {
    padding:1em;
  }
</style>
