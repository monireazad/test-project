<template>
  <div class="d-flex justify-center">
    <v-simple-table class="info-table grey lighten-5">
      <template v-slot:default>
        <thead class="primary">
          <tr>
            <th class="text-center font-weight-bold headline">User Information</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in Infos" :key="item.name">
            <td>
              <v-icon class="mr-3">{{ item.icon }}</v-icon>
              {{ item.value }}
            </td>
          </tr>
        </tbody>
      </template>
    </v-simple-table>
  </div>
</template>

<script>
export default {
  name: "Table",

  data() {
    return {
      // fields: [
      //   {
      //     name: "fullName",
      //     label: "Full Name",
      //     icon: "mdi-account",
      //     value: "",
      //     col: 6,
      //   },
      //   {
      //     name: "phone",
      //     label: "Phone",
      //     icon: "mdi-phone",
      //     value: "",
      //     col: 6,
      //   },
      //   {
      //     name: "email",
      //     label: "E-mail",
      //     icon: "mdi-at",
      //     value: "",
      //     col: 6,
      //   },
      //   {
      //     name: "address",
      //     label: "Address",
      //     icon: "mdi-map-marker",
      //     value: "",
      //     col: 12,
      //   },
      // ],
    };
  },

  props: ['Infos'] ,
};
</script>

<style>
.info-table {
    width: 30rem;
    box-shadow: 5px 10px 15px #e6e6e6;
}
</style>
