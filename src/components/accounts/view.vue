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
          { label: "Account Name", field: "account_name" },
          { label: "Account Address", field: "account_address" },
          { label: "Contact number", field: "contact_number" },
          { label: "Email", field: "email" },
          { label: "City", field: "city" },
          { label: "State", field: "state" },
          { label: "Country", field: "country" },
          { label: "Pin Code", field: "pin_code" },
          { label: "Accounting receipts", field: "accounting_receipts" },
          { label: "User created", field: "user_created" },
          { label: "User updated", field: "user_updated" }
        ],
      },
    };
  },

  methods: {
    insertData(data) {
      this.table.rows.push(data)
    },
    async fetchData() {
      let response = await this.$api.get("https://gangotri-api.brainysoftwares.com/items/accounts?fields=*.*")
      this.table.rows = response.data.data;
    }


  },
  created() {
    this.fetchData();
  },
}
</script>
