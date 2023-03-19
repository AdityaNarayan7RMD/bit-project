<template>
  <div class="q-pa-md">
    <div>
      <h5>Driver</h5>
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
          { label: "Driver Name", field: "driver_name" },
          { label: "Address", field: "address" },
          { label: "Contact Number", field: "contact_no" },
          { label: "Status", field: "status" }

        ]
      },
    };
  },

  methods: {
    insertData(data) {
      this.table.rows.push(data)
    },
    async fetchData() {
      let response = await this.$api.get("https://gangotri-api.brainysoftwares.com/items/driver?fields=*.*")
      this.table.rows = response.data.data;
    }


  },
  created() {
    this.fetchData();
  },
}
</script>
