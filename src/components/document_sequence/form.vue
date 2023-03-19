<template>
  <q-form ref="form" class="q-pa-md q-ma-md">
    {{ formData }}
    <div class="column">
      <q-select v-model="formData.organisation_id" label="Organisation Id" :options="organisation"
        option-label="organisation_name" option-value="id" map-options emit-value />
      <q-select clearable v-model="formData.document_type" label="Document Type" :options="['invoices', 'receipt']"
        :rules="[(val) => (val && val.length > 0) || 'Required Field']" />
      <q-input clearable v-model="formData.sequence_no" label="Sequence No" mask="#" reverse-fill-mask
        :rules="[(val) => (val && val.length > 0) || 'Mandatory Field']" />
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
      organisation: [],
    };
  },
  created() {
    this.fetchOrganisation();
  },
  methods: {
    async fetchOrganisation() {
      let response = await this.$api.get("items/organisation");
      this.organisation = response.data.data;
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
