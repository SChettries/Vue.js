
<template>
    <div class="container">
    <div class="card">
        <div class="card-header">
            <h4>
                Students
                <RouterLink to="/student/create" class="btn btn-primary float-end"> 
                    Add Students
                </RouterLink>
            </h4>
        </div>
        <div class="card-body">

            <table class="table table-bordered">
                <thead>
                <tr>
                    <th>ID</th>
                    <th>Name</th>
                    <th>Course</th>
                    <th>Email</th>
                    <th>Phone</th>
                    <th>Created At</th>
                    <th>Action</th>

                </tr>
                </thead>
                <tbody v-if="this.students.length > 0">
                    <tr v-for="(student, index) in this.students" :key="index">
                        <tr>{{ student.id }}</tr>
                        <tr>{{ student.name }}</tr>
                        <tr>{{ student.cousrse }}</tr>
                        <tr>{{ student.email }}</tr>
                        <tr>{{ student.phone }}</tr>
                        <tr>{{ student.created_at }}</tr>
                        <td>
                            <RouterLink to="/" class="btn btn-success"> 
                    Add Students 
                </RouterLink>
                        <button type="button" class="btn btn-danger">
                            Delete
                        </button>
                        </td>
                    </tr>
                </tbody v-else>
                <tr>
                    <td colspan="7">Loading...</td>
                </tr>
            </table>
        </div>
    </div>
</div>
  </template>

  <script>
  import axios from 'axios'
  export default {
    name: 'students',
    data(){
        return {
            students: []
        }
    },
    mounted(){
        this.getStudents();
      //   console.log('I am here.')
    },
    methods: {
        getStudents(){
            axios.get('file:///Applications/XAMPP/xamppfiles/htdocs/Vue.js/src/api/students.json').then(response => {
                this.students = res.data.students
                console.log(this.students)
            });
        }
    }
  }
</script>
