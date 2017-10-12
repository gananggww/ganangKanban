<template>
  <div>
    <div class="ui fluid link card" v-for="all in backlog">
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
          <button class="ui mini basic button" type="button" @click="remove(all['.key'])">Delete</button>
          <button class="ui mini basic button" type="button" @click="gotodo(all['.key'], all.title, all.desc, all.assign)">Todo</button>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
export default {
  data () {
    return {
      // backlog: this.$db.ref('task/backlog/')
    }
  },
  firebase: function () {
    return {
      backlog: this.$db.ref('task/backlog/')
    }
  },
  methods: {
    gotodo (id, title, desc, assign) {
      this.$db.ref('task/todo/').push({
        title: title,
        desc: desc,
        assign: assign
      })
      this.title = ''
      this.disc = ''
      this.assign = ''
      this.$db.ref(`task/backlog/${id}`).remove()
    },
    remove (id) {
      this.$db.ref(`task/backlog/${id}`).remove()
    }
  }
}
</script>

<style lang="css">
</style>
