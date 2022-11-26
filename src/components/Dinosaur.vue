<script>
import { store } from '../store.js';

export default {
  data() {
    return {
      store,
      loading: false
    }
  },

  async mounted() {
    const dinoName = this.$router.currentRoute._value.params.dinosaur
    if (!store?.dinosaur?.name) {
      this.loading = true
      const res = await fetch(`http://localhost:8000/api/${dinoName}`)
      const dinosaur = await res.json();
      this.store.dinosaur = dinosaur
      this.loading = false
    }
  }
}
</script>


<template>
  <div v-if="store.dinosaur.name">
    Name: {{ store.dinosaur.name }}
    <br />
    Description: {{ store.dinosaur.description }}
  </div>
  <div v-else-if="loading">
    Loading...
  </div>
</template>