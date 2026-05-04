<template>
  <PostEmployee/>
  <EmployeeList/>
  <UpdateEmployee/>
  <DeleteEmployee/>
  <NavBar/>
</template>

<script>
import DeleteEmployee from './components/DeleteEmployee.vue';
import EmployeeList from './components/EmployeeList.vue';
import PostEmployee from './components/PostEmployee.vue';
import UpdateEmployee from './components/UpdateEmployee.vue';


export default {
  name: 'App',
  components: {
    PostEmployee,
    EmployeeList,
    UpdateEmployee,
    DeleteEmployee
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
