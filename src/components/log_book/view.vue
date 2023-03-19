<template>
  <div class="q-pa-md">
    <div>
      <h5>Lof Book</h5>
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
          { label: "Account Id", field: "account_id" },
          { label: "contact Id", field: "contact_id" },
          { label: "Vehicle Id", field: "vehicle_id" },
          { label: "Driver Id", field: "driver_id" },
          { label: "Contract Id", field: "contract_id" },
          { label: "Log Type", field: "log_type" },
          { label: "Date From", field: "date_from" },
          { label: "Date To", field: "date_to" },
          { label: "Rent", field: "rent" },
          { label: "Intial Reading", field: "initial_reading" },
          { label: "Final Reading", field: "final_reading" },
          { label: "Running Kms", field: "running_kms" },
        ]
      },
    };
  },

  methods: {
    insertData(data) {
      this.table.rows.push(data)
    },
    async fetchData() {
      let response = await this.$api.get("https://gangotri-api.brainysoftwares.com/items/log_book?fields=*.*")
      this.table.rows = response.data.data;
    }


  },
  created() {
    this.fetchData();
  },
}
</script>
