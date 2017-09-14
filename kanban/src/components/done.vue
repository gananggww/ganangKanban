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
          <button class="ui mini basic button" type="button" @click="goDoing(all['.key'], all.title, all.desc, all.assign)">Doing</button>
          <button class="ui mini basic button" type="button" @click="remove(all['.key'])">Delete</button>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
export default {
  firebase: function () {
    return {
      backlog: this.$db.ref('task/done/')
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
      this.$db.ref(`task/done/${id}`).remove()
    },
    remove (id) {
      this.$db.ref(`task/done/${id}`).remove()
    }
  }
}
</script>

<style lang="css">
</style>
