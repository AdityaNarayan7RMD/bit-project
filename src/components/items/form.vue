<template>
  <q-card class="q-pa-md q-ma-md">
    {{ formData }}
    <div class="column">
      <q-input v-model="formData.item_name" label="Item Name" :options="item_name" />
      <q-select clearable v-model="formData.item_type" label="Item Type" :options="['service', 'service with rate']" />
      <q-select clearable v-model="formData.status" label="Status" :options="['public', 'draft', 'archieved']" />

    </div>
    <div class="q-py-md">
      <q-btn color="red" label="submit" @click="submitData"></q-btn>
    </div>
    <div class="q-py-md">
      <q-btn color="red" label="close" to="./"></q-btn>
    </div>
  </q-card>
</template>
<script>
export default {
  data() {
    return {
      formData: {},
    };
  },
  methods: {

    submitData() {
      console.log("Emitting Event of submitting form with data");
      alert();
      this.$emit("formSubmit", this.formData);
      console.log("Resetting Form");
      alert();
      this.formData = {};
    },
  },
};
</script>
