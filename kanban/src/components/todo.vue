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
          <button class="ui mini basic button" type="button" @click="goBacklog(all['.key'], all.title, all.desc, all.assign)">Backlog</button>
          <button class="ui mini basic button" type="button" @click="remove(all['.key'])">Delete</button>
          <button class="ui mini basic button" type="button" @click="goDoing(all['.key'], all.title, all.desc, all.assign)">Doing</button>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
export default {
  firebase: function () {
    return {
      backlog: this.$db.ref('task/todo/')
    }
  },
  methods: {
    goDoing (id, title, desc, assign) {
      this.$db.ref('task/doing/').push({
        title: title,
        desc: desc,
        assign: assign
      })
      this.title = ''
      this.disc = ''
      this.assign = ''
      this.$db.ref(`task/todo/${id}`).remove()
    },
    remove (id) {
      this.$db.ref(`task/todo/${id}`).remove()
    },
    goBacklog (id, title, desc, assign) {
      this.$db.ref('task/backlog/').push({
        title: title,
        desc: desc,
        assign: assign
      })
      this.title = ''
      this.disc = ''
      this.assign = ''
      this.$db.ref(`task/todo/${id}`).remove()
    }
  }
}
</script>

<style lang="css">
</style>
