<template>
  <div class="q-pa-md">
    <div>
      <h5>Accounting Receipts</h5>
    </div>

    <q-table separator="horizontal" :columns="table.columns" :rows="table.rows">
    </q-table>
  </div>
</template>

<script>
export default {
  data () {
    return {
      table: {
        rows: [


        ],
        columns: [
        { label:'Id',field:'id' },
        { label:'Account ID',field:'account_id' },
        { label:'Receipt date', field: 'receipt_date' },
        { label:'Receipt number', field: 'receipt_number'},
        { label:'Receipt mode', field: 'receipt_mode'},
        { label:'Receipt amount', field: 'receipt_amount'},
        { label:'Transaction number', field: 'transaction_number'},
        { label:'User created', field: 'user_created'},
        { label:'User updated', field: 'user_updated'},
        { label:' Receipt status', field: 'receipt_status'},
        { label:'Receipt settlement', field: 'receipt_settlement'},
        { label:'Date created', field: 'date_created'},
        { label:'Date updated', field: 'date_updated'},


      ]
      }
    }
  },

  methods: {
    insertData (data) {
      this.table.rows.push(data)
    },
     async fetchData(){
      let response=await this.$api.get('https://gangotri-api.brainysoftwares.com/items/accounting_receipts?fields=*.*')
      this.table.rows=response.data.data
    }
  },
  created(){
    this.fetchData()
  }
}

</script>

