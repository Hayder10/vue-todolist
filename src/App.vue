<template>
    <nav class="navbar">
      <img src="./assets/logo.svg" width="50"/>
      <div class="brand">Todo List App</div>
    </nav>
    <main class="container">
      <section>
        <form class="add-todo-form">
          <input type="text" placeholder="Todo Title">
          <div>
            <button>Add Task</button>
          </div>
        </form>
      </section>
      <section>
        <div class="todo">
          <p>Pasear al Perro</p>
          <div>
            <button class="remove-todo-btn">&times;</button>
          </div>
        </div>
      </section>
    </main>

</template>

<script setup>
</script>


<style scoped>
.navbar{
  display: flex;
  align-items: center;
  background-color: var(--navbar-color);
  padding: 20px;
  margin-bottom: 30px;
}
.brand{
  font-size: 2rem;
}

.add-todo-form{
  display: flex;
  justify-content: space-between;
}
.add-todo-form input{
  width: 80%;
  border: solid 2px var(--accent-color);
}
.add-todo-form button{
  background: var(--accent-color);
  color: var(--text-color);
  border: none;
  height: 50px;
}
.todo{
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: var(--accent-color);
  margin-top: 30px;
  padding: 0 20px 0 20px;
  border-radius: 5px;
}
.remove-todo-btn{
  border-radius: 50%;
  border: none;
  width: 40px;
  height: 40px;
}

</style>
