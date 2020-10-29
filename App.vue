<template>
  <view class="container">
    <StatusBar color="#FFCE00"/>
    <Header title="todo app" />

    <!-- Text Input -->
    <view class="inputContainer">
      <text-input class="input" v-model="newTodoText" />
      <touchable-opacity class="add-btn" :on-press="addTodo">
        <text class="btn-text">add</text>  
      </touchable-opacity>
    </view>

    <!-- Todo List -->
    <view class="todo" v-for="todo in todos" v-bind:key="todo.id">
      <touchable-opacity :on-press="() => todoFinished(todo.id)">
        <text class="todo-text done" v-if="todo.done">
          {{ todo.title }}
        </text>
        <text class="todo-text" v-else>
          {{ todo.title }}
        </text>
      </touchable-opacity>
      <touchable-opacity :on-press="() => todoRemoved(todo.id)">
        <text class="remove-btn-text">Remove</text>
      </touchable-opacity>
      
    </view>
  </view>
</template>

<script>
import StatusBar from './components/StatusBar';
import Header from './components/Header';

export default {
  components: {
    StatusBar,
    Header
  },
  data: {
    newTodoText: '',
    todos: [
      {
        id: 1,
        title: 'Go to work',
        done: false
      },
      {
        id: 2,
        title: 'Go to school',
        done: false
      }
    ]
  },
  methods: {
    addTodo(){
      this.todos.push({
        id: this.todos.length + 1,
        title: this.newTodoText,
        done: false
      });
      this.newTodoText = '';
    },
    todoFinished(id){
      this.todos = this.todos.map(todo => {
        if(todo.id == id) {
          todo.done = !todo.done;
        }
        return todo;
      });
    },
    todoRemoved(id){
      this.todos = this.todos.filter(todo => todo.id !== id);
    }
  }
}
</script>

<style>
.container {
  background-color: white;
  flex: 1;
}
.inputContainer {
  flex-direction: row;
  justify-content: center;
  align-items: stretch;
}
.input {
  flex: 1;
  height: 35;
  background-color: #F3F3F3;
  font-size: 18;
  color: #888;
}
.add-btn {
  width: 100;
  height: 35;
  background-color: #FFCE00;
  justify-content: center;
  align-items: center;
}
.btn-text {
  text-transform: uppercase;
  font-size: 18;
  font-weight: 700;
}
.todo {
  flex-direction: row;
  justify-content: space-between;
  padding: 15;
}
.remove-btn-text {
  font-size: 18;
  color: red;
}
.todo-text {
  font-size: 18;
}
.done {
  color: #AAA;
}
</style>
