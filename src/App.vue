<template>
  <div id="app">
    <img @mouseenter="changeStatus('open')" alt="Vue logo" src="./assets/logo.png">
    <div>
      <button @click="changeStatus('all')">all</button>
      <button @click="changeStatus('open')">open</button>
      <button @click="changeStatus('close')">close</button>
    </div>
    <Sample 
      v-for="item in filteredItems"
      :key="item.id"
      :message="item.message"
      :number="item.number"
    />
  </div>
</template>

<script>
import Sample from './components/Sample'

export default {
  name: 'App',
  components: {
    Sample
  },
  data(){
    return {
      currentStatus: "all",
      items: [{
        id: 1,
        message: "hoge",
        number: 1,
        status: "open"
      },{
        id: 2,
        message: "hoo",
        number: 2,
        status: "close"
      }]
    }
  },
  methods: {
    changeStatus(status) {
      this.currentStatus = status
    }
  },
  computed: {
    filteredItems() {
      if (this.currentStatus === "all") {
        return this.items
      }
      return this.items.filter(item => item.status === this.currentStatus)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
