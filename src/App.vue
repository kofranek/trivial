<template>
  <!--  <HelloWorld msg="Welcome to Your Vue.js App"/>-->
  <div>
    <h2>počet poznámek: </h2>
    <form>
      <input type="text" placeholder="zadej poznámku" v-model="notes">
      <button @click="addNote">zadej poznámku</button>
      <hr/>
      <h3>{{ notes.length }}</h3>
    </form>
  </div>

</template>

<script>
//  import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  data () {
    return {
      notes: []
    }
  },
  methods: {
    addNote (event) {
      this.notes.push(event.target.value)
      console.log(this.notes)
    }
  }

}
</script>

<style lang="scss">

</style>
