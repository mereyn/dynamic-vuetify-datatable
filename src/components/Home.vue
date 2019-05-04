<template>
  <v-container>
    <v-layout text-xs-center wrap>
      <v-flex mb-12>
        <h1 class="display-2 font-weight-bold mb-3">Table Edify Component</h1>
        <p class="subheading font-weight-regular">
          Generate Dynamic Vuetify Data Table
          <br>Source Code
          <a href="https://community.vuetifyjs.com" target="_blank">Github</a>
        </p>
      </v-flex>
    </v-layout>
    <table-edify :columns="headers" url="user.json"></table-edify>
  </v-container>
</template>

<script>
import TableEdify from "./TableEdify";

export default {
  data: () => ({
    pagination: {
      sortBy: "name"
    },
    selected: [],
    headers: [
      {
        text: "First Name",
        align: "left",
        dataIndex: "fname"
      },
      {
        text: "Last Name",
        dataIndex: "lname",
        type: "text-input"
      },
      {
        text: "URL",
        dataIndex: "url",
        type: "anchor-link"
      },
      {
        text: "Actions",
        type: "action-buttons",
        actions: [
          {
            text: "Success",
            type: "button"
          }
        ]
      }
    ]
  }),
  components: {
    TableEdify
  }
};
</script>