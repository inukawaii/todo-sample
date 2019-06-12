<template>
  <li v-show="!done_is_invisible || !is_done">  
    <input type="checkbox" v-model="is_done">  
      <span>
          <input type="text" v-model="title" v-bind:disabled="is_done">
      </span>
    <select v-bind:disabled="is_done" v-model="rep">
        <option v-for="member in members" v-bind:value="member" v-bind:key="member">{{member}}</option>
    </select>
    <input type="date" v-model="date" v-bind:disabled="is_done">
  </li>
</template>

<script>
export default {
  props: {
    members: Array,
    title: String,
    date: Date,
    rep: String,
    done_is_invisible: Boolean
  },
  data: function() {
      return {
        is_done: false,
      }
  }
}
</script>

<style scoped>
</style>
