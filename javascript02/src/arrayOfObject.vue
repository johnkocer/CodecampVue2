<template>
  <div id="app">
    <h3>ArrayOfObject</h3>
    {{this.myClasses()}}
  </div>
</template>

<script>
/* eslint-disable */

export default {
  name: "ArrayOfObject",

  methods: {
    myClasses() {
      // create a Class with consructor
      class Student {
        // properties (public by default)
        constructor() {
          this.id = 1;
          this.name = "Jen";
        }
      };
      let myStudent = new Student();
      console.log(myStudent);
      // Student {id: 1, name: "Jen"}

      class StudentA {
        // properties (public by default)
        // constructor with default values
        constructor(id = 2, name = "Nancy") {
          this.id = id;
          this.name = name;
        }
      }

      let myStudentA = new StudentA();
      console.log(myStudentA);
      // StudentA {id: 2, name: "Nancy"}

      let myStudentB = new StudentA(5, "James");
      console.log(myStudentB);
      // StudentA {id: 5, name: "James"}

      myStudentB.id = 6;
      myStudentB.name = "Harry";
      console.log(myStudentB);
      // StudentA {id: 6, name: "Harry"}

      // create a Class with properties that have default values
      class Car {
        id = 1;
        name = "Ford";
      }

      let myCar = new Car();
      console.log(myCar);
      // Car {id: 1, name: "Ford"}

      // create a Class with properties that have NO default values
      class Pet {
        id; // default value is undefained
        name; // default value is undefained
      }

      let myPet = new Pet();
      console.log(myPet);
      // Pet {}
      console.log(myPet.name, myPet.id);
      // undefined, undefined

      class CarB {
        id;
        name;
        constructor(id, name) {
          this.id = id;
          this.name = name;
        }
        setId(value) {
          this.id = value;
        }
        // getter
        getId() {
          return this.id;
        }
        // setter
        setName(value) {
          this.name = value;
        }

        getName() {
          return this.name;
        }
        // function
        start(gear) {
          console.log("Car started with gear: " + gear);
        }
      }

      let carB = new CarB(0, "");
      carB.setId(2);
      carB.setName("Toyota");

      console.log(`Id: ${carB.getId()} Name: ${carB.getName()}`);
      // Id: 2 Name: Toyota
    }
  }
};
</script>