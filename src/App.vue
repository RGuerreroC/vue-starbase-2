<template>
  <div id="app">
    <h3>{{title}}</h3>
    <div class="col-md-12">
      <div class="card-columns">
        <Character v-for="id in initial_ids" :id="id"/>
      </div>
    </div>
  </div>
</template>

<script>
import Character from "./components/Character.vue";

export default {
  name: "app",
  data() {
    return {
      title: "Genera tu equipo",
      initial_ids: [1, 13, 14]
    };
  },
  components: {
    Character
  }
};
</script>
<style src='./assets/css/index.css'></style>