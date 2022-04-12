<template>
  <div id="app">
    <div class="d-flex">
      <!-- section -->
      <task-section :newId="newId"></task-section>
      <!-- add section button -->
      <div>
        <button @click="createSection()" type="button" class="btn btn-light shadow">ADD SECTION</button>
      </div>
    </div>
    
  </div>
</template>

<script>
import TaskSection from './components/TaskSection.vue'
// import TaskSection from './components/TaskSection.vue'

export default {
  name: 'App',
  components: {
    TaskSection,
  },
  data() {
    return {
      newId: 0,
    }
  },
  methods: {
    createSection: function(){
      this.newId += 1;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.card {
  width: 300px;
}
button {
  background-color: transparent;
  border: transparent;
}
</style>
