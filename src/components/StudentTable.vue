<template>
  <div>
<!--    copied and pasted the table from vue-week-2-starter-student_sign_in.html-->
    <div class="card student-list m-2 p-2">
      <h4 class="card-title">Student List</h4>
      <div id="student-table">
        <table class="table">
          <tr>
            <th>Name</th>
            <th>StarID</th>
            <th>Present?</th>
          </tr>
          <tr v-for="student in students" v-bind:class=" { present: student.present, absent: !student.present } ">
            <td>{{ student.name }}</td>
            <td>{{ student.starID }}</td>
<!--            <td> <input type="checkbox" v-model="student.present" v-on:change="arrivedOrLeft(student)"></td>-->
<!--            remove v-model (used in the input in StudentTable)
                **v-model has 2 way data binding, if the checkbox changes, then whatever is v-modeled also changes  :-->
<!--            *change v-model to v-bind (to bind the checked property of a checkbox to student.present.  -->
            <td> <input type="checkbox" v-bind="student.present" v-on:change="arrivedOrLeft(student)"></td>
<!--            vid 5 stalled out at 12:00-->
          </tr>
        </table>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  //create the component here:
  //whatever is created here "export" will be available to another
  //  javascript will read this file and "export default" means whatever is created
  //  here will be available to that other file.
  name: 'StudentTable', //student table is NOT in charge of getting a list of students or creating a list,
  //App.vue will manage the list (the array of students) and will provide that data to student table using a prop.
  //StudentTable's job will be to display that list of students in a table.
  props: {
    //this will be the type of data, which is an array.
    students: Array
  },
  //  add the arrivedOrLeft method
  methods: {
    arrivedOrLeft() {
    //  what should happen when a box is checked or unchecked? Should studentTable deal with it? NO!!
    //  studentTable's parent (App.vue) will deal with it
    //  TODO emit message to parent.
    }
  }
}
</script>

<style scoped>
/*scoped means these component styles will only apply here, not on other components. */
.present {
  color:grey;
  font-style: italic;
}

.absent {
  color: black;
  font-weight: bold;
}

</style>