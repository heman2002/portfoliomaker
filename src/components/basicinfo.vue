<template>
  <div>
    <div class="layout-padding">
      <strong>First name:</strong> <input v-model="firstname" placeholder="First name">
      <br>
      <strong>Last name:</strong> <input v-model="lastname" placeholder="Last name">
      <br />
      <strong>Email id:</strong> <input v-model="emailid" placeholder="Email id">
      <br />
      <strong>Phone no:</strong> <input v-model="phoneno" placeholder="Phone number">
      <br />
      <strong>Address:</strong> <input v-model="address" placeholder="Address">
      <br />
      <button class="primary" @click="clickMethod()">
          Submit
      </button>
    </div>
    <div v-html="reloadText">
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      firstname: '',
      lastname: '',
      emailid: '',
      phoneno: '',
      address: '',
      reloadText: ''
    }
  },
  methods: {
    clickMethod () {
      console.log('firstname:' + this.firstname)
      console.log('lastname:' + this.lastname)
      console.log('emailid:' + this.emailid)
      console.log('phoneno:' + this.phoneno)
      console.log('address:' + this.address)
      axios.post('https://safe-cliffs-38280.herokuapp.com/template2', {
        firstname: this.firstname,
        lastname: this.lastname,
        emailid: this.emailid,
        phoneno: this.phoneno,
        address: this.address
      })
      .then(function (response) {
        console.log(response)
      })
      .catch(function (error) {
        console.log(error)
      })
    }
  }
}
</script>
