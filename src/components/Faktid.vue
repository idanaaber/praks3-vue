<template>
  <div>
   <h1>Numbri faktid</h1>
   <p>Huvitavad faktid iga numbri kohta</p>
   <input type="number" min="0" v-model="number">
   <input type="number" min="0" v-model="increment">
   <p v-for></p>
  </div>
</template>

<script>
const axios = require('axios')

export default {
  name: 'Faktid',
  data() {
      return {
        data: '',
        number: 0, 
        increment: 0
        
    }
  },

  methods: {
    getFacts() {
      if (this.number !== ''){


      let url = `http://numbersapi.com/${this.number}..${parseInt(this.number) + parseInt(this.increment)}`

      axios.get(url)
      .then(response => {
        this.data = response.data
      })
      .catch(error => {
        console.log(error)
       })
    }
  }
  },
  watch: {
    
      number() {
        this.getFacts()
      },

      increment() {
        this.getFacts()
      }


      }

  }
 


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>


</style>
