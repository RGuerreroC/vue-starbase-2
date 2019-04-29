<template>
  <div class="card bg-dark text-light border-info text-left" @click="switchCharacter">
    <div class="card-body">
      <h4 class="card-title">{{ character.name }}</h4>
      <p class="card-text">Height: {{character.height}} cm</p>
      <p class="card-text">
        Mass: {{ character.mass }}
        <span v-if="character.mass !== 'unknown'">kg</span>
      </p>
      <p class="card-text">Hair: {{ character.hair_color }}</p>
      <p class="card-text">Eyes: {{ character.eye_color}}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["id"],
  data() {
    return {
      character: {}
    };
  },
  methods: {
    fetchCharacter(id) {
      //fetch(`http://dxcodercrew.net/rest/recipe-laravel-api/public/r/${id}`, {
      fetch(`https://swapi.co/api/people/${id}`, {
        method: "GET"
      })
        .then(response => response.json())
        .then(json => (this.character = json));
    },
    switchCharacter() {
      let random_id = Math.floor(Math.random() * 83) + 1;
      this.fetchCharacter(random_id);
    }
  },
  created() {
    this.fetchCharacter(this.id);
  }
};
</script>

