<template>
  <div>
    <h2>Update Form Data</h2>
    <form @submit.prevent="updateForm">
      <label for="name">Name: </label>
      <input type="text" id="name" v-model="updatedFormData.name" />
      <br />

      <label for="rollNumber">Roll Number: </label>
      <input type="text" id="roll-num" v-model="updatedFormData.rollNumber" />

      <label for="email">Email: </label>
      <input type="text" id="email" v-model="updatedFormData.email" />

      <label for="gender">Gender: </label>
      <label for="male">
        <input
          type="radio"
          id="male"
          name="gender"
          value="male"
          v-model="updatedFormData.gender"
          required
        />
        Male
      </label>
      <label for="female">
        <input
          type="radio"
          id="female"
          name="gender"
          value="female"
          v-model="updatedFormData.gender"
          required
        />
        Female
      </label>

      <label for="hobbies">Hobbies: </label>
      <label for="reading">
        <input
          type="checkbox"
          name="hobbies"
          value="reading"
          id="reading"
          v-model="updatedFormData.hobbies"
        />
        Reading
      </label>
      <label for="running">
        <input
          type="checkbox"
          name="hobbies"
          value="running"
          id="running"
          v-model="updatedFormData.hobbies"
        />
        Running
      </label>
      <label for="travelling">
        <input
          type="checkbox"
          name="hobbies"
          value="travelling"
          id="travelling"
          v-model="updatedFormData.hobbies"
        />
        Travelling
      </label>
      <label for="playing">
        <input
          type="checkbox"
          name="hobbies"
          value="playing"
          id="playing"
          v-model="updatedFormData.hobbies"
        />
        Playing
      </label>

      <label for="marks">Marks:</label>
      <input type="number" id="marks" v-model="updatedFormData.marks" />

      <label for="phoneNumber">Phone Number: </label>
      <input
        type="number"
        id="phone-number"
        v-model="updatedFormData.phoneNumber"
      />

      <button type="submit">Update</button>
    </form>
  </div>
</template>

<script>
export default {
  props: ["formData"], //selectedFormData is sent as the props here!
  data() {
    return {
      updatedFormData: { ...this.formData },
    };
  },
  methods: {
    updateForm() {
      this.$emit("update-form-data", this.updatedFormData);
      this.updatedFormData = { ...this.formData }; //reset
    },
  },
};
</script>

<style scoped>
h2 {
  font-size: 1.2rem;
  margin-bottom: 1rem;
}

form {
  background-color: #f2f2f2;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

label {
  display: block;
  margin-bottom: 10px;
  font-family: cursive;
}

input[type="text"],
input[type="number"] {
  width: 100%;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  margin-bottom: 10px;
}

input[type="radio"],
input[type="checkbox"] {
  margin-right: 5px;
}

button[type="submit"] {
  margin-top: 10px;
  padding: 10px 20px;
  color: #4caf50;
  background-color: white;
  border: 1px solid #4caf50;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button[type="submit"]:hover {
  background-color: #45a049;
  color: white;
}
</style>
