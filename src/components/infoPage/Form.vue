<template>
  <div class="form-container rounded-lg grey lighten-5 mx-md-16">
    <v-row>
      <v-col
        cols="12"
        md="4"
        class="right-side rounded-lg rounded-r-0 d-none d-md-flex"
      ></v-col>

      <v-col cols="12" md="8" class="px-16">
        <h1 class="my-5">Information Form</h1>
        <v-row>
          <v-col
            cols="12"
            :md="item.col"
            v-for="item in fields"
            :key="item.name"
          >
            <v-text-field
              v-if="item.name != 'address'"
              v-model="item.value"
              :label="item.label"
              :prepend-inner-icon="item.icon"
              :rules="item.rule"
              required
              dense
            ></v-text-field>
            <v-textarea
              v-else
              v-model="item.value"
              :label="item.label"
              :prepend-inner-icon="item.icon"
              :rules="item.rule"
              required
              dense
            ></v-textarea>
          </v-col>
        </v-row>
        <div class="d-flex justify-end">
          <v-btn
            class="mb-5 px-10"
            type="submit"
            depressed
            color="primary"
            @click="sendData()"
          >
            Submit
          </v-btn>
        </div>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  name: "Form",
  data: () => ({
    valid: false,
    fields: [
      {
        name: "name",
        label: "Your Name",
        icon: "mdi-account",
        value: "",
        col: 12,
        rule: [(v) => !!v || "Name is required"],
      },
      {
        name: "phone",
        label: "Phone",
        icon: "mdi-phone",
        value: "",
        col: 6,
        rule: [
          (v) => !!v || "Phone is required",
          (v) => (v.length > 10 && v.length <= 11 || "Phone must be 11 digits"),
        ],
      },
      {
        name: "email",
        label: "E-mail",
        icon: "mdi-at",
        value: "",
        col: 6,
        rule: [
          (v) => !!v || "E-mail is required",
          (v) => /.+@.+/.test(v) || "E-mail must be valid",
        ],
      },
      {
        name: "address",
        label: "Address",
        icon: "mdi-map-marker",
        value: "",
        col: 12,
        rule: [(v) => !!v || "Address is required"],
      },
    ],
  }),
  methods: {
    sendData() {
      this.$emit("transfer-data", this.fields);
    },
  },
};
</script>

<style>
.form-container {
  box-shadow: 3px 5px 20px #e7e7e7;
}
.right-side {
  background-image: url(../../assets/backImage.jpg);
  background-size: cover;
  background-position: center;
}
</style>
