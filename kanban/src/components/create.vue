<template>
  <div>
    <form class="ui form">
      <div class="field">
        <label>Judul</label>
        <input type="text" v-model="title">
      </div>
      <div class="field">
        <label>Deskripsi</label>
        <input type="text" v-model="desc">
      </div>
      <div class="field">
        <label>Assign</label>
        <input type="text" v-model="assign">
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
        desc: this.desc,
        assign: this.assign
      })
      this.title = ''
      this.disc = ''
      this.assign = ''
    }
  },
  mounted () {
    // console.log(this.create())
  }
}
</script>

<style lang="css">
</style>
