<template>
  <div>
    <form class="ui form">
      <div class="field">
        <label>Judul</label>
        <input type="text" name="first-name" v-model="title">
      </div>
      <div class="field">
        <label>Deskripsi</label>
        <input type="text" name="last-name" v-model="desc">
      </div>
      <div class="field">
        <label>Assign</label>
        <input type="text" name="last-name" v-model="assign">
      </div>
      <button class="ui fluid button" type="submit" @click="create()">Submit</button>
    </form>
  </div>
</template>
<script>
export default {
  data () {
    return {
      title: '',
      desc: '',
      assign: ''
    }
  },
  methods: {
    create () {
      this.$db.ref('task/backlog/').push({
        title: this.title,
        desc: this.disc,
        assign: this.assign
      })
      this.title = ''
      this.disc = ''
      this.assign = ''
    }
  },
  mounted () {
    console.log(this.$db.ref('task/backlog/'))
  }
}
</script>

<style lang="css">
</style>
