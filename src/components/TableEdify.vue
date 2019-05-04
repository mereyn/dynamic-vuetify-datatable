<template>
  <v-data-table
    :headers="headers"
    :items="items"
    :pagination.sync="pagination"
    item-key="name"
    class="elevation-1"
  >
    <template slot="items" slot-scope="props">
      <td v-for="(header, index) in headers" :key="index">
        <span v-if="header.type !== 'undefined' && header.type === 'text-input'">
          <v-text-field v-model="props.item[header.dataIndex]"></v-text-field>
        </span>
        <span v-else-if="header.type !== 'undefined' && header.type === 'anchor-link'">
          <a
            :href="props.item.url"
            class="button js-button"
            role="button"
          >{{ props.item[header.dataIndex] }}</a>
        </span>
        <span v-else-if="header.type !== 'undefined' && header.type === 'action-buttons'">
          <span v-for="(action, index) in header.actions" :key="index">
            <span v-if="action.type !== 'undefined' && action.type === 'button'">
              <v-btn :color="action.color || 'success'">{{ action.text }}</v-btn>
            </span>
          </span>
        </span>
        <span v-else>{{ props.item[header.dataIndex] }}</span>
      </td>
    </template>
  </v-data-table>
</template>

<script>
import axios from "axios";

export default {
  data: () => ({
    pagination: {
      sortBy: "name"
    },
    selected: [],
    items: []
  }),
  props: {
    columns: {
      type: Array,
      default: () => []
    },
    url: {
      type: String,
      default: null
    }
  },
  methods: {
    toggleAll() {
      if (this.selected.length) this.selected = [];
      else this.selected = this.desserts.slice();
    },
    changeSort(column) {
      if (this.pagination.sortBy === column) {
        this.pagination.descending = !this.pagination.descending;
      } else {
        this.pagination.sortBy = column;
        this.pagination.descending = false;
      }
    }
  },
  computed: {
    headers() {
      if (this.columns.length > 0) {
        return this.columns;
      } else {
        return [];
      }
    }
  },
  mounted() {
    // Load data
    axios
      .get(this.url)
      .then(res => {
        return (this.items = res.data);
      })
      .catch(error => console.log(error));
  }
};
</script>