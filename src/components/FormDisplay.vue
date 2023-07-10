<template>
  <div class="form-container">
    <form class="form-display" @submit.prevent="onSubmit">
      <label for="name">Name: </label>
      <input type="text" id="name" v-model="name" />
      <br />

      <label for="rollNumber">Roll Number: </label>
      <input
        type="text"
        pattern="[A-Za-z0-9]+"
        id="roll-num"
        v-model="rollNumber"
      />

      <label for="email">Email: </label>
      <input type="email" id="email" v-model="email" />

      <label for="gender">Gender: </label>
      <label for="male">
        <input
          type="radio"
          id="male"
          name="gender"
          value="male"
          v-model="gender"
          required
        />
        <img
          src="./icons/icons8-male-50.png"
          alt="male"
          @click="gender = 'male'"
        />
      </label>
      <label for="female">
        <input
          type="radio"
          id="female"
          name="gender"
          value="female"
          v-model="gender"
          required
        />
        <img
          src="./icons/icons8-female-48.png"
          alt="female"
          @click="gender = 'female'"
        />
      </label>

      <label for="hobbies">Hobbies: </label>
      <label for="reading">
        <input
          type="checkbox"
          name="hobbies"
          value="reading"
          id="reading"
          @click="updateHobbies"
        />
        Reading
      </label>
      <label for="running">
        <input
          type="checkbox"
          name="hobbies"
          value="running"
          id="running"
          @click="updateHobbies"
        />
        Running
      </label>
      <label for="travelling">
        <input
          type="checkbox"
          name="hobbies"
          value="travelling"
          id="travelling"
          @click="updateHobbies"
        />
        Travelling
      </label>
      <label for="playing">
        <input
          type="checkbox"
          name="hobbies"
          value="playing"
          id="playing"
          @click="updateHobbies"
        />
        Playing
      </label>

      <label for="marks">Marks</label>
      <input type="number" id="marks" v-model="marks" />

      <label for="phoneNumber">Phone Number: </label>
      <input type="number" id="phone-number" v-model="phoneNumber" />

      <input type="submit" value="Submit" class="submit-button" />
    </form>
  </div>
</template>

<script>
import "@fortawesome/fontawesome-free/css/all.css";
export default {
  data() {
    return {
      name: "",
      rollNumber: "",
      email: "",
      gender: "",
      hobbies: [],
      marks: "",
      phoneNumber: null,
    };
  },

  methods: {
    onSubmit() {
      if (
        this.name === "" ||
        this.rollNumber === "" ||
        this.email === "" ||
        this.gender === "" ||
        this.hobbies === "" ||
        this.marks.toString().length > 3 ||
        this.marks > 100 ||
        this.phoneNumber.toString().length !== 10
      ) {
        alert("Enter valid details!");
        return;
      }

      this.$emit("form-data", {
        name: this.name,
        rollNumber: this.rollNumber,
        email: this.email,
        gender: this.gender,
        hobbies: this.hobbies,
        marks: this.marks,
        phoneNumber: this.phoneNumber,
      });

      this.reset();
    },
    reset() {
      this.name = "";
      this.rollNumber = "";
      this.email = "";
      this.gender = "";
      this.hobbies = null;
      this.marks = "";
      this.phoneNumber = "";
    },
    updateHobbies(event) {
      const hobbyValue = event.target.value;

      if (event.target.checked) {
        this.hobbies.push(hobbyValue);
      } else {
        const index = this.hobbies.indexOf(hobbyValue);
        if (index !== -1) {
          this.hobbies.splice(index, 1);
        }
      }
    },
  },
};
</script>

<style>
.form-container {
  max-width: 500px;
  margin: 0 auto;
}

.form-display {
  background-color: #f2f2f2;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.form-display label {
  display: block;
  margin-bottom: 10px;
  font-family: cursive;
}

.form-display input[type="text"],
.form-display input[type="number"],
.form-display input[type="email"] {
  width: 100%;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  margin-bottom: 10px;
}

.form-display input[type="radio"],
.form-display input[type="checkbox"] {
  margin-right: 5px;
}

.form-display .submit-button {
  margin-top: 10px;
  padding: 10px 20px;
  border: 1px solid #4caf50;
  border-radius: 4px;
  cursor: pointer;
  color: #4caf50;
  background-color: white;
}

.form-display .submit-button:hover {
  background-color: #45a049;
  color: white;
}
</style>
