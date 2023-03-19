<template>
  <q-form ref="form" class="q-pa-md q-ma-md">
    {{ formData }}
    <div class="column">
      <q-input clearable v-model="formData.vehicle_no" label="Vehicle No" mask="S" reverse-fill-mask type="char"
        :rules="[(val) => (val && val.length > 0) || 'Required Field']" />
      <q-select v-model="formData.vehicle_type" label="Vehicle Type" :options="vehicle_type" option-label="id"
        option-value="id" map-options emit-value />
      <q-input v-model="formData.status" label="Status" :options="['published', 'draft', 'archived']"
        option-label="Standard" />
      <q-input v-model="formData.sort" label="Sort" />
      <q-input v-model="formData.fuel_avg" label="Fuel Avg" />
      <q-select v-model="formData.log_book" label="Log Book" :options="log_book" option-label="vehicle_id"
        option-value="vehicle_id" map-options emit-value />
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
      vehicle_type: [],
      log_book: [],
    };
  },
  created() {
    this.fetchVehicle();
    this.fetchLogBook();
  },
  methods: {
    async fetchVehicle() {
      let response = await this.$api.get("items/vehicle_type");
      this.vehicle_type = response.data.data;
    },
    async fetchLogBook() {
      let response = await this.$api.get("items/log_book");
      this.log_book = response.data.data;
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
