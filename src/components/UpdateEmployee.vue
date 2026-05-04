<template>
  <div class="container mt-4">
    <h2 class="text-center mb-4">Update Employee</h2>

    <div class="table-responsive">
      <table class="table table-bordered table-hover">
        <thead class="table-warning">
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
              <button class="btn btn-primary btn-sm" @click="editEmp(emp)">
                Edit
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>

    <!-- Edit Form -->
    <div v-if="editData.id" class="card p-4 mt-4 shadow">
      <h4>Edit Employee</h4>

      <input class="form-control mb-2" v-model="editData.name" placeholder="Name" />
      <input class="form-control mb-2" v-model="editData.department" placeholder="Department" />
      <input class="form-control mb-2" v-model="editData.designation" placeholder="Designation" />
      <input class="form-control mb-2" type="number" v-model="editData.salary" placeholder="Salary" />

      <button class="btn btn-warning w-100" @click="updateEmp">
        Update Employee
      </button>
    </div>
  </div>
</template>

<script>
import axios from "axios";

const API = "https://69f050cb112e1b968e2586a8.mockapi.io/api/employees";

export default {
  name: "UpdateEmployee",

  data() {
    return {
      employees: [],
      editData: {
        id: null,
        name: "",
        department: "",
        designation: "",
        salary: ""
      }
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

    editEmp(emp) {
      this.editData = { ...emp };
    },

    updateEmp() {
      axios.put(`${API}/${this.editData.id}`, this.editData)
        .then(() => {
          alert("Employee updated successfully");
          this.getEmployees();

          this.editData = {
            id: null,
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