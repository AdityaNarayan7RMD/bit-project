<template>
  <div class="q-pa-md">
    <div>
      <h5>Invoices</h5>
    </div>

    <q-table separator="horizontal" :columns="table.columns" :rows="table.rows">
    </q-table>
</div>
</template>

<script>
export default {
  data() {
    return {
      table: {
        rows: [
        ],
        columns: [
          { label: "Id", field: "id" },
          { label: "Account id", field: "id" },
          { label: "Invoice Number", field: "invoice_number" },
          { label: "Invoice Date", field: "invoice_date" },
          { label: "Grand Total", field: "grand_total" },
          { label: "Invoices Status", field: "invoice_status" },
          { label: "User Created", field: "user_created" },
          { label: "Date Created ", field: "date_created" },
          { label: "user Updated", field: "user_updated" },
          { label: "Date Updated", field: "date_updated" },
          { label: "Organisation Id", field: "organisation_id" },
          { label: "invoice_details", field: "invoice_details" },
          { label: "Invoice Settlement", field: "invoice_settlement" },
          { label: "period", field: "period" },
          { label: "Bank Id", field: "bank_id" },
          { label: "Booked By", field: "booked_by" },
          { label: "Oncall Plan", field: "oncall_plan" },
          { label: "vehicle_no", field: "vehicle_no" },
          { label: "Log Type", field: "log_type" },
          { label: "Journey Date", field: "journey_date" },

        ]
      },
    };
  },

  methods: {
    insertData(data) {
      this.table.rows.push(data)
    },
    async fetchData() {
      let response = await this.$api.get("https://gangotri-api.brainysoftwares.com/items/invoices?fields=*.*")
      this.table.rows = response.data.data;
    }


  },
  created() {
    this.fetchData();
  },
}
</script>
