<template>
 <div>
   <textarea v-model="model"></textarea><br />
   <button class="primary" @click="skillMethod()">
       Submit
   </button>
 </div>
</template>
<script>
import axios from 'axios'
export default {
  data () {
    return {
      model: ''
    }
  },
  methods: {
    skillMethod () {
      axios.post('https://safe-cliffs-38280.herokuapp.com/skills', {
        skill: this.model
      })
      .then(function (response) {
        console.log(response)
      })
      .catch(function (error) {
        console.log(error)
      })
    }
  }
}</script>
