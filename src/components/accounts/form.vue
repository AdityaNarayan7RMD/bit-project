<template>
  <q-form ref="form" class="q-pa-md q-ma-md">
    {{ formData }}
    <div class="column">
      <q-input ref="inputref" v-model="formData.account_name" mask="S" reverse-fill-mask label="Account Name*"
       :rules="[val => !!val || 'Name is required']" />
      <q-input v-model="formData.account_address" label="Account Address*" type="text"
       :rules="[val => !!val || 'Address is required']" />
      <q-input v-model="formData.contact_number" mask="(###) ### - ####" label="Contact Number" />
      <q-input v-model="formData.email" mask="S" reverse-fill-mask label="Email" type="email" />
      <q-input ref="inputref" v-model="formData.city" mask="S" reverse-fill-mask label="City" type="char"
       :rules="[val => !!val || 'city is missing']" />
      <q-input ref="inputref" v-model="formData.state" mask="S" reverse-fill-mask label="State" type="char"
       :rules="[val => !!val || 'field is required']" />
      <q-input  ref="inputref" v-model="formData.pin_code" mask="######" label="Pin Code"
       :rules="[val => !!val || 'field is required']" />
      <q-input ref="inputref" v-model="formData.country" mask="N" reverse-fill-mask label="Country" type="char"
       :rules="[val => !!val || 'field is required']" />
      <q-input ref="inputref" v-model="formData.accounting_receipts" mask="SSSS - #### - SS" label="Accounting Receipts" />
      <q-select v-model="formData.status" label="Status" :options="['Published','Draft','Archived']"
       option-label="Standard"
       :rules="[val => !!val || 'field is required']" />
      <q-input v-model="formData.invoices" label="Invoices"/>
      <q-input ref="inputref" v-model="formData.contacts" mask="#" reverse-fill-mask label="Contacts"/>
      <q-input v-model="formData.log_book" label="Log Book"/>
      <q-input v-model="formData.contracts" label="Contracts" />
      <q-input ref="inputref" v-model="formData.gst" mask="## AAAAA####A # A #" label="GST" />
     </div>
  </q-form>
</template>
<script>
export default {
  data () {
    return {
      formData: {}
    }
  },
  methods: {
    async submitData () {
      let validation = await this.$refs.form.validate();
      if (!validation) {
        alert("invalid form");
        return;
      }
      console.log('Emitting Event of submitting form with data')
      alert()
      this.$emit('formSubmit', this.formData)
      console.log('Resetting Form')
      alert();
      this.formData = {};
    },
  },
};
</script>
