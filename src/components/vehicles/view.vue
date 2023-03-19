<template>
  <div class="q-pa-md">
    <div>
      <h5>Vehicle Type</h5>
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
          { label: "Vehicle No", field: "vehicle_no" },
          { label: "Vehicle Type", field: "vehicle_type" },
          { label: "Status", field: "status" },
          { label: "Sort", field: "sort" },
          { label: "Fuel Avg", field: "fuel_avg" },
          { label: "Log Book", field: "log_book" },
        ]
      },
    };
  },

  methods: {
    insertData(data) {
      this.table.rows.push(data)
    },
    async fetchData() {
      let response = await this.$api.get("https://gangotri-api.brainysoftwares.com/items/vehicles?fields=*.*")
      this.table.rows = response.data.data;
    }


  },
  created() {
    this.fetchData();
  },
}
</script>
