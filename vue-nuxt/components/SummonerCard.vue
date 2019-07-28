<template>
  <div>
    <div class="column">
      <div class="card">
        <div class="card-image">
          <figure class="image is-4by3">
            <img src="" alt="Placeholder image" />
          </figure>
        </div>
        <h1>{{summoner.name}}</h1>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SummonerCard.vue",
  props: {
    //    summoner:Object
    summoner: Object,
  }
};
</script>

