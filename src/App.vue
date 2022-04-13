<template>
  <div id="app">
    <div class="d-flex">
      <!-- section -->
      <div v-for="(section, index) in sectionList" v-bind:key="index">
        <task-section :newId="newId" v-bind:section="section"></task-section>
      </div>
      <!-- add section button -->
      <div>
        <button @click="createSection()" type="button" class="btn btn-light shadow">ADD SECTION</button>
      </div>
    </div>
    
  </div>
</template>

<script>
import TaskSection from './components/TaskSection.vue'

export default {
  name: 'App',
  components: {
    TaskSection,
  },
  data() {
    return {
      sectionList: [],
      newId: 0,
    }
  },
  methods: {
    createSection: function(){
      const newSection = {
        id: this.newId,
        sectionName: "",
      }
      this.sectionList.push(newSection);
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
