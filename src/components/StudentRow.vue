<template>
<!--  copied tr from StudentTable (remove v-for)-->
<!--  <tr v-for="student in students" v-bind:class=" { present: student.present, absent: !student.present } ">-->
  <tr v-bind:class=" { present: student.present, absent: !student.present } ">
    <td>{{ student.name }}</td>
    <td>{{ student.starID }}</td>
    <td>
      <input type="checkbox" v-bind="student.present" v-on:change="arrivedOrLeft(student, $event.srcElement.checked)">
      <!-- after one-way data binding (v-bind), then we need to emit a message to a parent (App.vue)**Head down to methodsVVV-->
    </td>
  </tr>
</template>

<script>
  export default {
    //name: 'after the name of the file', 'piece of data")
    name: 'StudentRow',
    emits: ['student-arrived-or-left'],
    props: {
      student: Object
    },
    methods: {
      arrivedOrLeft(student, present){
        this.$emit('student-arrived-or-left', student, present)
      }
    }
  }
</script>

<style scoped>
/*removed styles from StudentTable.vue and put them here:*/
.present {
  color:grey;
  font-style: italic;
}

.absent {
  color: black;
  font-weight: bold;
}

</style>