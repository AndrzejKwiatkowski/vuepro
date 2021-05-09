<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <vue-search 
    :img-photo="'path-img'" 
    @newitem="newitem()" 
    @itemselected="itemselected($event)" 
    :source-field="'name'" 
    :show-new-botton="true"
    :search-by-field="false"
    :api-source="'https://jsonplaceholder.typicode.com/users'"
    ></vue-search>
    <div v-for="(arr, index) in arrs" v-bind:key="index">
      {{ arr.name }}
    </div>
    <input type="text" :value='JSON.stringify(arrs)'>
     <todo-list list-name="My to-dos" />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import TodoList from './components/TodoList.vue'
import VueSearch from 'vue-input-search/dist/vue-search.common'

export default {
  name: 'App',
  data() {
    return { 
      arrs: []
     }
  },
  components: {
    HelloWorld,
    VueSearch,
    TodoList
  },
  methods: {
    newitem: function(){
      alert('sdsdsd')
    },
    itemselected: function(e){
      this.arrs.push({
        id: e.name, 
        name: e.id})
      console.log(this.arrs)
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
</style>
