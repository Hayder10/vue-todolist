<template>
  <nav class="navbar">
    <img src="./assets/logo.svg" width="50" />
    <div class="brand">Todo List App</div>
  </nav>
  <main class="container">
    <Alert message="To do Title is required!" :show="showAlert" @close="showAlert = false" type="info"/>
    <section>
      <form class="add-todo-form">
        <input v-model="todoTitle" type="text" placeholder="Todo Title">
        <div>
          <button @click.prevent="addTodo">Add Task</button>
        </div>
      </form>
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
import Alert from './components/Alert.vue'

export default {
    components:{
      Alert,
    },
    data() {
        return {
            todoTitle: "",
            todos: [],
            showAlert: false,
        };
    },
    methods: {
        addTodo() {
            if (this.todoTitle === "") {
                this.showAlert = true;
                return;
            }
            this.todos.push({
                title: this.todoTitle,
                id: Math.floor(Math.random() * 1000)
            });
            this.todoTitle = "";
        },
        removeTodo(todoTitle) {
            this.todos = this.todos.filter(todo => todo !== todoTitle);
        }
    },
    components: { Alert }
}
</script>


<style scoped>
.navbar {
  display: flex;
  align-items: center;
  background-color: var(--navbar-color);
  padding: 20px;
  margin-bottom: 30px;
}

.brand {
  font-size: 2rem;
}


.add-todo-form {
  display: flex;
  justify-content: space-between;
}

.add-todo-form input {
  width: 80%;
  border: solid 2px var(--accent-color);
}

.add-todo-form button {
  background: var(--accent-color);
  color: var(--text-color);
  border: none;
  height: 50px;
}

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
