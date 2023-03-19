<template>
  <div class="q-pa-md">
    <div>
      <h5>Organisation</h5>
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
          { label: "Organisation Name", field: "organsiation_name" },
          { label: "Prefix", field: "prefix" },
          { label: "Description", field: "description" },
          { label: "Address", field: "address" },
          { label: "State", field: "state" },
          { label: "Country", field: "country" },
          { label: "City", field: "city" },
          { label: "Pincode", field: "pincode" },
          { label: "Contact Number", field: "contact_number" },
          { label: "Email", field: "email" },
          { label: "Gst Number", field: "gst_number" },
          { label: "Pan No.", field: "pan_no" },
          { label: "invoices", field: "invoices" },
          { label: "Stated", field: "stated" },
          { label: "User Created", field: "user_created" },
          { label: "Date Created", field: "date_created" },
          { label: "User Updated", field: "user_updated" },
          { label: "Date Updated", field: "date_updated" },
          { label: "Banks", field: "banks" },

        ]
      },
    };
  },

  methods: {
    insertData(data) {
      this.table.rows.push(data)
    },
    async fetchData() {
      let response = await this.$api.get("https://gangotri-api.brainysoftwares.com/items/organisation?fields=*.*")
      this.table.rows = response.data.data;
    }


  },
  created() {
    this.fetchData();
  },
}
</script>
