<template>
  <div>
    <div class="ui link card">
      <div class="content">
        <div class="header">Cute Dog</div>
        <div class="meta">
          <span class="category">Animals</span>
        </div>
        <div class="description">
          <p></p>
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
      status: 'backlog'
    }
  }
}
</script>

<style lang="css">
</style>
