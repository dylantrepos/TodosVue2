<template>
  <div id="app">
    <CarouselComponent>
      <CarouselSlide>
       <div style="position: absolute; left: 0; right: 0; text-align: center; top: 50%; color: #FFF; font-size: 16px"> Salut les gens</div>
        <img src="https://picsum.photos/630/300" width="100%"> 
      </CarouselSlide>
      <CarouselSlide>
       <div style="position: absolute; left: 0; right: 0; text-align: center; top: 50%; color: #FFF; font-size: 16px"> Aurevoir les gens</div>
        <img src="https://picsum.photos/630/300"  width="100%">
      </CarouselSlide>
    </CarouselComponent>
    <TodosApp v-model="todos" @input="updateTodos"></TodosApp>
    <button @click="addTodo">Ajouter une tache</button>
  </div>
</template>

<script>
import TodosApp from './components/TodosApp.vue'
import CarouselComponent from './components/carousel/CarouselComponent.vue'
import CarouselSlide from './components/carousel/CarouselSlide.vue'

export default {
  name: 'App',
  data() {
    return {
      todos: [{
        name: 'Test de todo',
        completed: false
      }]
    }
  },
  components: {
    CarouselComponent,
    CarouselSlide,
    TodosApp,
  },
  methods: {
    addTodo() {
      this.todos.push({
        name: 'Jeanjean',
        completed: false
      })
    },
    updateTodos(newTodos) {
      this.todos = newTodos;
    }
  }
}
</script>

<style src="./components/todos.css">

</style>