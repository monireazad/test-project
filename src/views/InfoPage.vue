<template>
  <div class="mx-16 my-12">
    <v-row>
      <v-col cols="12">
        <Form @transfer-data="transferData" />
      </v-col>
    </v-row>
    <v-row class="my-10">
      <v-col cols="12">
        <Table v-if="showTable" :infos="fields" />
      </v-col>
    </v-row>
  </div>
</template>

<script>
import Form from "@/components/infoPage/Form.vue";
import Table from "@/components/infoPage/Table.vue";
export default {
  name: "InfoPage",
  components: { Form, Table },

  data: () => ({
    fields: [],
    showTable: false
  }),

  methods: {
    transferData(fields) {
      if (fields) {
        this.showTable = true
        this.fields = fields;
      }
    },
  },
};
</script>
