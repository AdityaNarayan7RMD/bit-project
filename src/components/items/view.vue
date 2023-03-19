<template>
  <div class="q-pa-md">
    <div>
      <h5>Accounts</h5>
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
          { label: "Item Name", field: "item_name" },
          { label: "Item Type", field: "item_type" },
          { label: "Status", field: "status" },
          { label: "User Created", field: "user_created" },
          { label: "Date Updated", field: "date_updated" },
          { label: "User Updated", field: "user_updated" },
          { label: "Date Updated", field: "date_updated" }
        ]
      },
    };
  },

  methods: {
    insertData(data) {
      this.table.rows.push(data)
    },
    async fetchData() {
      let response = await this.$api.get("https://gangotri-api.brainysoftwares.com/items/items?fields=*.*")
      this.table.rows = response.data.data;
    }


  },
  created() {
    this.fetchData();
  },
}
</script>
