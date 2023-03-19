<template>
  <q-form ref="form" class="q-pa-md q-ma-md">
    {{ formData }}
    <div class="column">
      <q-input v-model="formData.id" label="Id" />
      <q-input v-model="formData.organisation_name" label="Organisation Name"
        :rules="[(val) => (val && val.length > 0) || 'Required Field']" />
      <q-input v-model="formData.prefix" label="Prefix" />
      <q-input v-model="formData.invoice_date" label="Invoice Date" />
      <q-input v-model="formData.description" label="Description" />
      <q-input v-model="formData.invoice_address" label="Address" />
      <q-input v-model="formData.payment_state" label="State" />
      <q-input v-model="formData.city" label="City" />
      <q-input v-model="formData.country" label="Country" />
      <q-input v-model="formData.pincode" label="Pincode" mask="######" />
      <q-input v-model="formData.contact_number" label="Contact Number" mask="(###-####-###)" />
      <q-input v-model="formData.email" label="Email" />
      <q-input v-model="formData.gst_number" label="Gst Number" />
      <q-input v-model="formData.pan_no" label="Pan No" />
      <q-input v-model="formData.invoices" label="Invoices" />
      <q-input v-model="formData.status" label="Status" />
      <q-select v-model="formData.banks" label="Banks" />
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
        alert("Invalid Form");
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
