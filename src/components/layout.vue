<template>
  <q-layout>
    <div slot="header" class="toolbar">
      <q-toolbar-title :padding="1">
        PortfolioMaker
      </q-toolbar-title>
      <button @click="drawerOpen()">
        <i>assignment</i>
      </button>
    </div>

    <q-tabs slot="navigation">
      <q-tab icon="view_day" route="/showcase/basicinfo" exact replace>Basic Information</q-tab>
      <q-tab icon="view_day" route="/showcase/workexperience" replace>Work Experience</q-tab>
      <q-tab icon="view_day" route="/showcase/skills" replace>Skills</q-tab>
      <q-tab icon="view_day" route="/showcase/education" replace>Education</q-tab>
    </q-tabs>

    <router-view class="layout-view"></router-view>


    <q-drawer right-side swipe-only ref="rightDrawer">
      <div class="toolbar light">
        <q-toolbar-title :padding="1">
            Resume
        </q-toolbar-title>
      </div>

      <div v-html="res">

      </div>
    </q-drawer>

    <div slot="footer" class="toolbar">
      <div class="auto flex justify-center within-iframe-hide">
        <button v-go-back="'/showcase'">
          <i class="on-left animate-blink">
            replay
          </i>
          Back to Showcase
        </button>
      </div>
      <q-toolbar-title :padding="0" class="within-iframe-only">
        Footer
      </q-toolbar-title>
    </div>
  </q-layout>
</template>

<script>
import axios from 'axios'
var temp
export default {
  data () {
    return {
      search: '',
      res: ''
    }
  },
  methods: {
    drawerOpen () {
      temp = this
      this.$refs.rightDrawer.open()
      axios.get('https://safe-cliffs-38280.herokuapp.com/resume')
      .then(function (response) {
        console.log(response)
        temp.res = response.data
      })
      .catch(function (error) {
        console.log(error)
      })
      axios.post('http://api.html2pdfrocket.com/pdf?value=http://http://localhost:9000/#/&apikey=45499f30-b524-45cc-9ac9-03bdf6d5dd88', {

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
