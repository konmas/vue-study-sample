<template>
  <div>
    <form v-on:submit.prevent="sendTodo">
      <input v-model="todo">
      <input type="submit" val="追加">
    </form>
    <ui v-for="(item, index) in list" :key="index">
      <li v-on:click='doneTodo(item)'>
        <span>
          status: {{item.status}}
        </span>
        <s v-if="item.status === 'done'">
          {{item.text}}
        </s>
        <span v-else>
          {{item.text}}
        </span>
      </li>
    </ui>
  </div>
</template>

<script>
export default {
  name: 'TodoList',
  data() {
    return {
      todo: '',
      list: []
    }
  },
  methods: {
    sendTodo () {
      this.list.push({
        text: this.todo,
        status: 'todo'
      })
      this.todo = ''
    },
    doneTodo (item) {
      if (item.status === 'done') {
        item.status = 'todo'
      } else {
        item.status = 'done'
      }
    }
  },
  created () {
  },
  computed: {
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
