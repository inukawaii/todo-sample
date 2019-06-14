<template>
  <li class="list-group-item container" v-show="!display_none || !is_done">
    <div class="row">
      <div class="col-4">
        <input type="text" class="form-control" v-model="todo.title" v-bind:disabled="is_done">
      </div>
      <div class="col-3">
        <select class="custom-select" v-bind:disabled="is_done" v-model="todo.rep">
          <option v-for="member in members" v-bind:value="member" v-bind:key="member">{{member}}</option>
        </select>
      </div>
      <div class="col-3">
        <input type="date" class="form-control" v-model="date" v-bind:disabled="is_done">
      </div>
      <div class="col-2">
        <input type="checkbox" v-model="is_done" class="form-check">
      </div>
    </div>
  </li>
</template>

<script>
export default {
  props: {
    members: Array,
    date: Date,
    todo: Object,
    display_none: Boolean
  },
  data: function() {
    return {
      is_done: false
    };
  }
};
</script>

<style scoped>
</style>
