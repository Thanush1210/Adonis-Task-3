<script>
import FormDisplay from "../components/FormDisplay.vue";
export default {
  data(){
    return{
        formDataSet: []
    }
  },

  components: {
    FormDisplay,
  },

  methods: {
    addFormData(formData){
        formData.id = Date.now();
        this.formDataSet.push(formData);
    }

  },
 
};
</script>

<template>
  <div>
    <FormDisplay @form-data="addFormData"/>
    <div v-if="formDataSet.length > 0" >
        <table>
            <tr>
                <th>Name</th>
                <th>Roll Number</th>
                <th>Email</th>
                <th>Gender</th>
                <th>Hobbies</th>
                <th>Marks</th>
                <th>Phone number</th>
            </tr>
            <tr v-for="formData in formDataSet" :key="formData.id">
                <td>{{ formData.name }}</td>
                <td>{{ formData.rollNumber }}</td>
                <td>{{ formData.email }}</td>
                <td>{{ formData.gender }}</td>
                <td>{{ formData.hobbies }}</td>
                <td>{{ formData.marks }}</td>
                <td>{{ formData.phoneNumber }}</td>
            </tr>
        </table>
    </div>
  </div>
</template>

<style>
table , th , td{
    border: 1px solid black;
    border-collapse: collapse;
}
</style>
