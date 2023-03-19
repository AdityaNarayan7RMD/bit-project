<template>
  <q-form ref="form" class="q-pa-md q-ma-md">
    {{ formData }}
    <div class="column">
      <q-input v-model="formData.item_id" label="Item Id" />
      <q-input v-model="formData.rate" label="Rate" :rules="[(val) => (val && val.length > 0) || 'Required Field']" />
      <q-input ref="inputref" v-model="formData.quantity" label="Quantity"
        :rules="[(val) => (val && val.length > 0) || 'Required Field']" />
      <q-input v-model="formData.amount" label="Amount" :rules="[(val) => (val && val.length > 0) || 'Required Field']" />
      <q-input ref="inputref" v-model="formData.tax_rate" mask="#" reverse-fill-mask label="Tax Rate"
        :rules="[(val) => (val && val.length > 0) || 'Required Field']" />
      <q-input v-model="formData.tax_amount" label="Tax Amount"
        :rules="[(val) => (val && val.length > 0) || 'Required Field']" />
      <q-input v-model="formData.total_amount" label="Total amount"
        :rules="[(val) => (val && val.length > 0) || 'Required Field']" />
      <q-input v-model="formData.status" label="Status" :rules="[(val) => (val && val.length > 0) || 'Required Field']" />
      <q-input v-model="formData.invoice_id" label="Invoice Id"
        :rules="[(val) => (val && val.length > 0) || 'Required Field']" />
      <q-input v-model="formData.description" label="Description"
        :rules="[(val) => (val && val.length > 0) || 'Required Field']" />
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
        alert("invalid from");
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
-
