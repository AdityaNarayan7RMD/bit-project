<template>
  <q-form ref="form" class="q-pa-md q-ma-md">
    {{ formData }}
    <div class="column">
      <q-input v-model="formData.id" label="Id" />
      <q-select v-model="formData.account_id" label="Account Id" :options="accounts" option-label="account_name"
        option-value="id" map-options emit-value />
      <q-input v-model="formData.contact_id" label="Contact Id" />
      <q-input v-model="formData.vehicle_id" label="Vehicle Id" />
      <q-input v-model="formData.driver_id" label="Driver Id" />
      <q-input v-model="formData.contract_id" label="Contract Id" />
      <q-select v-model="formData.contact_id" label="Log Type" :options="['monthly', 'oncall']" />
      <q-input v-model="formData.date_from" label="Date From" type="date" stack-label />
      <q-input v-model="formData.date_to" label="Date To" type="date" stack-label />
      <q-input v-model="formData.rent" label="Rent" />
      <q-input v-model="formData.initial_reading" label="Initial Reading" />
      <q-input v-model="formData.final_reading" label="Final Reading" />
      <q-input v-model="formData.running_kms" label="Running Kms" />
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
      accounts: [],
    };
  },
  created() {
    this.fecthAccounts();
  },
  methods: {
    async fetchAccounts() {
      let response;
    },
    async submitData() {
      let validation = await this.$api.form.validate();
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
