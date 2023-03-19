<template>
  <div class="q-pa-md">
    <div>
      <h5>contracts</h5>
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
          { label: "Account id", field: "id" },
          { label: "Name", field: "item_name" },
          { label: "Account", field: "account" },
          { label: "Rent Per Month", field: "rent_per_month" },
          { label: "Vehicle Type", field: "vehicle_type" },
          { label: "fuel", field: "fuel" },
          { label: "Date Created", field: "date_created" },
          { label: "Date Updated", field: "date_updated" },
          { label: "Log Book", field: "log_book" },
          { label: "Is Tax Included", field: "is_tax_included" }
        ]
      },
    };
  },

  methods: {
    insertData(data) {
      this.table.rows.push(data)
    },
    async fetchData() {
      let response = await this.$api.get("https://gangotri-api.brainysoftwares.com/items/contracts?fields=*.*")
      this.table.rows = response.data.data;
    }


  },
  created() {
    this.fetchData();
  },
}
</script>
