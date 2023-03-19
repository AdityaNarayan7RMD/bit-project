<template>
  <q-form ref="form" class="q-pa-md q-ma-md">
    {{ formData }}
    <div class="column">
      <q-select clearable v-model="formData.account_id" label="Account Id" :options="accounts" option-label="account_name"
        option-value="id" map-options emit-value />
      <q-input v-model="formData.invoice_number" label="Invoices Number" mask="S" reverse-fill-mask type="char"/>
      <q-input v-model="formData.invoice_date" type="date" stack-label label="Invoice Date"
      :rules="[(val) => (val && val.length > 0) || 'Required Field']" />
      <q-input v-model="formData.grand_total" label="Grand Total" />
      <q-select clearable v-model="formData.invoice_status" label="Invoices Status"
        :options="['Draft', 'Provisional', 'Final', 'Cancelled']" />
      <q-select v-model="formData.payment_status" label="Payment Status" :options="['Unpaid', 'Partially Paid', 'Paid']"
        :rules="[(val) => (val && val.length > 0) || 'Required Field']" />
      <q-select clearable v-model="formData.organisation_id" label="Organisation Id" :options="organisation"
        option-label="id" option-value="organisation_name" map-options emit-value />
      <q-input v-model="formData.invoice_details" label="Invoice Details" />
      <q-input v-model="formData.invoice_settlement" label="Invoice Settlement"/>
      <q-input v-model="formData.period" label="Period"/>
      <q-select v-model="formData.bank_id" label="Bank Id" :options="banks" option-label="id" option-value="bank_name"
        map_options emit-value />
      <q-input v-model="formData.booked_by" label="Booked By"/>
      <q-input v-model="formData.oncall_plan" label="Oncall Plan"/>
      <q-input v-model="formData.vehicle_no" label="Vehicle No" />
      <q-input v-model="formData.log_type" label="Log Type"/>
      <q-input v-model="formData.journey_date" label="Journey Date" type="date" stack-label
        :rules="[validationDateMandatory, validateDateFuture]" />
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
      organisation: [],
      banks: [],
    };
  },
  created() {
    this.fetchAccounts();
    this.fetchOrganisation();
    this.fetchBanks();
  },
  methods: {
    async fetchAccounts() {
      let response = await this.$api.get("items/accounts");
      this.accounts = response.data.data;
    },
    async fetchOrganisation() {
      let response = await this.$api.get("items/organisation");
      this.organisation = response.data.data;
    },
    async fetchBanks() {
      let response = await this.$api.get("items/banks");
      this.banks = response.data.data;
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
