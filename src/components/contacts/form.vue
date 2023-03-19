<template>
  <q-form ref="form" class="q-pa-md q-ma-md">
    {{ formData }}
    <div class="column">
      <q-input v-model="formData.account_id" label="Account Id" mask="S" reverse-fill-mask
        :rules="[(val) => (val && val.length > 0) || 'Required Field']" />
      <q-input v-model="formData.designation" label="Designation" mask="S" reverse-fill-mask type="char"
        :rules="[(val) => (val && val.length > 0) || 'Required Field']" />
      <q-input v-model="formData.name" label="Name" mask="S" reverse-fill-mask
       :rules="[(val) => (val && val.length > 0) || 'Required Field']" />
      <q-select v-model="formData.status" label="Status" :options="['published', 'draft', 'archived']"
       :rules="[(val) => (val && val.length > 0) || 'Required Field']" />
      <q-input v-model="formData.sort" label="Sort"/>
    </div>
    <div class="q-py-md">
      <q-btn color="red" label="submit" @click="submitData"></q-btn>
    </div>
    <div class="q-py-md">
      <q-btn color="red" label="close" to="./"></q-btn>
    </div>
  </q-form>
</template>
<script>
export default {
  data() {
    return {
      formData: {},
    };
  },
  methods: {
    async submitData() {
      let validation = await this.$refs.form.validate();
      if (!validation) {
        alert("invalid form");
        return;
      }
      console.log("Emitting Event of submitting form with data");
      alert();
      this.$emit("formSubmit", this.formData);
      console.log("Resetting Form");
      alert();
      this.formData = {};
    },
  },
};
</script>
