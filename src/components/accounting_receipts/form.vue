<template>
  <q-form ref="form" class="q-pa-md q-ma-md">
    {{ formData }}
    <div class="column">
      <q-select v-model="formData.account_id" label="Account ID" :options="accounts" option-label="account_id"
      option-value="id" map-options emit-value />
    <q-select filled v-model="formData.receipt_date" label="Receipt Date"
      type="date" >
     <template v-slot:append>
        <q-icon name="event" class="cursor-pointer">
          <q-popup-proxy cover transition-show="scale" transition-hide="scale">
            <q-date v-model="date">
              <div class="row items-center justify-end">
                <q-btn v-close-popup label="Close" color="primary" flat />
              </div>
            </q-date>
          </q-popup-proxy>
        </q-icon>
      </template>
    </q-select>
      <q-input v-model="formData.receipt_number" label="Receipt Number" mask="#" reverse-fill-mask
      :rules="[val => !!val || 'field is required']" />
      <q-select v-model="formData.receipt_mode" label="Receipt Mode" :options="['Cheque','Cash','Bank transfer','UPI']"
       option-label="Standard"
       :rules="[val => !!val || 'field is required']"/>
      <q-input v-model="formData.receipt_amount" label="Receipt Amount" mask="#" reverse-fill-mask
      :rules="[val => !!val || 'field is required']" />
      <q-input v-model="formData.transaction_number" label="Transaction Number" mask="#" reverse-fill-mask />
      <q-select v-model="formData.receipt_status" label="Receipt Status" :options="['Received', 'Cleared', 'Declined']"/>
      <q-input v-model="formData.receipt_settlement" label="Receipt Setttlement" />
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
  data () {
    return {
      formData: {},
      accounts:[]
    }
  },
  created (){
    this.fetchAccounts()
  },
  methods: {
    async submitData () {
      let validation = await this.$refs.form.validate();
      if (!validation) {
        alert("invalid form");
        return;
      }
    },

      async fetchAccounts() {
      let response = await this.$api.get('items/accounts')
      this.accounts = response.data.data
    },

  }
}
</script>
