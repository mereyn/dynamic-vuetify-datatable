# VueJS Custom Vuetify Data Table

Generate dynamic vuetify data table.

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Compiles and minifies for production

```
npm run build
```

### Run your tests

```
npm test
```

## Vuetify

Vuetify is developed exactly according to Material Design spec. Every component is hand crafted to bring you the best possible UI tools to your next great app. The development doesn't stop at the core components outlined in Google's spec. Through the support of community members and sponsors, additional components will be designed and made available for everyone to enjoy.

## Importing and sample usage of TableEdify component.

```javascript
import TableEdify from "./TableEdify";

export default {
  data: () => ({
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
```

```template
<table-edify :columns="headers"></table-edify>
```

### Result

https://dynamic-vuetify-datatable.firebaseapp.com/

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).
