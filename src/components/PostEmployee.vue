<template>
  <div class="container mt-5">
    <h2 class="text-center mb-4">Add Employee</h2>

    <div class="row justify-content-center">
      <!-- 👇 Controls width -->
      <div class="col-md-6 col-lg-5">

        <form @submit.prevent="postEmp" class="card p-4 shadow-lg" style="background-color:lightblue;">

          <div class="mb-3">
            <label class="form-label fw-semibold fs-2">Name</label>
            <input 
              type="text" 
              class="form-control" 
              v-model="employee.name" 
              placeholder="Enter name"
              required 
            />
          </div>

          <div class="mb-3">
            <label class="form-label fw-semibold fs-2">Department</label>
            <input 
              type="text" 
              class="form-control" 
              v-model="employee.department" 
              placeholder="Enter department"
              required 
            />
          </div>

          <div class="mb-3">
            <label class="form-label fw-semibold fs-2">Designation</label>
            <input 
              type="text" 
              class="form-control" 
              v-model="employee.designation" 
              placeholder="Enter designation"
              required 
            />
          </div>

          <div class="mb-3">
            <label class="form-label fw-semibold fs-2">Salary</label>
            <input 
              type="number" 
              class="form-control" 
              v-model="employee.salary" 
              placeholder="Enter salary"
              required 
            />
          </div>

          <button class="btn btn-success w-100 mt-2">
             Add Employee
          </button>

        </form>

      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

const API = "https://69f050cb112e1b968e2586a8.mockapi.io/api/employees";

export default {
  name: "PostEmployee",

  data() {
    return {
      employee: {
        name: "",
        department: "",
        designation: "",
        salary: ""
      }
    };
  },

  methods: {
    postEmp() {
      axios.post(API, this.employee)
        .then(() => {
          alert("Employee added successfully");

          // reset form
          this.employee = {
            name: "",
            department: "",
            designation: "",
            salary: ""
          };
        })
        .catch(err => console.log(err));
    }
  }
};
</script>

<style>
.card {
  border-radius: 12px;
}

button {
  border-radius: 8px;
}
</style>