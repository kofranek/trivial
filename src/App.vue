<template>
  <!--  <HelloWorld msg="Welcome to Your Vue.js App"/>-->
  <div>
    <h2>počet poznámek: {{ counter }}</h2>
    <form>
      <input type="text" placeholder="zadej poznámku" v-model="notes">
      <button @click.prevent="submit">zadej poznámku</button>
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
      notes: ['pozn1', 'pozn2'],
      counter: 0

    }
  },
  methods: {
    addNote (event) {
      this.notes.push(event.target.value)
      this.counter++
      console.log(this.notes)
    }
  }

}
</script>

<style lang="scss">

</style>
