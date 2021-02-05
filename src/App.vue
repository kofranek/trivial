<template>
  <!--  <HelloWorld msg="Welcome to Your Vue.js App"/>-->
  <h1 :style="{color: inputValue.length<5?
  'darkred':
  'darkblue',
  fontSize: inputValue.length<10?
  '2rem':
  '4rem'}"
  >seznam poznámek</h1>
  <div>
    <span v-if="notes.length===0">Nejsou žádné poznámky</span>
  </div>
  <div>
    <input
        type="text"
        :placeholder="placeholderString"
        v-model="inputValue"
        @input="newNote"
        @keypress.enter="addNewNote"
    />
  </div>
  <h2>{{ inputValue }}</h2>
  <button @click="addNewNote">přidat</button>
  <hr/>
  <div>
    <strong>počet poznámek {{ notes.length }}|{{ doubleCount }}</strong>
  </div>
  <ul>
    <li v-for="(item) in notes" :key="item.id">
      {{ item.text }}
      <button @click="deleteNote(item)">odstranit poznámku</button>
    </li>
  </ul>
  <hr/>

</template>

<script>
//  import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  data () {
    return {
      placeholderString: 'zadej poznámku',
      counter: 0,
      inputValue: '',
      notes: []
    }
  },
  methods: {
    // newNote (event) {
    //   console.log('newNote')
    //   this.inputValue = event.target.value
    //   this.counter++
    //   console.log(this.notes)
    // },
    addNewNote () {
      console.log('addNewNote inputValue.trim().length=', this.inputValue.trim().length)
      if (this.inputValue.trim().length > 0) {
        const item = {}
        item.id = new Date().toUTCString()
        item.text = this.inputValue
        this.notes.push(item)
        this.inputValue = ''
      }
    },
    deleteNote (note) {
      console.log('delete note')
      if (this.notes.length > 0) {
        this.notes.splice(note, 1)
      }
    }
  },
  computed: {
    doubleCount () {
      console.log('double count')
      return this.notes.length * 2
    }
  },
  watch: {
    inputValue (value) {
      console.log('inputValue changed=', value)
      console.log('notes=', this.notes)
    },
    notes (value) {
      console.log('notes changed=', value)
    },
    counter (value) {
      console.log('counter changed=', value)
    }
  }
}
</script>

<style lang="scss">

</style>
