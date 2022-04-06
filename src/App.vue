<template>
  <div id="app">
    <CarouselComponent>
      <CarouselSlide v-for="n in slides" :key="n" :index="n - 1">
       <div style="position: absolute; left: 0; right: 0; text-align: center; top: 50%; color: #FFF; font-size: 16px"> Slide numéro {{ n }}</div>
        <img :src="'https://picsum.photos/630/300?random=' + n" width="100%"> 
      </CarouselSlide>
    </CarouselComponent>
    <button @click="addSlide">Ajouter un slide</button>
    <button @click="removeSlide">Supprimer une slide</button>

    <p>Relation Parent/child test : {{ todos }}</p>
    <TodosApp v-model="todos" @input="updateTodos"></TodosApp>
    <button @click="addTodo">Ajouter une tache</button>
  </div>
</template>

<script>
import CarouselComponent from './components/carousel/CarouselComponent.vue';
import CarouselSlide from './components/carousel/CarouselSlide.vue';
import TodosApp from './components/TodosApp.vue'


export default { 
  name: 'App',
  data() {
    return {
      slides: 5,
      todos: [{
        name: 'Test de todo',
        completed: false
      }]
    }
  },
  components: {
    CarouselComponent,
    CarouselSlide,
    TodosApp
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
    },
    addSlide() {
      this.slides++
    },
    removeSlide() {
      if(this.slides > 1) this.slides--;
    }
  }
}
</script>

<style src="./components/todos.css">

</style>