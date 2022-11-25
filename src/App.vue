<template>
  <div id="app">
    <new-student-form></new-student-form>
    <student-table></student-table>
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
//  after the set-up, HERE is where you add data:
  data() {
    return {
    wyrQuestion: 'Would you rather never have to take a bath/shower but still always smell nice or never have to get ' +
        'another shot but still be healthy?',
      wyrAnswer1: 'No bathing, but always smell nice.',
      wyrAnswer2: 'No shots, but still be healthy.',
      userSelectionMessage: ''
   //
    }
  },
  methods: {
    answerChanged(choice) {
      this.userSelectionMessage = `Thanks! You chose ${choice}`
    }
  }
}
</script>

<style>

</style>
