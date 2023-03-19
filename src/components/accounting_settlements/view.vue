<template>
  <div class="q-pa-md">
    <div>
      <h5>Accounting Settlements</h5>
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
        { label:'Invoice ID',field:'invoice_id' },
        { label:'Receipt ID', field: 'receipt_id' },
        { label:'Amount', field: 'amount'},
        { label:'Date created', field: 'date_created'},
        { label:'Date updated', field: 'date_updated'},
        { label:'User created', field: 'user_created'},
        { label:'User updated', field: 'user_updated'},


      ]
      }
    }
  },

  methods: {
    insertData (data) {
      this.table.rows.push(data)
    },
     async fetchData(){
      let response=await this.$api.get('https://gangotri-api.brainysoftwares.com/items/accounting_settlements?fields=*.*')
      this.table.rows=response.data.data
    }
  },
  created(){
    this.fetchData()
  }
}

</script>
