<template>
  <div class="container mt-4">
    <h2 class="text-center mb-4">Delete Employee</h2>

    <div class="table-responsive">
      <table class="table table-bordered table-hover">
        <thead class="table-danger">
          <tr>
            <th>Name</th>
            <th>Department</th>
            <th>Designation</th>
            <th>Salary</th>
            <th>Action</th>
          </tr>
        </thead>

        <tbody>
          <tr v-for="emp in employees" :key="emp.id">
            <td>{{ emp.name }}</td>
            <td>{{ emp.department }}</td>
            <td>{{ emp.designation }}</td>
            <td>₹ {{ emp.salary }}</td>
            <td>
              <button class="btn btn-danger btn-sm" @click="deleteEmp(emp.id)">
                Delete
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import axios from "axios";

const API = "https://69f050cb112e1b968e2586a8.mockapi.io/api/employees";

export default {
  name: "DeleteEmployee",

  data() {
    return {
      employees: []
    };
  },

  mounted() {
    this.getEmployees();
  },

  methods: {
    getEmployees() {
      axios.get(API)
        .then(res => {
          this.employees = res.data;
        })
        .catch(err => console.log(err));
    },

    deleteEmp(id) {
      axios.delete(`${API}/${id}`)
        .then(() => {
          alert("Employee deleted successfully");
          this.getEmployees();
        })
        .catch(err => console.log(err));
    }
  }
};
</script>