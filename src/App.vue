<template>
  <div id="app">
<!--    vvv came from $emit in NewStudentForm, use the name used in this string
        in NewStudentForm (this.$emit('student-added', student)-->
<!--    when the v-on:student-added happens, call a method in app.vue called-->
    <new-student-form v-on:student-added="newStudentAdded"> </new-student-form>
<!--    in order to get the data to show up on the webpage, you have to get the app.vue (parent)
        to connect the StudentTable's prop (students) has to be provided by the parent of
         StudentTable(App.vue) using v-bind.vvv
        (name of prop and the data are the same here, but they don't have to be.-->
    <student-table v-bind:students="students"> </student-table>
    <student-message></student-message>

 </div>
</template>

<script>
import NewStudentForm from './components/NewStudentForm.vue'
import StudentMessage from './components/StudentMessage.vue'
import StudentTable from './components/StudentTable.vue'

export default {
  name: 'App',
  components: {
    NewStudentForm,
    StudentMessage,
    StudentTable
  },
  //needs to be a function that returns an object:, will use the data from newStudentAdded above:
  data() {
    return {
      //empty array to start with vvv:
      students: []
    }
  },
  //then add a method to be called when the message is emited from New Student Form, added to app.vue above,
  //and then the array students: [] will have something in it.
  methods: {
    newStudentAdded(student) {
      //this will push the data to the array
      this.students.push(student)
    // sort the students:vv
      this.students.sort(function(s1, s2) {
        // return minus or plus one depending on the order of the newly added student name
        //( ? -1 : 1 )
        return s1.name.toLowerCase() < s2.name.toLowerCase() ? -1 : 1
      })
    }
  }
}
</script>

<style>
/*to apply styles from bootstrap to the whole page, go here: https://getbootstrap.com/docs/4.6/getting-started/introduction/
snag the href from the css listed:
This will import all the bootstrap styles, so it looks a lot like the original student sign in page we made.
Import Boostrap into App.vue using the CSS @import rule
https://www.w3schools.com/cssref/pr_import_rule.asp

*/

@import "https://cdn.jsdelivr.net/npm/bootstrap@4.6.2/dist/css/bootstrap.min.css";

</style>
