<template>
    <section class="todoapp">
        <header class="header">
            <h1>Todos</h1>
            <input type="text" class="new-todo" placeholder="Ajouter une tâche" v-model="newTodo" @keyup.enter="addTodo">
        </header>
        <div class="main">
            <input id="toggle-all" type="checkbox" class="toggle-all" v-model="allDone">
            <label for="toggle-all">Tout completer</label>

            <ul class="todo-list">
                <li class="todo" v-for="(todo, index) in showTasks" :key="index" :class="{completed: todo.completed}">
                    <div class="view">
                        <input type="checkbox" v-model="todo.completed" class="toggle">
                        <label for="">{{ todo.name }}</label>
                    </div>
                </li>
            </ul>
        </div> 
        <footer class="footer">
            <span class="todo-count"><strong>{{remaining}}</strong> tâche(s) à faire</span>
            <ul class="filters">
                <li><a href="#" :class="{selected: filter == 'all'}" @click.prevent="filter = 'all'">Toutes</a></li>
                <li><a href="#" :class="{selected: filter == 'todo'}" @click.prevent="filter = 'todo'">À faire</a></li>
                <li><a href="#" :class="{selected: filter == 'done'}" @click.prevent="filter = 'done'">Faites</a></li>
            </ul>
        </footer>
    </section>
</template>

<script>
export default {
    data() {
        return {
            todos: [{
                name: 'Tache de test',
                completed: false
            },
            {
                name: 'Tache de test',
                completed: false
            }],
            newTodo: '',
            filter: 'all',
        }
    },

    methods: {
        addTodo() {
            if(!this.newTodo.trim()) return;
            this.todos.push({
                name: this.newTodo,
                completed: false
            });
            this.newTodo = '';
        },
    },

    computed: {
        remaining() {
            const tasks = this.todos.filter(task => !task.completed);
            return tasks.length;
        },
        showTasks() {
            if(this.filter == 'todo') return this.todos.filter(task => !task.completed);
            if(this.filter == 'done') return this.todos.filter(task => task.completed);
            return this.todos;
        },
        allDone: {
            get () {
                return this.remaining === 0;
            },
            set (value) {
                this.todos.forEach(todo => todo.completed = value)
            }
        }
    }

}
</script>

<style src="./todos.css">

</style>