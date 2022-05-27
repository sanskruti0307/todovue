<template>
  <div id="app">
    <div class="container">
      <div class="card">
        <h1 class="card-title text-center">To Do List</h1>
        <img
          src="@/assets/images/checklist.png"
          style="height: 50px; width: 50px"
          class="card-img1"
        />
        <div class="card-body">
          <h5 class="card-subtitle text-center">
            What do you want to get done today?
          </h5>
          <input
            class="d-flex justify-content-center align-items-center"
            type="text"
            v-model="todo"
            placeholder="e.g. Workout"
          />
          <button
            class="btn btn-outline-secondary"
            type="button"
            id="btn-id"
            style="
              padding: 10px;
              width: 100px;
              margin-left: 430px;
              margin-top: 20px;
            "
            @click="storeTodo()"
          >
            Add
          </button>
          <button
            class="btn btn-outline-success"
            type="button"
            id="btn-id"
            style="
              padding: 10px;
              width: 100px;
              margin-top: 20px;
              margin-left: 20px;
            "
            @click="clrAll()"
          >
            Clear
          </button>

          <table class="table">
            <thead>
              <tr>
                <th scope="col"></th>
              </tr>
            </thead>
          </table>

          <ol>
            <li v-for="todo in todos" :key="todo.id">
              {{ todo }}
              <button
                class="btn btn-outline-danger"
                v-on:click="remove"
                style="
                  padding: 8px;
                  width: 100px;
                  margin-left: 380px;
                  border-radius:12px;
                  font-size:16px;
                "
              >
                Remove
              </button>
              </li>
          </ol>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
  data() {
    return {
      todo: "",
      todos: [],
    };
  },
  methods: {
    storeTodo() {
      console.log("storeTodo");
      this.todos.push(this.todo);
      console.log("todo", this.todos);
      this.todo = "";
    },
    clrAll() {
      console.log("clrAll");
      this.todos.length = 0;
    },
    remove() {
      console.log("remove");
      this.todos.pop(this.todo);
    },
    
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Lobster&family=Roboto:wght@300&display=swap');
body{
  background: rgb(178,144,205);
  background: linear-gradient(90deg, rgba(178,144,205,1) 0%, 
  rgba(123,54,208,1) 49%, rgba(199,155,196,0.9640231092436975) 100%);
}

#app{
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px; 
}

h1{
  font-family: 'Lobster', cursive;
}

.card-img1{
  margin-left: 540px;
}

input{
  width: 400px;
  padding: 10px;
  margin-left: 350px;
  margin-top: 20px;
}

li{
  margin-left: 380px;
  font-size: 20px;
  font-weight: 900;
  margin-top: 10px;
  font-family: 'Roboto', sans-serif;
}

.card{
  border-radius: 22px;
}

</style>
