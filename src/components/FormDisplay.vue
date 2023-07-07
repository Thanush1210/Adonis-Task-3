<template>
  <form class="form-display" @submit.prevent="onSubmit">
    <label for="name">Name: </label>
    <input type="text" id="name" v-model="name" />
    <br />

    <label for="rollNumber">Roll Number: </label>
    <input type="text" pattern="[A-Za-z0-9]+" id="roll-num" v-model="rollNumber" />

    <label for="email">Email: </label>
    <input type="text" id="email" v-model="email" />

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
    <input type="number" id="marks" v-model="marks">

    <label for="phoneNumber">Phone Number: </label>
    <input type="number" id="phone-number" v-model="phoneNumber">

    <input type="submit" value="Submit" />
  </form>
</template>

<script>
import "@fortawesome/fontawesome-free/css/all.css";
export default {
  data() {
    return {
      name: "",
      rollNumber: "",
      email: "",
      gender: '',
      hobbies: [],
      marks:'',
      phoneNumber:null
    };
  },

  methods: {
    onSubmit() {
      if (
        this.name === "" ||
        this.rollNumber === "" ||
        this.email === "" ||
        this.gender === "" ||
        this.hobbies === ""
      ) {
        alert("Please fill out every field!");
        return;
      }

      this.$emit('form-data',{
        name: this.name,
        rollNumber: this.rollNumber,
        email: this.email,
        gender: this.gender,
        hobbies: this.hobbies,
        marks: this.marks,
        phoneNumber: this.phoneNumber
      })
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
.form-display {
  display: flex;
  flex-direction: column;
}
#name , #roll-num , #email{
    width: 50%;
}
</style>
