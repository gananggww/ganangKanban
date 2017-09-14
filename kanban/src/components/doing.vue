<template>
  <div>
    <div class="ui link card" v-for="all in backlog">
      <div class="content">
        <div class="header">{{all.title}}</div>
        <div class="meta">
          <span class="category">{{all.assign}}</span>
        </div>
        <div class="description">
          <p>{{all.desc}}</p>
        </div>
      </div>
      <div class="extra content">
        <div class="author">
          <button class="ui mini basic button" type="button" @click="goTodo(all['.key'], all.title, all.desc, all.assign)">Todo</button>
          <button class="ui mini basic button" type="button" @click="remove(all['.key'])">Delete</button>
          <button class="ui mini basic button" type="button" @click="goDone(all['.key'], all.title, all.desc, all.assign)">Done</button>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
export default {
  firebase: function () {
    return {
      backlog: this.$db.ref('task/doing/')
    }
  },
  methods: {
    goDone (id, title, desc, assign) {
      this.$db.ref('task/done/').push({
        title: title,
        desc: desc,
        assign: assign
      })
      this.title = ''
      this.disc = ''
      this.assign = ''
      this.$db.ref(`task/doing/${id}`).remove()
    },
    remove (id) {
      this.$db.ref(`task/doing/${id}`).remove()
    },
    goTodo (id, title, desc, assign) {
      this.$db.ref('task/todo/').push({
        title: title,
        desc: desc,
        assign: assign
      })
      this.title = ''
      this.disc = ''
      this.assign = ''
      this.$db.ref(`task/doing/${id}`).remove()
    }
  }
}
</script>

<style lang="css">
</style>
