<template>
  <div>
    <form>
      <input type="submit" value="Add new entry" @click="addEducationEntry()"/>
    </form>
    <div v-if="isok === '1'">
      <div class="layout-padding">
        <strong>Course Name:</strong> <input v-model="coursename" placeholder="Course">
        <br>
        <strong>Institute:</strong> <input v-model="institute" placeholder="institute">
        <br />
        <strong>Start Date:</strong> <input v-model="startdate" placeholder="Start date">
        <br />
        <strong>End date:</strong> <input v-model="enddate" placeholder="End date">
        <br />
        <form>
          <input type="submit" value="Add new entry" @click="addEntry()"/>
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
      isok: '',
      coursename: '',
      institute: '',
      startdate: '',
      enddate: ''
    }
  },
  methods: {
    addEducationEntry () {
      this.isok = '1'
    },
    addEntry () {
      axios.post('https://safe-cliffs-38280.herokuapp.com/education', {
        coursename: this.coursename,
        institute: this.institute,
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
}</script>
