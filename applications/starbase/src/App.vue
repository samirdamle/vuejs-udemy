<template>
  <div id="app">
    <h3>{{title}}</h3>
    <div class="row">
      <div class="col-sm-12">  
        <Character v-for="(id, index) in initialIds" :key="index" :id="id"></Character>
      </div>
    </div>
    <button class=".btn .btn-primary" @click="fetchCharacters">Test Fetch Character</button>
  </div>
</template>
<script>
import Character from './components/Character.vue'
export default {
  name: 'app',
  data() {
    return {
      title: 'Generate Your Teams',
      initialIds: [1, 13, 14]
    }
  },
  methods: {
    fetchCharacters() {
      fetch('http://swapi.co/api/people', {
        method: 'GET'
      })
        .then(res => res.json())
        .then(data => {
          console.log(data);
        });
    }
  },
  components: {
    Character
  }
}
</script>
<style lang="scss">
.yellow {
  color: yellow;
}
</style>

