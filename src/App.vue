<template>
  <div id="app">
    <h1>TODOリスト</h1>
    <div class="form-check">
        <input type="checkbox" class="form-check-input" id="display_none" v-model="display_none">
        <label for="display_none">完了したTODOは非表示にする</label>
    </div>
    
    <ul>
      <Todo
        v-for="(todo, index) in todos"
        v-bind:key="index"
        v-bind:todo="todo"
        v-bind:members="members"
        v-bind:display_none="display_none"
      />
      <li>
        <input type="textarea" v-model="new_todo" placeholder="TODOを入力してください">
        <select v-model="rep" size="1">
          <option value='' disabled selected>担当者を選択</option>
          <option v-for="member in members" v-bind:value="member" v-bind:key="member">
            {{member}}
          </option>
        </select>
        <input type="date" v-model="new_date">
        <button v-on:click="add">追加</button>
      </li>
    </ul>
  </div>
</template>

<script>
import Todo from "./components/Todo.vue";

export default {
  name: "app",
  components: {
    Todo
  },
  data: function() {
    return {
      members: ["さざえ", "かつお", "わかめ"],
      new_todo: "",
      new_date: null,
      todos: [],
      rep: '',
      display_none:false
    };
  },
  methods: {
    add: function() {
      if(this.valid) {
        this.todos.push(
          {
            title: this.new_todo,
            date: this.date,
            rep: this.rep
          }
        )
        this.new_todo = ''
        this.new_date = null
        this.rep = null
      }
    }
  },
  computed: {
    valid: function() {
      return this.new_todo != ''
    }
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
