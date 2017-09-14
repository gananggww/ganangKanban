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
          <button class="ui mini basic button" type="button">Delete</button>
          <button class="ui mini basic button" type="button">Todo</button>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
export default {
  data () {
    return {
      title: '',
      desc: '',
      assign: ''
      // backlog: this.$db.ref('task/backlog/')
    }
  },
  firebase: function () {
    return {
      backlog: this.$db.ref('task/backlog/')
    }
  },
  methods: {
    gotodo () {
      this.$db.ref('task/backlog/').push({
        title: this.title,
        desc: this.desc,
        assign: this.assign
      })
      this.title = ''
      this.disc = ''
      this.assign = ''
      // this.$db.ref('task/backlog/')
    },
    remove () {
      this.$db.ref('task/backlog/').remove()
    }
  }
}
</script>

<style lang="css">
</style>
