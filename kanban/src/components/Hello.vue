<template>
  <div class="ui container">
    <h1>TAMBAL-BAN</h1>
    <button @click="showw()" type="button" class="ui fluid basic black button">Start Project</button>
    <div v-if="shown === true" class="ui segment">
      <create></create>
    </div>
    <div class="ui stackable grid four column container segment">
      <div class="four wide column">
        <div class="ui segment log">
          <h2>Back Log</h2>
        </div>
        <backlog></backlog>
      </div>
      <div class="four wide column">
        <div class="ui segment todo">
          <h2>Todo</h2>
        </div>
        <todo></todo>
      </div>
      <div class="four wide column">
        <div class="ui segment doing">
          <h2>Doing</h2>
        </div>
        <doing></doing>
      </div>
      <div class="four wide  column">
        <div class="ui segment done">
          <h2>Done</h2>
        </div>
        <done></done>
      </div>
    </div>
  </div>
</template>
<script>
import backlog from '@/components/backlog'
import todo from '@/components/todo'
import doing from '@/components/doing'
import done from '@/components/done'
import create from '@/components/create'

export default {
  components: {
    backlog,
    todo,
    doing,
    done,
    create
  },
  name: 'hello',
  data () {
    return {
      shown: false
    }
  },
  methods: {
    showw () {
      if (this.true === true) {
        this.true = false
      } else {
        this.shown = true
      }
    }
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

.doing {
  color: white;
  background-color: #2196F3;
}
.todo {
  color: white;
  background-color: #F44336;
}
.log {
  color: white;
  background-color: #FF9800;
}
.done {
  color: white;
  background-color: #4CAF50;
}

</style>
