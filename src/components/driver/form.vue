<template>
  <q-form ref="form" class="q-pa-md q-ma-md">
    {{ formData }}
    <div class="column">
      <q-input ref="inputref" v-model="formData.driver_name" mask="N" reverse-fill-mask label="Driver Name"
        :options="driver_name" :rules="[(val) => (val && val.length > 0) || 'Required Field']" />
      <q-input ref="inputref" v-model="formData.address" mask="S" label="Address" :options="address"
        :rules="[(val) => (val && val.length > 0) || 'Required Field']" />
      <q-input ref="inputref" v-model="formData.contact_no" mask="##########" label="Contact Number"
        :rules="[(val) => (val && val.length > 0) || 'Required Field']" />
      <q-select clearable v-model="formData.status" label="Status" :options="['Published', 'Draft', 'Archived']" />
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
  created() {
    this.fetchDriver();
  },
  methods: {
    async fetchDriver() {
      let response = await this.$api.get("items/driver");
      this.driver = response.data.data;
    },
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
