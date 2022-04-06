<template>
  <div id="app">
    <CarouselComponent>
      <CarouselSlide>
        Salut les gens
      </CarouselSlide>
      <CarouselSlide>
        Aurevoir les gens
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
