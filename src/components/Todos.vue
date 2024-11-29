<template>
  <div class="todos">
    <input 
      type="text" 
      v-model="newTodo" 
      @keypress.enter="addTodo"
      placeholder="Add a new todo..."
    />

    <transition name="switch" mode="out-in">
      <div v-if="todos.length">
        <transition-group tag="ul" name="todo-list" appear>
          <li v-for="todo in todos" :key="todo.id" @click="deleteTodo(todo.id)">
            {{ todo.text }}
          </li>
        </transition-group>
      </div>
      <div v-else class="empty-todos">
        Woohoo, nothing left todo!
      </div>
    </transition>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  setup(props, { emit }) {
    const todos = ref([
      { text: 'make the bed', id: 1 },
      { text: 'play video games', id: 2 },
    ])
    const newTodo = ref('')

    const addTodo = () => {
      if (newTodo.value) {
        const id = Math.random()
        todos.value = [{ text: newTodo.value, id }, ...todos.value]
        newTodo.value = ''
      } else {
        emit('badValue')
      }
    }

    const deleteTodo = (id) => {
      todos.value = todos.value.filter(todo => todo.id != id)
    }

    return { todos, addTodo, deleteTodo, newTodo }
  }
}
</script>

<style>
  .todos {
    max-width: 400px;
    margin: 20px auto;
    position: relative;
  }
  input {
    width: 100%;
    padding: 12px;
    border: 1px solid #eee;
    border-radius: 10px;
    box-sizing: border-box;
    margin-bottom: 20px;
  }
  .todos ul {
    position: relative;
    padding: 0;
  }
  .todos li {
    list-style-type: none;
    display: block;
    margin-bottom: 10px;
    padding: 10px;
    background: white;
    box-shadow: 1px 3px 5px rgba(0,0,0,0.1);
    border-radius: 10px;
    width: 100%;
    box-sizing: border-box;
  }
  .todos li:hover {
    cursor: pointer;
  }

  .empty-todos {
    padding: 12px;
  }

/* todo-list transition */

/* initial state */
.todo-list-enter-from {
  opacity: 0;
  transform: scale(.6);
}
.todo-list-enter-to {
  opacity: 1;
  transform: scale(1);
}

.todo-list-enter-active {
  transition: all .4s ease;
}

.todo-list-leave-from {
  opacity: 1;
  transform: scale(1);
}
.todo-list-leave-to {
  opacity: 0;
  transform: scale(.6);
}
.todo-list-leave-active {
  transition: all .4s ease;
  position: absolute;
}

.todo-list-move {
  transition: all 0.3s ease;
}

/* switch components */
.switch-enter-from, .switch-leave-to {
  opacity: 0;
  transform: translateY(20px);
}

/* não precisamos dessas propriedades, pois são os defaults */
/* .switch-enter-to, .switch-leave-from {
  opacity: 1;
  transform: translateY(0);
} */

.switch-enter-active, .switch-leave-active {
  transition: all .2s ease;
}

</style>