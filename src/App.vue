<template>
  <main class="container">
    <Navbar />
    <Alert message="To do Title is required!" :show="showAlert" @close="showAlert = false" type="danger"/>
    <section>
     <AddTodoForm @submit="addTodo"/>
    </section>
    <section>
      <div v-for="(todo) in todos" class="todo" v-bind:key="todo.id">
        <p>{{ todo.title }}</p>
        <div>
          <button @click="removeTodo(todo)" class="remove-todo-btn">&times;</button>
        </div>
      </div>
    </section>
  </main>

</template>

<script>
import AddTodoForm from './components/AddTodoForm.vue';
import Alert from './components/Alert.vue'
import Navbar from './components/Navbar.vue';

export default {
    components:{
      Alert,Navbar,AddTodoForm
    },
    data() {
        return {
            todos: [],
            showAlert: false,
        };
    },
    methods: {
        addTodo(title) {
            if (title === "") {
                this.showAlert = true;
                return;
            }
            this.todos.push({
                title,
                id: Math.floor(Math.random() * 1000)
            });
            this.todoTitle = "";
        },
        removeTodo(todoTitle) {
            this.todos = this.todos.filter(todo => todo !== todoTitle);
        }
    },
    components: { Alert, Navbar, AddTodoForm }
}
</script>


<style scoped>

.todo {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: var(--accent-color);
  margin-top: 30px;
  padding: 0 20px 0 20px;
  border-radius: 5px;
}

.remove-todo-btn {
  border-radius: 50%;
  border: none;
  width: 40px;
  height: 40px;
  font-size: 30px;
  color: var(--text-color);
  background: var(--danger-color);
  cursor: pointer;
}
</style>
