<template>
  <div>
    <form>
      <input type="submit" value="Add new entry" @click="addEntryMethod()"/>
    </form>
    <div v-if="ok === '1'">
      <div class="layout-padding">
        <strong>Job Title:</strong> <input v-model="jobtitle" placeholder="Job title">
        <br>
        <strong>Company:</strong> <input v-model="company" placeholder="Company">
        <br />
        <strong>Start Date:</strong> <input v-model="startdate" placeholder="Start date">
        <br />
        <strong>End date:</strong> <input v-model="enddate" placeholder="End date">
        <br />
        <form>
          <input type="submit" value="Add new entry" @click="addMethod()"/>
        </form>
      </div>
    </div>
  </div>
</template>
<script>
import axios from 'axios'
export default{
  data () {
    return {
      ok: '',
      jobtitle: '',
      company: '',
      startdate: '',
      enddate: ''
    }
  },
  methods: {
    addEntryMethod () {
      this.ok = '1'
    },
    addMethod () {
      axios.post('https://safe-cliffs-38280.herokuapp.com/entry', {
        jobtitle: this.jobtitle,
        company: this.company,
        startdate: this.startdate,
        enddate: this.enddate
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
