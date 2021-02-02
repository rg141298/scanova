<template>
  <v-app>
    <v-stepper v-model="e1">
      <v-stepper-header>
        <v-stepper-step :complete="e1 > 1" step="1">
          Name of step 1
        </v-stepper-step>

        <v-divider></v-divider>

        <v-stepper-step :complete="e1 > 2" step="2">
          Name of step 2
        </v-stepper-step>
      </v-stepper-header>

      <v-stepper-items>
        <v-stepper-content step="1">
          <v-form>
            <v-container>
              <v-row>
                <v-col cols="12" md="4">
                  <v-text-field
                    v-model="name"
                    :rules="nameRules"
                    :counter="30"
                    label="Name"
                    required
                  ></v-text-field>
                </v-col>

                <v-col cols="12" md="4">
                  <v-text-field
                    v-model="password"
                    type="password"
                    label="Password"
                    required
                  ></v-text-field>
                </v-col>

                <v-col cols="12" md="4">
                  <v-text-field
                    v-model="confirmPassword"
                    type="password"
                    label="Confirm Password"
                    required
                  ></v-text-field>
                </v-col>

                <v-col>
                  <v-btn @click="submitStepOne()">
                    Continue
                  </v-btn>
                </v-col>
              </v-row>
            </v-container>
          </v-form>
        </v-stepper-content>

        <v-stepper-content step="2">
          <v-form>
            <v-container>
              <v-row>
                <v-col class="d-flex" cols="12">
                  <v-select
                    v-model="ageGroup"
                    :items="ageGroups"
                    label="Age Group"
                    dense
                  ></v-select>
                </v-col>
                <v-col cols="12">
                  <v-text-field
                    v-model="age"
                    type="number"
                    label="Enter Age"
                    required
                  ></v-text-field>
                </v-col>

                <v-col cols="12">
                  <v-text-field
                    v-model="hours"
                    type="number"
                    label="Enter hours in week"
                    required
                  ></v-text-field>
                </v-col>
                <v-col cols="12">
                  <v-textarea v-model="movies" label="Movies"></v-textarea>
                </v-col>

                <v-col>
                  <v-btn @click="submitStepTwo()">
                    Submit
                  </v-btn>
                  <v-btn text @click="cancelStepTwo()">
                    Cancel
                  </v-btn>
                </v-col>
              </v-row>
            </v-container>
          </v-form>
        </v-stepper-content>
      </v-stepper-items>
    </v-stepper>
  </v-app>
</template>

<script>
export default {
  data: () => ({
    e1: 1,
    valid: false,
    name: "",
    password: "",
    confirmPassword: "",
    nameRules: [
      (v) => !!v || "Name is required",
      (v) => v.length <= 30 || "Name must be less than 30 characters",
    ],
    age: "",
    hours: "",
    ageGroup: null,
    ageGroups: ["Child", "Teen", "Adult", "Old aged"],
    movies: "",
    data: [],
  }),
  methods: {
    submitStepOne() {
      if (this.name !== "") {
        if (this.password === this.confirmPassword && this.password !== "") {
          if (this.password.length >= 8 && this.password.length <= 20) {
            this.e1 = 2;
          } else {
            alert("Password Length should be between 8 to 20 character");
            this.password = "";
            this.confirmPassword = "";
          }
        } else {
          alert("Check the passwords");
          this.password = "";
          this.confirmPassword = "";
        }
      } else alert("Name is mandatory");
    },
    submitStepTwo() {
      if (this.ageGroup !== "") {
        if (this.ageGroup === "Child") {
          if (this.age !== "" && this.age > 5 && this.age < 13) {
            if (this.hours !== "") {
              if (this.hours >= 0 && this.hours <= 168) {
                if (this.movies !== "") {
                  this.submitData();
                } else alert("Movies field cannot be empty");
              } else {
                alert("Hours should be between 0 and 168");
                this.hours = "";
              }
            } else {
              alert("Enter Number of hours");
              this.hours = "";
            }
          } else {
            alert("Child Age should be between 6 to 12 ");
            this.age = "";
          }
        } else if (this.ageGroup === "Teen") {
          if (this.age !== "" && this.age > 12 && this.age < 20) {
            if (this.hours !== "") {
              if (this.hours >= 0 && this.hours <= 168) {
                if (this.movies !== "") {
                  this.submitData();
                } else alert("Movies field cannot be empty");
              } else {
                alert("Hours should be between 0 and 168");
                this.hours = "";
              }
            } else {
              alert("Enter Number of hours");
              this.hours = "";
            }
          } else alert("Teen age should be between 13 to 19");
        } else if (this.ageGroup === "Adult") {
          if (this.age !== "" && this.age > 19 && this.age < 51) {
            if (this.hours !== "") {
              if (this.hours >= 0 && this.hours <= 168) {
                if (this.movies !== "") {
                  this.submitData();
                } else alert("Movies field cannot be empty");
              } else {
                alert("Hours should be between 0 and 168");
                this.hours = "";
              }
            } else {
              alert("Enter Number of hours");
              this.hours = "";
            }
          } else alert("Adult age should be between 20 to 50");
        } else if (this.ageGroup === "Old aged") {
          if (this.age !== "" && this.age > 50) {
            if (this.hours !== "") {
              if (this.hours >= 0 && this.hours <= 168) {
                if (this.movies !== "") {
                  this.submitData();
                } else alert("Movies field cannot be empty");
              } else {
                alert("Hours should be between 0 and 168");
                this.hours = "";
              }
            } else {
              alert("Enter Number of hours");
              this.hours = "";
            }
          } else alert("Old aged person is older than 50 ");
        } else alert("Select Age Group");
      } else {
        alert("Age Group is mandatory");
      }
    },
    cancelStepTwo() {
      this.e1 = 1;
      this.ageGroup = null;
      this.age = "";
      this.hours = "";
    },
    submitData() {
      let tempData = {
        userName: "",
        ageGroup: "",
        age: "",
        hours: "",
        movies: [],
      };
      alert("Data Submitted");
      tempData.userName = this.name;
      tempData.ageGroup = this.ageGroup;
      tempData.age = this.age;
      tempData.hours = this.hours;
      tempData.movies.push(this.movies.split(","));

      this.data.push(tempData);
      console.log("Data of User::::", tempData);
      console.log("Total Data:::::", this.data);
      this.e1 = 1;
      this.clearForms();
    },
    clearForms() {
      this.name = "";
      this.password = "";
      this.confirmPassword = "";
      this.ageGroup = "";
      this.age = "";
      this.hours = "";
      this.movies = "";
    },
  },
};
</script>

<style></style>
