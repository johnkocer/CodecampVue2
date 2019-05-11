<template>
  <div class="hello">
    <br>Find Employee by Name:
    <input type="text" v-model="findEmployee.name">
    <button class="btn btn-sm btn-primary ml-1" v-on:click="searchEmployeesByName()">Search</button>
    <table class="table table-striped table-hover table-sm small table-bordered">
      <thead class="thead-light">
        <tr>
          <th>Id</th>
          <th>Name</th>
          <th>Gender</th>
          <th>Salary</th>
          <th>DepartmentId</th>
          <th></th>
          <th></th>
        </tr>
        <tr>
          <th></th>
          <th>
            <input id="newName" v-model="newEmployee.name" type="text" placeholder="newName">
          </th>
          <th>
            <input type="text" v-model="newEmployee.gender" placeholder="newGender">
          </th>
          <th>
            <input type="text" v-model="newEmployee.salary" placeholder="newSalary">
          </th>
          <th>
            <input type="text" v-model="newEmployee.departmentId" placeholder="newdepartmentId">
          </th>
          <th>
            <button class="btn btn-sm btn-primary" v-on:click="addEmployee(newEmployee)">Add</button>
          </th>
          <th></th>
        </tr>
      </thead>
      <tbody v-bind:key="item.id" v-for="item in employees">
        <tr>
          <td>{{item.id}}</td>
          <td>
            <input type="text" v-model="item.name">
          </td>
          <td>
            <input type="text" v-model="item.gender">
          </td>
          <td>
            <input type="text" v-model="item.salary">
          </td>
          <td>
            <input type="text" v-model="item.departmentId">
          </td>
          <td>
            <button class="btn btn-sm btn-primary" v-on:click="updateEmployee(item)">Update</button>
          </td>
          <td>
            <button class="btn btn-sm btn-primary" v-on:click="deleteEmployee(item)">Remove</button>
          </td>
        </tr>
      </tbody>
    </table>
    <br>Find Employee Id:
    <input type="text" v-model="findEmployee.id">
    <button class="btn btn-sm btn-primary ml-1" v-on:click="searchEmployeesById()">Search</button>
    <br>
    {{findEmployee}}
    <hr>
  </div>
</template>

<script>
/* eslint-disable */
import { EmployeeService } from "../service/employee.service";

export default {
  name: "EmployeeComponent",
  props: {
    msg: String
  },
  data() {
    return {
      name: "John",
      employees: [],
      showEditor: true,
      myName: "",
      newEmployee: { id: 0, name: "", gender: "", salary: 0, departmentId: 1 },
      findEmployee: { id: 0, name: "", gender: "", salary: 0, departmentId: 1 }
    };
  },
  mounted() {
    console.log("in Mounted");
    this.getEmployees();
  },
  methods: {
    getEmployees() {
      EmployeeService.get()
        .then(res => {
          this.employees = res.data;
        })
        .catch(error => {
          console.log("There is an error in getEmployees API call." + error);
        });
    },

    addEmployee(item) {
      EmployeeService.post(this.newEmployee)
        .then(res => {
          console.dir(res.data);
          this.getEmployees();
        })
        .catch(error => {
          console.log("There is an error in Post API call." + error);
        });
    },

    searchEmployeesByName(e) {
      console.log("In searchEmployees");
      EmployeeService.searchEmployees(this.findEmployee.name)
        .then(res => {
          console.log("In searchEmployees");
          console.dirxml(res.data);

          this.employees = res.data;
        })
        .catch(error => {
          console.log("There is an error in Get API call." + error);
        });
    },

    searchEmployeesById(e) {
      console.log("In searchEmployeesById");
      EmployeeService.getEmployee(this.findEmployee.id)
        .then(res => {
          console.dirxml(res.data);

          this.findEmployee = res.data;
        })
        .catch(error => {
          console.log("There is an error in Get API call." + error);
          this.setState({ employee: null });
        });
    },

    updateEmployee(row) {
      console.dirxml(row);
      let findEmployee = this.employees.find(t => t.id === row.id);
      if (findEmployee) {
        EmployeeService.put(findEmployee)
          .then(res => {
            const todoRes = res.data;
            console.dir(todoRes);
            this.getEmployees();
          })
          .catch(error => {
            console.log("There is an error in Put API call." + error);
          });
      }
      console.dirxml(findEmployee);
    },

    deleteEmployee(row) {
      console.dirxml(row);
      EmployeeService.delete(row)
        .then(res => {
          this.getEmployees();
        })
        .catch(error => {
          console.log("There is an error in Put API call." + error);
        });
    }
  } // methods
};
</script>
