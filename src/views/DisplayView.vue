<script>
import FormDisplay from "../components/FormDisplay.vue";
import UpdateForm from "../components/UpdateForm.vue";
export default {
  data() {
    return {
      formDataSet: [],
      selectedFormData: null,
    };
  },

  components: {
    FormDisplay,
    UpdateForm,
  },

  methods: {
    addFormData(formData) {
      formData.id = Date.now();
      this.formDataSet.push(formData);
    },
    editFormData(formData) {
      this.selectedFormData = { ...formData };
    },
    updateFormData(updatedFormData) {
      const index = this.formDataSet.findIndex(
        (formData) => formData.id === updatedFormData.id
      );
      if (index !== -1) {
        this.formDataSet[index] = updatedFormData;
      }
      this.selectedFormData = null;
    },
    deleteFormData(formData) {
      const index = this.formDataSet.findIndex(
        (data) => data.id === formData.id
      );
      if (index !== -1) {
        this.formDataSet.splice(index, 1);
      }
    },
  },
};
</script>

<template>
  <div>
    <FormDisplay @form-data="addFormData" />
    <div v-if="formDataSet.length > 0">
      <table class="data-table">
        <tr>
          <th>Name</th>
          <th>Roll Number</th>
          <th>Email</th>
          <th>Gender</th>
          <th>Hobbies</th>
          <th>Grade:</th>
          <th>Phone number</th>
          <th>Update</th>
          <th>Delete</th>
        </tr>
        <tr v-for="formData in formDataSet" :key="formData.id">
          <td>{{ formData.name }}</td>
          <td>{{ formData.rollNumber }}</td>
          <td>{{ formData.email }}</td>
          <td>{{ formData.gender }}</td>
          <td>{{ formData.hobbies }}</td>
          <td>{{ $filters.gradeFilter(formData.marks) }}</td>
          <td>{{ formData.phoneNumber }}</td>
          <td><button @click="editFormData(formData)">Update</button></td>
          <td><button @click="deleteFormData(formData)">❌</button></td>
        </tr>
      </table>
    </div>
    <UpdateForm
      v-if="selectedFormData"
      :formData="selectedFormData"
      @update-form-data="updateFormData"
    />
  </div>
</template>

<style>
.data-table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 20px;
  font-family: cursive;
}

.data-table th,
.data-table td {
  border: 1px solid #ddd;
  padding: 8px;
}

.data-table th {
  background-color: #f2f2f2;
  font-weight: bold;
}

.data-table td {
  text-align: center;
}
</style>
